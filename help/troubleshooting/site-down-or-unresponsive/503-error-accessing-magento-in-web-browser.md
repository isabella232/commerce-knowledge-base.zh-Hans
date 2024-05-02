---
title: 在Web浏览器中访问Adobe Commerce时出现503错误
description: 本文针对在尝试访问Adobe Commerce店面和/或管理员时出现503错误的问题提供了可能的解决方案。
exl-id: 4232aa21-40c2-41b0-9fb0-fc8cd4db8e39
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# 在Web浏览器中访问Adobe Commerce时出现503错误

本文针对在尝试访问Adobe Commerce店面和/或管理员时出现503错误的问题提供了可能的解决方案。

## 受影响的产品和版本

Adobe Commerce 2.3.x

## 问题 {#symptoms}

<u>重现问题的步骤</u>

(先决条件：确保该存储不在 [维护模式](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-mode.html#config-mode-show))。

在Web浏览器中导航到您的Commerce管理员或店面。

<u>预期结果</u>

页面加载。

<u>实际结果</u>

您收到HTTP 503 （服务不可用）错误。 Apache `error.log` 包括以下消息：

*命令“Order”无效，可能拼写错误或由未包含在服务器配置中的模块定义。*

## 原因 {#details}

Apache 2.4兼容性模块 `mod_access_compat` 已禁用，这将导致Adobe Commerce URL重写无法正常工作。

## 解决方案 {#suggested-solution}

启用 `mod_access_compat` Apache模块并重新启动Apache，方法是以具有“root”权限的用户身份运行以下命令：

```bash
a2enmod access_compat
service <name> restart
```

在CentOS上，

```bash
<name>
```

是

```bash
httpd
```

。在Ubuntu，

```bash
<name>
```

是

```bash
apache2
```

.

## 相关阅读 {#additional-resources}

* [Apache有关mod\_access\_compat的文档](https://httpd.apache.org/docs/current/mod/mod_access_compat.html)
* [Apache有关mod\_authz\_host的文档](https://httpd.apache.org/docs/current/mod/mod_authz_host.html)
* [Apache Definitive指南中的Order、Allow、Deny](https://docstore.mik.ua/orelly/linux/apache/ch05_06.htm)
* [askubuntu.com](https://askubuntu.com/questions/335228/changes-in-apache-config-between-12-04-2-and-12-04-3-lts)
