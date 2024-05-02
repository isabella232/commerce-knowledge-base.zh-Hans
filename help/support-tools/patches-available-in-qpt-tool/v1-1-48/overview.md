---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.48呎'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.48。
feature: Tools and External Services
role: Admin, Developer
exl-id: 6170c616-312c-4de3-98dc-e2c27c376608
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 概述： [!DNL Quality Patches Tool] (QPT) v1.1.48

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.48。

QPT v1.1.48包含以下修补程序：

1. **ACSD-55566**：修复了 *[!UICONTROL mergeCart mutation]* 失败并显示 *内部服务器错误* 在合并源购物车和目标购物车时具有相同的捆绑项目的GraphQL响应中。
1. **ACSD-56546**：修复了可配置和捆绑产品显示为 *[!UICONTROL Out of Stock]* 在店面时 *[!UICONTROL Display Out of Stock Product]* 配置已禁用。
1. **ACSD-56635**：修复了在使用导入功能时，导入的客户使用相同的电子邮件地址复制的问题 [!UICONTROL Account Sharing] 设置为 *[!UICONTROL Global]*.
1. **ACSD-56741**：修复了错误消息 *正在尝试访问类型为null的值上的数组偏移* 显示于 `setup:upgrade` 当数据库包含与索引机制无关的自定义MySQL触发器并且 [!DNL MView].
1. **ACSD-57315**：修复了在中创建新交易的问题 [!DNL PayPal Payflow Pro] 每次 **[!UICONTROL Fetch]** 在的“查看交易”屏幕上单击了按钮 [!UICONTROL Admin].
1. **ACSD-57337**：修复了具有特定网站访问限制的管理员用户能够在中查看所有网站公司的问题。 *[!UICONTROL Companies]* 网格。
1. **ACSD-57394**：修复了GraphQL中按多个排序字段对产品排序不正确的问题。
1. **ACSD-57565**：修复了 *[!UICONTROL Order]* 在更新时间段之前，仪表板显示不正确的订单信息。 现在，仪表板在首次加载时显示正确的订单统计信息。
1. **ACSD-57854**：修复了产品GraphQL请求在类别聚合中返回禁用类别的问题。
1. **ACSD-58008**：修复了在未指定结束日期的情况下，更新计划更新会删除暂存项目的先前版本的问题。

使用左侧的菜单导航到特定的修补程序页面。

