---
title: '部署错误： *下载时出错7 ...端口443：连接被拒绝*'
description: '本文提供了针对部署错误的解决方案：*“下载时出错7 ...端口443：连接被拒绝”*。'
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 部署错误： *下载时出错7...端口443：连接被拒绝*

本文修复了部署失败并出现以下错误消息的问题：

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## 受影响的版本

云基础架构上的Adobe Commerce， [所有受支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

部署失败，出现 **curl错误7** 消息。

<u>重现问题的步骤</u>：

触发部署。

<u>预期行为</u>：

部署成功。

<u>实际行为</u>：

部署失败，并出现以下错误： *下载……端口443时出现CURL错误7：连接被拒绝* 显示在部署日志中。

## 原因

这可能是由于与存储库的缓存连接丢失所致。

## 解决方案

要求项目中的超级用户运行此命令：

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

要检查项目中的谁是超级用户，请参阅 [查看用户的项目角色](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role) 《Commerce on Cloud Infrastructure指南》中的。

## 推荐阅读

* [Adobe Commerce部署疑难解答程序](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter.html).
* [无法访问云存储库上的Adobe Commerce：部署时出现403 Forbidden或404 Not Found错误](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html).
* [部署失败，并显示“构建项目时出错：构建挂接失败，状态代码为1”](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html).
