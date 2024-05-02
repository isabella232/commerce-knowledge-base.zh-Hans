---
title: 在寻找特定产品时获得数千个结果
description: 本文提供了一种解决方案，来解决您在查找特定产品时会获得数千个搜索结果的问题。
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 在寻找特定产品时获得数千个结果

本文提供了一种解决方案，来解决您在查找特定产品时会获得数千个搜索结果的问题。

## 受影响的产品和版本

* Adobe Commerce所有版本 [!DNL ElasticSearch] 已安装

## 问题

您要查找特定产品(例如， *WSH12-32-Red*)，但搜索返回了大量类似的产品。

## 解决方案

中全文搜索的性质 [!DNL ElasticSearch] 基于相关性，而不是精确匹配。 因此，首先排序的是大多数相关的匹配项（如完全匹配的SKU）。

但是，如果您需要与搜索词完全匹配的搜索结果（完全匹配），则应该在搜索查询中使用引号。 例如，查询 *WSH12-32-Red* 不带引号将返回多个与完全匹配的结果(product with *SKU WSH12-32-Red*)在结果中显示在首位。 但引用查询 *“WSH12-32-Red”* 将仅返回一个完全匹配的结果。
