---
title: 如何请求云基础架构扩展中的临时Adobe Commerce
description: 如果贵组织正在计划一个在线活动，而您预期该活动将出现高流量，或者您突然发现您的网站正在进行高流量活动，则可以提交[支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以请求为云基础架构商店上的Adobe Commerce临时添加云容量。
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# 如何请求云基础架构扩展中的临时Adobe Commerce

如果贵组织正在计划一个您预计会有高流量的在线活动，或者您突然发现您的网站正在进行高流量活动，则可以提交一个 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 为云基础架构存储上的Adobe Commerce请求临时性额外云容量。

>[!NOTE]
>
>非紧急升级请求需要48小时通知。 升级促销活动不被视为紧急情况，除非站点完全无法正常工作或接收的流量比预期高得多，并且性能严重降低。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，全部 [支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 如何识别高流量事件

在New Relic警报中，您可以使用基线警报条件来定义根据数据行为调整的阈值。

基线警报可用于创建满足以下条件的警报条件：

* 仅在数据行为异常时通知您。
* 动态调整以适应不断变化的数据和趋势，包括每日或每周趋势。

此外，当您还没有已知行为时，基线警报可很好地用于新应用程序。

请按照此链接了解有关New Relic的更多信息 [应用智能的异常检测](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/).

如果您收到建议高流量事件的警报通知，您可能需要考虑 [提交支持票证](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) 请求增加容量 请按照以下步骤操作。

## 如何监控站点的性能

Adobe为Adobe Commerce on cloud infrastructure提供一套New Relic警报策略专业规划架构和Adobe Commerce on cloud infrastructure入门规划架构生产环境可跟踪以下关键性能指标：

* [Apdex得分](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* 错误率
* 磁盘空间（仅适用于Pro体系结构生产环境）

根据行业最佳实践，这些策略可设置影响性能的警告和严重情况的阈值。 当站点遇到触发警报阈值的基础架构或应用程序问题时，New Relic会发送警报通知，以便您能够主动解决该问题。 要使用这些策略，必须配置通知通道以接收警报消息。

按照此链接了解如何 [配置基于性能的警报](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts).

## 请求临时扩展的步骤

请按照以下步骤提交 [支持服务单](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) 要请求临时额外云容量，请执行以下操作：

提交 [Adobe Commerce支持中心的支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，输入以下信息后：

>[!NOTE]
>
>此 *假期激增请求* 只有在10月到12月之间才能做出选择。

1. 请选择您要为其寻求支持的Adobe Commerce产品。
1. 填写前四个（产品、组织、实施类型、主题）字段。
1. 选择 *Adobe Commerce云基础架构* 在 **联系原因** 下拉菜单。
1. 选择 *假期激增容量请求* 在 **Adobe Commerce基础架构联系原因** 下拉选项。 单击 **确定** ，请求提前四十八个工作小时发出临时额外云容量请求通知。
1. 为必填字段选择日期 **调整开始日期的大小** 和 **调整结束日期大小**. 首选的 **调整开始时间大小** 也是必填字段。
1. 填写下面的四个字段。
1. 在 **描述** 字段，如果您有关于大小的其他信息，请在此处提供。 如果不要求特定的更大容量，我们将为您提供下一个更大的环境容量。 紧急事件请求将默认使用当前大小的下一个较大大小。 如果您需要额外的容量，请在 **描述** 字段。 增加的容量将从您签订的“喘振天数”或vCPU天数中扣除。 通常的容量增加时段为5天，但如果您需要更多或更少的天数，请在 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

>[!NOTE]
>
>一旦安排了扩展，自动化系统将调整云实例的大小。 过程完成后，您将不会收到任何票证通知。 您可以使用针对Adobe Commerce的观察结果工具查看您的AWS或Azure实例类型，以 [验证更改](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md).

## 查看您的升级历史记录

您可以查看请求调整大小的历史记录，方法是向 **CSM（客户成功经理）**.
以下信息适用于每个调整大小请求：

* **调整开始日期的大小**：升级请求的日期。
* **调整结束日期大小**：将集群返回到先前大小的日期。
* **vCPU大小**：集群在升级后的大小。
* **使用天数**：群集保持放大状态的天数。
* **周期vCPU**：根据使用的天数更改vCPU大小。 （例如，vCPU大小192 x 25天等于4,800）。


## 相关阅读

* 有关如何衡量和改进站点性能的见解、方法和示例，请参阅我们的支持知识库中的以下深入文章：
   * [云中Adobe Commerce的CPU分配计算](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [检查云上的Adobe Commerce是否需要针对主机实例进行大小调整](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [检查云中Adobe Commerce的主机的CPU配置](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* 有关如何识别中断的信息，请参阅 [识别并测量Adobe Commerce on cloud的中断](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html) 在我们的支持知识库中。
* 有关提高站点性能以避免利用容量增加的需求的信息，请参阅我们的开发人员文档中的以下文章：
   * [图像大小](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [全页缓存](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
