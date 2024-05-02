---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.8`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.8。
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.8概述

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.8。

QPT v1.0.8包含以下修补程序：

1. **MDVA-28357**：将标准分析器替换为带有关键字的SKU字段自定义分析器 [!DNL ElasticSearch] 索引，使通配符搜索查询可与包含连字符(“ — ”)的SKU配合使用。
1. **MDVA-29954**：修复了 *新建公司注册请求* 和 *您已被链接到某个公司* 电子邮件是从错误的地址发送的。
1. **MDVA-30112**：修复了订单数超过 *簇大小* 值，Adobe Commerce会考虑以下订单 *待处理* 状态为不一致。
1. **MDVA-30963**：修复了产品筛选结果设置为仅包含为指定的值的问题 *所有商店视图* 在管理员中定义范围，包括在商店视图级别覆盖值的产品。
1. **MDVA-31150**：修复了GETInvoice Rest API调用未返回商店信用卡和礼品卡余额的问题，当时，发票通过Rest API调用过帐，并且订单由商店信用卡和礼品卡帐户支付了一部分。
1. **MDVA-31242**：修复了在中显示错误货币符号的问题 [!UICONTROL Credit Memo] 网格。
1. **MDVA-31295**：修复了完成部分订购并征税项目后未计算奖励点数的问题。

使用左侧的菜单导航到特定的修补程序页面。
