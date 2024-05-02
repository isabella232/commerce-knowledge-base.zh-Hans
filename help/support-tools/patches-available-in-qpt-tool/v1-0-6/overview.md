---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.6`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.6。
exl-id: 38e9454b-e278-4b14-a861-2af0623db92e
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.6概述

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.6。

QPT v1.0.6包含以下修补程序：

1. **MDVA-28202**：修复了在使用MSI时分层导航无法正确过滤可配置产品的问题。
1. **MDVA-28300**：修复了GQL请求未反映目录价格规则中的价格更改的问题。
1. **MDVA-28993**：实施 *最小值应匹配* 功能和部分搜索 [!DNL Elasticsearch] 引擎。 解决了搜索查询中连字符的问题。
1. **MDVA-29446**：修复了结账期间不适用的配送方式价格显示为零的问题。
1. **MDVA-29787**：修复了以下情况下，相关产品的目标规则无法正常运行的问题： *是其中之一* 条件用于定义要显示的产品。
1. **MDVA-30102**：修复了以下问题： [!DNL Redis] 由于布局缓存没有TTL，因此缓存会快速增大。
1. **MDVA-30357**：修复了在通过cron生成Sitemap时创建错误图像URL的问题。
1. **MDVA-30565**：修复了以下问题： *没有cartid = 0的此类实体* 如果启用了永久购物车，则在storefront结帐时为访客客户显示错误。
1. **MDVA-30599**：修复了使用API创建的访客报价错误地标记为已登录客户的报价的问题。
1. **MDVA-30977**：修复了重新索引后类别中随机缺少产品的问题。
1. **MDVA-31006**：修复了使用下达订单后出现重复订单的问题 [!DNL Paypal Express] 付款。

使用左侧的菜单导航到特定的修补程序页面。
