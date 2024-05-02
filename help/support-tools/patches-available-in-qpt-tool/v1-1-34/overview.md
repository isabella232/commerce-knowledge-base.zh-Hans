---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.34`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.34。
feature: Tools and External Services
role: Admin
exl-id: 79998832-26cb-4c11-a505-08c3382f86d4
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 概述： [!DNL Quality Patches Tool] (QPT) v1.1.34

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.34。

QPT v1.1.34包含以下修补程序：

1. **ACSD-52277**：修复了在管理员中创建新订单时，选择商店视图后管理员用户未正确重定向的问题。
1. **ACSD-50813**：修复了以下问题：管理员无法在SKU中添加包含斜杠的捆绑产品 [!UICONTROL Add Products by SKU] 管理订单的功能。
1. **ACSD-51630**：修复了大量系统消息会减慢管理员页面下载速度的问题。
1. **ACSD-51853**：修复了在使用时未应用复制的文本样式的问题 [!DNL Page Builder].
1. **ACSD-52160**：修复了基于规则条件未正确评估购物车价格规则的产品验证结果的问题 *如果在购物车中找到/未找到项目，并且满足以下所有条件： All/Any of these conditions true*.
1. **ACSD-51636**：修复了以下问题：管理员无法从客户帐户部分添加新用户，尽管他们拥有所有必要的角色和权限。
1. **ACSD-51739**：修复了在运行请求时 `structure_id` 在中请求 `CompanyTeam` GraphQL请求。
1. **ACSD-51857**：修复了性能缓慢的问题 `aggregate_sales_report_bestsellers_data` cron报告影响大 `sales_order` 和 `sales_order_item` 数据库表。
1. **ACSD-48448**：修复了在取消订单期间发生争用条件问题，导致在 *inventory_reservation* 表格。
1. **ACSD-52689**：修复了图像无法上传到的问题 [!DNL Amazon S3] 使用REST API进行存储。

使用左侧的菜单导航到特定的修补程序页面。
