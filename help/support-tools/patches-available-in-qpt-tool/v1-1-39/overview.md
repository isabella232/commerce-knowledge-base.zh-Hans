---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.39`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.39。
feature: Tools and External Services
role: Admin, Developer
exl-id: 48563701-0fa0-4c88-943e-78b421b806b5
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# 概述： [!DNL Quality Patches Tool] (QPT) v1.1.39

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.39。

QPT v1.1.39包含以下修补程序：

1. **ACSD-53704**：修复了在奖励点过期后错误计算奖励点余额历史记录的问题。
1. **ACSD-53583**：改进的部分重新索引性能 *类别产品* 和 *产品类别* 索引器。
1. **ACSD-54026**：修复了的错误消息 `updateCompanyRole` 非授权用户的GraphQL请求。
1. **ACSD-54106**：修复了按名称对土耳其语重音字符进行类别产品排序不正确的问题。
1. **ACSD-52219**：修复了在书签视图之间频繁切换时，管理员网格保存的过滤器无法按预期工作的问题。
1. **ACSD-54342**：修复了错误的错误消息 *数据结构错误：值混合* 导入没有有效数据的CSV文件时。
1. **ACSD-54660**：添加了新输入属性 *sort* 在GraphQL中排序客户订单的依据 `sort_field` 和 `sort_direction`.
1. **ACSD-54776**：修复了取消选中的问题 *[!UICONTROL Use Default Value]* 对于第二个网站、商店和商店视图，和非默认产品字段值不会保存。
1. **ACSD-53998**：修复了 **[!UICONTROL Dynamic Block]** 基于 **[!UICONTROL Customer Segment]** 从客户帐户注销后无法正常工作。
1. **ACSD-53204**：修复 *无法保存产品。* 并发请求使用向产品库添加图像时出错 `rest/V1/products/<sku>/media` 端点。
1. **ACSD-47657**：为AWS凭据添加了缓存机制。 凭据提供程序现在使用Magento缓存来缓存从AWS检索到的凭据以进行EC2配置。

使用左侧的菜单导航到特定的修补程序页面。
