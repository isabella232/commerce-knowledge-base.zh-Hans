---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.13`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.13。
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.13概述

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.13。

QPT v1.0.13包含以下修补程序：

1. **MCP-87**：改进了大型用户档案的类别产品和库存索引器的索引时间。
1. **MDVA-13203**：修复了 *完整性约束违规search_tmp_表* 完全重新索引后出现错误。
1. **MDVA-19391**：修复了以下问题： `analytics_collect_data` 由于 `catalog_category_entity_text` 表格。
1. **MDVA-20376**：修复了的问题 *没有具有customerId = 1的此类实体* 中的错误 `exception.log` ，适用于下单后登录的客户。
1. **MDVA-22150**：修复了以下问题：如果在Admin中禁用了可配置产品，那么在购物车中安装了可配置产品并应用了优惠券的客户将无法登录。
1. **MDVA-23426**：修复了Adobe Commerce发送的通知电子邮件包含空白正文并将内容添加为附件的问题。
1. **MDVA-23764**：修复中的错误 `JsFooterPlugin.php` 这会影响动态块的显示。
1. **MDVA-30858**：修复了的问题 [!DNL PayPal] 结算报告不可用于 **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]** 按预期结算。
1. **MDVA-32545**：修复了在从管理员创建订单时未自动发送发票的问题。
1. **MDVA-32714**：修复了客户组价格在GraphQL产品查询中不起作用的问题。
1. **MDVA-33106**：修复了在cron之后擦除重新计划的产品更改的问题 `run` 命令被执行。

使用左侧的菜单导航到特定的修补程序页面。
