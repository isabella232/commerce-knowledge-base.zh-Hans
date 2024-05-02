---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.31`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.31。
exl-id: 0d93619e-0ae6-4dba-9b76-8aeb026c456d
feature: Tools and External Services
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 概述： [!DNL Quality Patches Tool] (QPT) v1.1.31

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.31。

QPT v1.1.31包含以下修补程序：

1. **ACSD-50817**：优化cron作业 `sales_clean_quotes` 通过将复合索引添加到来加快运行速度 `store_id` 和 `updated_at` 引号表中的列。
1. **ACSD-50345**：修复了以下问题： [!DNL Google reCAPTCHA v2] 提交失败的付款后不会重新加载， [!DNL Google reCAPTCHA v3 Invisible] 无法正常结帐，且无法下订单；以及 [!UICONTROL PlaceOrder] 事件未触发。
1. **ACSD-49392**：修复了在对捆绑产品进行部分退款后，订单状态更改为已关闭的问题。
1. **ACSD-51036**：修复了在并发REST API调用期间出现的争用情况导致在中覆盖配送状态信息的问题 [!UICONTROL Items Ordered] 表格。
1. **ACSD-50858**：修复了在卡付款失败后优惠券被错误地标记为使用的问题。

使用左侧的菜单导航到特定的修补程序页面。
