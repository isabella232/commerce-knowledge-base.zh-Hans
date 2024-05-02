---
title: '错误：在云基础架构上的Adobe Commerce上预热失败'
description: '本文为页面缓存预热并失败并出现错误提供了解决方案：'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# 错误：在云基础架构上的Adobe Commerce上预热失败

本文为页面缓存预热并失败并出现错误提供了解决方案：

*错误：预热失败：`<website link>`*

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，全部 [支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

缓存预热失败。

<u>重现问题的步骤</u>：

启动缓存预热操作。

<u>预期结果</u>：

页面或整个网站加载。

<u>实际结果</u>：

站点不可用或响应时间太长。 *错误：预热失败：`<website link>`*

## 原因

在启用HTTP访问控制的情况下，缓存预热不起作用。

## 解决方案

确保未启用访问控制：转到特定的分支/环境，然后单击 **设置** 图标，然后查看 **HTTP访问控制** 设置 — 在此情况下不能进行缓存热启动，必须禁用访问控制。

## 相关阅读

* [Adobe Commerce用户指南>全页缓存](https://docs.magento.com/user-guide/system/cache-full-page.html) 在我们的用户指南中。
* [缓存预热和网站在Adobe Commerce上不可用](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md) 在我们的支持知识库中。
