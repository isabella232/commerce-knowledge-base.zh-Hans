---
title: Adobe Commerce部署疑难解答程序
description: 使用Deployment Troubleshooter工具可解决Adobe Commerce上的停滞部署和失败部署。 单击每个问题以显示故障诊断程序每个步骤的答案。
exl-id: 5141e079-be61-44c2-8bff-c4b13cb7e07c
feature: Build, Deploy, Support
role: Developer
source-git-commit: 6177863da268f43cc30119cef6f718a04c46b3e6
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# Adobe Commerce部署疑难解答程序

使用Deployment Troubleshooter工具可解决Adobe Commerce上的停滞部署和失败部署。 单击每个问题以显示故障诊断程序每个步骤的答案。

## 步骤1 — 验证服务是否正在运行 {#step-1}

+++**云基础架构上的Adobe Commerce是否已启动？**

停滞的部署 — Adobe Commerce云基础架构服务是否已启动？ Check [Adobe Commerce Cloud](https://status.adobe.com/products/3350/).

a.是 — 转到 [步骤2](#step-2).\
b.否 — 维护或全球中断。 检查预计持续时间和更新。

+++

## 步骤2 — 检查其他环境中的部署 {#step-2}

+++**其他环境中的部署是否阻止了现有环境中的部署？**

要获取正在进行的活动的列表，请使用magento-cloud CLI运行以下命令（如果您仅添加到一个云项目）：

```bash
magento-cloud --state=in_progress
```

要获取正在进行的活动列表，请使用magento-cloud CLI运行以下命令（如果已添加到多个项目）：

```bash
magento-cloud -p <project-id or project-url> --state=in_progress
```

要查找有关现有部署活动的信息(请参阅 [检查部署日志，如果Cloud UI出现“日志截断”错误](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error.html)
详细信息)您可以运行此命令以获取该活动的运行日志：

```bash
magento-cloud activity:log <activity-id> [OPTIONAL: <-p project-id or project-url>]
```

a.是 — 对现有环境中阻止部署的其他环境进行故障排除。 继续到 [步骤3](#step-3).

b.否 — 对当前环境进行故障排除。 继续到 [步骤3](#step-3).

+++


## 步骤3 — 验证所有节点上的SSH {#step-3}

+++**是否对所有节点成功执行SSH？**

a.是 — 转到 [步骤4](#step-4).\
b.否 —  [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 步骤4 — 验证所有服务是否正在运行 {#step-4}

+++**所有服务都在运行吗？**

a.是 — 转到 [步骤5](#step-5).\
b.否 —  [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 步骤5 — 验证Bitbucket是否正在运行 {#step-5}

+++**使用Bitbucket？**

a.是 — 检查 [status.bitbucket.com](https://bitbucket.status.atlassian.com/).\
b. NO — 检查 [生成和部署日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html). 继续到 [步骤6](#step-6).

+++

## 步骤6 — 检查错误代码 {#step-6}

+++**是否报告了错误代码？**

a.是 — 转到 [步骤7](#step-7).\
b.否 — 继续访问 [步骤8](#step-8).

+++

## 步骤7 - 403禁止出现错误 {#step-7}

+++**403禁止访问？**

a.是 — 转到 [步骤16](#step-16).
b.否 — 继续访问 [步骤9](#step-9).

+++

## 步骤8 — 验证cron作业是否正在运行 {#step-8}

+++**cron作业当前是否正在运行？** 在分支上通过ssh登录并运行 `ps aufxx |grep cron`.

a.是 — 通过ssh在受影响的分支（例如，主分支）上登录。 杀掉并解锁cron作业。 这将终止cron作业并重置状态。 运行 `php vendor/bin/ece-tools cron:kill` 然后 `php vendor/bin/ece-tools cron:unlock`. 如果您正在将一个环境合并到另一个环境，请检查这两个环境是否正在运行cron。\
b.否 — 继续访问 [步骤17](#step-17).

+++

## 步骤9 — 应用程序可部署到远程群集错误 {#step-9}

+++**无法将应用程序上载到远程群集错误？**

a.是 — 转到 [步骤10](#step-10).\
b.否 — 继续访问 [步骤11](#step-11).

+++

## 步骤10 — 检查足够的存储 {#step-10}

+++**可用存储，还好吗？**

a.是 — 继续 [步骤11](#step-11).\
b.否 — 复查 [管理磁盘空间](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html).

+++

## 步骤11 — 验证磁盘空间 {#step-11}

+++**_无法写入文件警告&#x200B;_？**

答：是的，请 [增加.magento.app.yaml中的磁盘值](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space) 并重新部署。 如果这行不通， [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b.否 — 继续 [步骤12](#step-12).

+++

## 步骤12 — 环境重新部署失败错误 {#step-12}

+++**环境重新部署失败错误？**

a.是 — 继续 [步骤13](#step-13).\
b.否 — 继续 [步骤8](#step-8).

+++

## 步骤13 — 检查Elasticsearch升级是否失败 {#step-13}

+++**要升级或部署的Elasticsearch？**

a.是 — Elasticsearch升级步骤失败。 请参阅 [Elasticsearch软件兼容性](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html). 如果Elasticsearch升级仍然无法正常工作， [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket). **注意**：在云基础架构上的Adobe Commerce上，请注意，如果没有48个工作小时的通知，服务升级就无法推送到生产环境。 这是必需的，因为我们需要确保有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。 所以在更改需要投入生产前48小时， [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 详细描述所需的服务升级，并说明希望升级过程开始的时间。\
b.否 — 继续访问 [步骤14](#step-14).

+++

## 步骤14 — 检查空间限制 {#step-14}

+++**文件系统是否用完inode或空间？**

a.是 — 请参阅 [管理磁盘空间](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#application-disk-space).\
b.否 — 继续访问 [步骤15](#step-15).

+++

## 步骤15 -Elasticsearch版本错误 {#step-15}

+++**有关Elasticseach版本的错误？**

a.是 — 转到 [步骤16](#step-16).\
b.否 — 继续访问 [步骤21](#step-21).

+++

## 步骤16 — 验证编辑器配置 {#step-16}

+++**编辑器配置是否正确？**

a.是 — 转到 [步骤10](#step-10).\
b.否 — 复查 [“编辑器疑难解答”网页](https://getcomposer.org/doc/articles/troubleshooting.md).

+++

## 步骤17 — 检查长时间运行的进程 {#step-17}

+++**长时间运行的进程？**

a. YES — 确定长时间运行的进程，然后终止进程：
1. 在终端中运行以下命令： `ps aufx`.
1. 找到长时间运行的进程的PID。
1. 终止进程，使用 `kill -9 <PID>`.

监控部署以便再次发生。

b.否 — 继续访问 [步骤18](#step-18).

+++

## 步骤18 — 检查开机自检挂钩故障 {#step-18}

+++**挂机后失败/挂起？**

a.是 — 数据库： [可用磁盘空间](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html#allocate-disk-space)、损坏、表不完整/损坏。\
b.否 — 继续访问 [步骤19](#step-19).

+++

## 步骤19 — 检查第三方扩展是否阻止部署 {#step-19}

+++**是否使用第三方扩展？**

a.是 — 尝试 [禁用第三方扩展](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html) 和运行部署（以查看它们是否是问题的原因），尤其是当任何错误中都存在扩展名称时。\
b.否 — 继续访问 [步骤20](#step-20).

+++

## 步骤20 — 检查慢查询 {#step-20}

+++**长时间运行查询？**

[检查慢查询日志和MySQL显示进程列表](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md).

a.是 — 终止任何长时间运行的查询。 审核 [MySQL终止语法。](https://dev.mysql.com/doc/refman/8.0/en/kill.html)\
b.否 —  [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 步骤21 — 降级Elasticsearch版本 {#step-21}

+++**正在降级Elasticsearch版本？**

a.是 — 无法通过配置完成。 [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b.否 —  [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[返回步骤1](#step-1)
