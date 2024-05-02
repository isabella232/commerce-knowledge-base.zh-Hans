---
title: robots.txt在云基础架构上显示404错误Adobe Commerce
description: 本文修复了Adobe Commerce中的“robots.txt”文件在云基础架构上引发404错误的问题。
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt在云基础架构上显示404错误Adobe Commerce

本文修复了 `robots.txt` 文件在云基础架构上的Adobe Commerce中引发404错误。

## 受影响的产品和版本

云基础架构上的Adobe Commerce（所有版本）

## 问题

此 `robots.txt` 文件不起作用，并引发Nginx异常。 此 `robots.txt` 文件是“动态”生成的。 此 `robots.txt` 文件不可由访问 `/robots.txt` URL，因为Nginx具有强制重定向所有 `/robots.txt` 请求 `/media/robots.txt` 文件不存在。

## 原因

当Nginx未正确配置时，通常会发生这种情况。

## 解决方案

解决方案是禁用重定向的Nginx规则 `/robots.txt` 请求 `/media/robots.txt` 文件。 启用了自助服务的商家可以自行完成此操作，而未启用自助服务的商家需要创建支持工单。

如果未启用自助服务（或者不确定是否启用自助服务）， [提交Magento支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 请求从中删除Nginx重定向规则 `/robots.txt` 请求 `/media/robots.txt`.

如果您已启用自助服务，请至少将ECE-Tools升级到2002.0.12，并删除 `.magento.app.yaml` 文件。 您可以引用 [添加站点地图和搜索引擎机器人](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html) 查看我们的开发人员文档，以了解更多信息。

## 相关阅读

* [如何阻止恶意流量以进行Fastly级别的Magento Commerce Cloud](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md) 在我们的支持知识库中。
* [添加站点地图和搜索引擎机器人](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 在我们的开发人员文档中。
* [搜索引擎机器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots) 在我们的用户指南中。
