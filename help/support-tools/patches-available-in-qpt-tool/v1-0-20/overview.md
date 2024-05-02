---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.20`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.20。
exl-id: 13ed85f9-4ecb-467f-9ed0-ceec4ac200db
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.20概述

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.20。

QPT v1.0.20包含以下修补程序：

1. **MC-41359**：修复了SameSite Cookie参数设置不正确的问题。
1. **MDVA-11189**：修复了在导入CSV文件更新产品库存后，来自的行 `cataloginventory_stock` 表格将被删除。
1. **MDVA-15546**：修复了创建订单后 *列entity_id where子句不明确* 错误显示在异常日志中。
1. **MDVA-19640**：修复了以下问题： [!DNL Advanced Reporting] 未显示任何数据。
1. **MDVA-21095**：修复了查询时出现的问题 `INSERT INTO search_tmp` 批量属性值更新后不会结束。
1. **MDVA-22026**：修复了从CSV文件导入产品（包括来自外部URL的图像）失败的问题。
1. **MDVA-22383**：修复了保存产品耗时长且页面中断的问题。
1. **MDVA-23845**：修复了在启用JavaScript缩小后无法预览电子邮件模板的问题。
1. **MDVA-26639**：修复了以下问题：如果创建新的订单确认电子邮件模板，则订单邮件中缺少订单项目。
1. **MDVA-33168**：修复了通过API更新产品属性时，所有其他属性均更改为空值的问题。
1. **MDVA-36170**：这修复了GraphQL查询未使用类别缓存标记缓存的问题。

使用左侧的菜单导航到特定的修补程序页面。
