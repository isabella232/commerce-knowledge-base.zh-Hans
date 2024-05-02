---
title: 在Adobe Commerce 2.4.x中无法进行精确匹配搜索
description: 本文澄清了Adobe Commerce 2.4.x中使用同一搜索字符串的存储前端搜索结果与Adobe Commerce 2.3.x不同的问题。
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# 在Adobe Commerce 2.4.x中无法进行精确匹配搜索

本文澄清了Adobe Commerce 2.4.x中使用同一搜索字符串的存储前端搜索结果与Adobe Commerce 2.3.x不同的问题。

## 受影响的产品和版本

- Adobe Commerce（所有部署方法）2.4.x、2.3.x
- 实时搜索

## 问题

<u>先决条件：</u>

您的产品具有属性值 `Saga 1` 和 `Saga 16` 在Adobe Commerce 2.3和Adobe Commerce 2.4商店中。

<u>重现问题的步骤：</u>

1. 在Adobe Commerce 2.3支持的商店前面，输入 *佐贺1* 在搜索字段中并单击 **Search**.
1. 请注意，在搜索结果中，您只会获得具有属性值的产品 `Saga 1`.
1. 在Adobe Commerce 2.4支持的商店前面，输入 *佐贺1* 在搜索字段中并单击 **Search**.

<u>实际结果：</u>

2.4中的搜索结果包含具有属性值的产品 `Saga 1` 和 `Saga 16`.

<u>预期结果：</u>

2.4中的搜索结果与2.3类似，仅包含具有属性值的产品 `Saga 1`.

## 原因

2.3.x中使用的Adobe Commerce本机搜索功能提供了完全匹配的搜索结果。 虽然随Adobe Commerce 2.4.x一起发布的可供安装的可选模块Live Search的实施方式不同，但实际结果是使用该模块时的预期行为。

## 相关阅读

[安装Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) 在我们的用户指南中。

[实时搜索](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search) 在我们的开发人员文档中。
