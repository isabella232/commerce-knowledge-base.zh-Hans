---
title: 部署时出现“不支持当前版本的RDBMS”错误
description: '本文提供了一个解决方案，用于当部署失败并且部署日志中存在以下错误时： *当前版本的RDBMS不受支持*。'
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# 部署时出现“不支持当前版本的RDBMS”错误

本文为部署失败并在部署日志中出现以下错误时提供了解决方案： *不支持RDBMS的当前版本*.

## 受影响的产品和版本

云基础架构上的Adobe Commerce，从2.3.0到2.3.7-p1，从2.4.0到2.4.3。

## 问题

此错误消息表示您尝试升级到的Adobe Commerce版本不再支持当前的MariaDB版本，必须将MariaDB升级到兼容版本。


<u>重现问题的步骤</u>：

尝试部署。

<u>预期结果</u>：

部署成功。

<u>实际结果</u>：

部署失败，并出现错误消息： *不支持RDBMS的当前版本*.

## 原因

您的MariaDB版本与您尝试升级到的Adobe Commerce版本不兼容。

## 解决方案

在升级应用程序之前，必须将MariaDB服务升级到兼容版本。


有关Adobe Commerce上云基础架构的集成分支专业计划架构（以及入门架构中的所有分支），请关注 [配置服务](https://devdocs.magento.com/cloud/project/services.html) 在我们的开发人员文档中。

有关Adobe Commerce上云基础架构Pro计划架构的暂存和生产，请 [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) ，以在部署Adobe Commerce版本升级之前请求升级服务。


## 相关阅读

* [构建和部署的最佳实践](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) 在我们的开发人员文档中。
* [Adobe Commerce 2.3.5升级：压缩为动态表](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html) 在我们的支持知识基础中。
