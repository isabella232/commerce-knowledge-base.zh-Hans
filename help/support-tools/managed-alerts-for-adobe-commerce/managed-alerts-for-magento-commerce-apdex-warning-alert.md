---
title: 'Adobe Commerce托管警报：Apdex警告警报'
description: 本文提供了在New Relic中收到Adobe Commerce的Apdex警告警报时的故障排除步骤。 Apdex得分衡量用户对Web应用程序和服务的响应时间的满意度。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。
exl-id: 6e3f28ae-734b-468f-b6a5-c4f2edb1cb4b
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 3493214b468ac93dc938690495ea0a6bcf645a29
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Adobe Commerce的受管警报：Apdex警告警报

本文提供了在New Relic中收到Adobe Commerce的Apdex警告警报时的故障排除步骤。 Apdex得分衡量用户对Web应用程序和服务的响应时间的满意度。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。

![apdex警告警报](assets/apdex-warning-magento-managed.png){width="500"}

## 受影响的产品和版本

* Adobe Commerce on cloud infrastructure Pro计划架构
* 云基础架构上的Adobe Commerce入门计划架构

## 问题

如果您已注册，将在New Relic中收到托管警报 [Adobe Commerce的受管警报](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md) 以及一个或多个警报阈值已超出。 这些警报由Adobe开发，旨在通过支持和工程部门的分析为商家提供一套标准。

<u> **去吧！** </u>

* 中止任何计划的部署，直到清除此警报。
* 如果您的网站处于或完全无响应，请立即将网站置于维护模式。 有关步骤，请参阅  [安装指南>启用或禁用维护模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) 在我们的开发人员文档中。 确保将您的IP添加到免除IP地址列表，以确保您仍然能够访问站点进行故障排除。 有关步骤，请参阅 [维护免除IP地址列表](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt) 在我们的开发人员文档中。

<u>**不要！**</u>

* 启动其他营销活动，这可能会给您的网站带来其他页面查看次数。
* 运行索引器或其他cron，这可能会在CPU或磁盘上造成额外压力。
* 执行任何主要管理任务(即Commerce管理、数据导入/导出)。
* 清除缓存。

## 解决方案

按照以下步骤确定原因并排除故障。

1. 要确定问题的根源，请使用 [New Relic APM的“交易”页](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) 要识别具有性能问题的事务处理，请执行以下操作：
   * 按升序Apdex分数对事务排序。 [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) 指用户对Web应用程序和服务的响应时间的满意度。 A [Apdex得分低](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md) 可以指示瓶颈（响应时间较长的事务处理）。 通常是数据库、 Redis或PHP。 有关步骤，请参阅New Relic [查看对Apdex满意度最高的交易记录](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * 按最高吞吐量、最慢的平均响应时间、最耗时的阈值和其他阈值对事务进行排序。 有关步骤，请参阅New Relic [查找特定的性能问题](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. 使用 [New Relic APM的基础架构页面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) 确定资源密集型流程。 有关步骤，请参阅New Relic [“基础结构监视主机”页>“进程”选项卡](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. 如果Redis或MySQL等服务是内存消耗的最大来源，请尝试以下操作：
   * 检查您是否使用最新版本。 较新版本有时可以修复内存泄漏。 如果您不是最新版本，请考虑升级。 有关步骤，请参阅 [适用于Adobe Commerce的Cloud >服务>更改服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) 在我们的开发人员文档中。
1. 如果问题不是由服务版本引起的：
   * 检查其他MySQL问题，如长时间运行的查询、未定义主键以及重复的索引。 有关步骤，请参阅 [Adobe Commerce中有关云基础架构的最常见数据库问题](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) 在我们的支持知识库中。
   * 检查其他PHP问题。 通过运行复查正在运行的进程 `ps aufx` 在CLI/终端中。 在终端输出中，您将看到当前正在执行的cron作业和进程。 检查进程执行时间的输出。 如果存在执行时间较长的cron，则该cron可能会挂起。 有关疑难解答步骤，请参阅 [性能缓慢、运行速度缓慢且运行时间较长](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md) 和 [Cron作业停留在“正在运行”状态](/help/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.md) 在我们的支持知识库中。
1. 确定问题的潜在源后，可通过SSH连接到环境以进一步调查。 有关步骤，请参阅 [Cloud for Adobe Commerce >技术和要求> SSH进入您的环境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh) 在我们的开发人员文档中。
1. 如果您仍在努力确定源，请查看最新趋势，以确定最近的代码部署或配置更改（例如，新客户组和目录的大幅更改）中存在的问题。 建议您查看过去七天的活动，以了解代码部署或更改中的任何关联。
1. 如果您在合理的时间内找不到解决方案，请请求升级站点，或者将站点置于维护模式（如果尚未这么做）。 有关步骤，请参阅 [如何请求调整临时大小](/help/how-to/general/how-to-request-temporary-magento-upsize.md) 在我们的支持知识库中，以及 [安装指南>启用或禁用维护模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten) 在我们的开发人员文档中。
1. 如果 [放大](/help/how-to/general/how-to-request-temporary-magento-upsize.md) 将站点恢复为正常运营，考虑请求永久扩展(联系您的Adobe客户团队)，或通过运行负载测试和优化查询来尝试在专用暂存中重现问题，或尝试运行降低服务压力的代码。 请参阅 [Cloud for Adobe Commerce >测试部署>负载和压力测试](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest) 在我们的开发人员文档中。
