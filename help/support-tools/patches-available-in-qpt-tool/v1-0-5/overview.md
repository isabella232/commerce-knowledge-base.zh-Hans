---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.5`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.5。
exl-id: 439358e8-d6bc-4d35-aee1-f4fc33ae267c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.5概述

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.5。

QPT v1.0.5包含以下修补程序：

1. **MDVA-28191**：修复了在通过管理员创建订单期间无法加载支付方法的问题。
1. **MDVA-28409**：修复了 `sales_clean_quotes` cron作业失败于 *内存不足* 当数据库中的过期引号数量很大时出错。
1. **MDVA-28661**：修复了在更改公司管理员后，“公司用户”公司帐户部分中引发错误的问题。
1. **MDVA-28763**：修复了使用REST API多次更新产品信息后产品图像复制的问题。
1. **MDVA-29042**：修复了目录权限更改为的问题。 *允许* 将新产品添加到共享目录后自动更新。
1. **MDVA-29959**：修复了受限管理员用户使用的问题 *公司* 不允许使用权限删除公司帐户。
1. **MDVA-30107**：修复了当存储视图使用不同的基本URL时，存储切换器无法按预期工作的问题。
1. **MDVA-30265**：修复了在创建发票后装运跟踪链接停止工作的问题。
1. **MDVA-30284**：修复了目录搜索索引器由于以下原因而失败的问题 *[!DNL Elasticsearch]错误：已超过索引中字段总数的限制。*
1. **MDVA-30428**：修复了将产品分配给自定义库存源时，客户无法将产品添加到愿望清单的问题。
1. **MDVA-30593**：修复了未清理根据报价生命周期设置过期的报价的问题。

使用左侧的菜单导航到特定的修补程序页面。
