---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.42`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.42。
feature: Tools and External Services
role: Admin, Developer
exl-id: 49f7ebd6-7a5f-49da-8fac-c3c2b73b52c1
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 概述： [!DNL Quality Patches Tool] (QPT) v1.1.42

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.42。

QPT v1.1.42包含以下修补程序：

1. **ACSD-53658**：修复了以下问题： *[!UICONTROL Recently Viewed]* 产品数据未在商店视图中正确更新。
1. **ACSD-54626**：修复了无法创建新采购订单规则的问题(`createPurchaseOrderApprovalRule`) `NUMBER_OF_SKUS` 属性访问GraphQL。
1. **ACSD-53845**：修复了以下情况下的MySQL连接超时问题： `consumer max_messages` = 0。
1. **ACSD-54890**：修复了以下问题： `aggregate_sales_report_bestsellers_data` 导致MySQL错误的原因为 `/tmp` 磁盘空间不足。
1. **ACSD-55112**：修复了 *[!UICONTROL Submit review]* 多次单击按钮，不需要 [!DNL Google reCAPTCHA v3] 验证。
1. **ACSD-54264**：修复了错误消息的问题 *无法更新请求的属性。 行ID：store_id* 当客户尝试使用另一商店视图中的可转让报价结帐时显示。
1. **ACSD-54418**：修复了将固定数量的折扣错误地应用于动态定价捆绑包的每个子产品的问题。
1. **ACSD-55238**：修复了保存空的产品元描述时的问题。
1. **ACSD-54966**：修复了在上一个订单失败时，无法重用每个客户限量使用的优惠券代码的问题。
1. **ACSD-54060**：修复了受限制的管理员无法保存产品（如果它是分配给其他范围的另一个产品的子产品）的问题。
1. **ACSD-48910**：修复了以下问题：在订单开具发票和发运后，分配给多个来源的捆绑产品出现缺货情况，即使该产品的数量不为零。
1. **ACSD-55381**：修复了查询时的内部服务器错误 `configurable_product_option_uid` 和 `configurable_product_option_value_uid` 来自B2B的字段 *[!UICONTROL Requisition list]* 通过GraphQL。
1. **ACSD-55628**：修复了在公司注册表中上传文件的操作，以及替换店面中客户属性的文件的操作。

使用左侧的菜单导航到特定的修补程序页面。
