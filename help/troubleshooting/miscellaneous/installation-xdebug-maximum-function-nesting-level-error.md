---
title: 安装xdebug最大函数嵌套级别错误
description: 本文修复了安装期间出现的xdebug最大函数嵌套级别错误。
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# 安装xdebug最大函数嵌套级别错误

本文修复了安装期间出现的xdebug最大函数嵌套级别错误。

## 详细信息

在Adobe Commerce安装过程中，会显示一条与以下内容类似的消息：

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

强烈建议不要使用 `xdebug` 在生产环境中！

## 解决方案

存在已知问题 `xdebug` 会影响Adobe Commerce的安装或对storefront或Commerce Admin的安装后访问权限。

有关详细信息，请参阅 [xdebug的已知问题](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md) 在我们的支持知识库中。
