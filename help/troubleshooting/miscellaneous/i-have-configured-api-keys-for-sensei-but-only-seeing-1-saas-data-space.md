---
title: 我已为Sensei配置了API密钥，但只看到一个SaaS数据空间
description: 本文提供了一种解决方案，来解决在为Sensei配置API密钥后您只能看到一个SaaS数据空间的问题。
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 我已为Sensei配置了API密钥，但只看到一个SaaS数据空间

本文提供了一种解决方案，来解决在为Sensei配置API密钥后您只能看到一个SaaS数据空间的问题。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）：所有版本
* Magento Open Source：所有版本
* 扩展或技术(Fastly、New Relic等)、Adobe Sensei(产品Recommendations/实时搜索)

## 问题

我已为Sensei配置了API密钥，但我只看到一个SaaS数据空间。

## 原因

显示的SaaS数据空间数量取决于您的Commerce许可证：

* Adobe Commerce — 一个生产数据空间；两个测试数据空间
* Magento Open Source — 一个生产数据空间；无测试数据空间

## 解决方案

* 确保在帐户所有者的帐户上创建API密钥。 即使已授予您对其帐户的共享访问权限，并在您自己的帐户中创建了密钥，这也不会授予您多个数据空间。
* 如果密钥是在帐户所有者的帐户中生成的，请确保许可证有效，即没有待定发票。
