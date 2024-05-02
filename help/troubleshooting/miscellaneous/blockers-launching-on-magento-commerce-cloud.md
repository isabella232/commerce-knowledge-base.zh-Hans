---
title: 在云基础架构上的Adobe Commerce上启动阻止程序
description: 本文修复了阻止程序在云基础架构上的Adobe Commerce上启动的问题，包括与Fastly配置、SSL证书、301重定向和静态资产性能相关的问题。
exl-id: 3b2c331f-5d90-4051-ada1-4934538fce79
feature: Cache, Cloud, Marketing Tools, Observability, Paas
role: Developer
source-git-commit: 3dd44b72bc9f02fe808b70355c4331fc28aa3606
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# 在云基础架构上的Adobe Commerce上启动阻止程序

本文修复了阻止程序在云基础架构上的Adobe Commerce上启动的问题，包括与Fastly配置、SSL证书、301重定向和静态资产性能相关的问题。

## 1. Fastly配置

[Fastly](https://www.fastly.com/) 是一个用于提供静态资产的基于清漆的内容交付网络(CDN)。 在生产环境中，云基础架构上的Adobe Commerce需要此项，因此，在暂存环境和生产环境中配置Fastly并测试您的网站(UAT)以启用和配置Fastly非常重要。

>[!WARNING]
>
>启用全页缓存(FPC)后，网站的执行方式会有所不同；请确保在网站正式启用前对其进行测试。

Fastly的配置过程在 [设置Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) 用户指南中的主题。 以下是重要步骤。

### 1a. 确保您安装了最新版本的Fastly模块

确保您安装了最新版本的Fastly模块，以获取最新功能和改进。 要检查您是否拥有最新版本的Fastly，请查看 [升级Fastly模块](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) 在我们的用户指南中。 有关更多详细信息，请查看 [设置Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) 在我们的用户指南中。

### 1b. 使用Commerce管理员启用和配置Fastly

有关更多详细信息，请查看 [获取您的Fastly凭据](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials) 在我们的用户指南中。

### 1c. 上传Fastly VCL片段

有关更多详细信息，请参阅 [将VCL上传到Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) 在我们的用户指南中。

您还可以 [创建并添加自己的自定义VCL片段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html).

### 1d 为Fastly配置DNS


有关详细步骤，请参阅本文： [设置Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings) 在我们的用户指南中。

### 我们的支持知识库中的相关Fastly文章

* [Fastly缓存不适用于云](/help/troubleshooting/miscellaneous/fastly-caching-is-not-working-on-magento-cloud.md)
* [清除云上的Fastly缓存时出错（未成功处理清除请求）](/help/troubleshooting/miscellaneous/error-purging-fastly-cache-on-cloud-the-purge-request-was-not-processed-successfully.md)

## 2.有效的SSL (TLS)证书

问题：如果没有有效且有效的SSL证书，您将无法在“结帐”页面（在暂存环境中）上测试外部付款方法。

推荐 **：** 为暂存或实时域名请求共享SSL证书。

请阅读以下内容，了解SSL证书 [快速常见问题解答](/help/announcements/adobe-commerce-announcements/magento-ssl-tls-certificate-requirements-and-clean-up.md) 文章。

## 3.配置和测试301重定向

问题： 301重定向未提供或配置不正确，导致您的商店在SEO排名和搜索列表中排名下降。

推荐 **：** 仔细配置和测试301重定向。

如果您从旧网站迁移到新网站，301会将您的客户从之前编制索引的旧页面重定向到新商店中的相应页面，如下所示：

http://www.mywebsite.com/old-category-page.html **>** http://www.mywebsite.com/new-seo-friendly-category-page.html

**相关文章：**

* [通过路由重定向.yaml](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/routes/redirects.html) 在我们的用户指南中。
* [通过云控制台重定向](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) 在我们的用户指南中。
* [URL重写](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite.html) 在我们的用户指南中。

## 4.资产绩效

问题：静态资产提供缓慢，导致网站性能不佳（加载时间长、不显示多媒体内容等）。 网站的静态资产包括CSS资源、图像、视频、附加文档等。 组织和提供这些网站的方式是网站性能的一个关键因素。

建议：要确定性能不佳的可能原因，请考虑使用 [Adobe Commerce Performance Toolkit](https://github.com/magento/magento2/tree/2.3/setup/performance-toolkit) 以进行性能测试。 您还可以考虑以下第三方工具：

* [围困](https://www.joedog.org/siege-home/)： HTTP负载测试和基准测试实用程序；支持基本身份验证、Cookie、HTTP、HTTPS和FTP协议。
* [Jmeter](https://jmeter.apache.org/)：一款著名的负载测试和性能测量工具。 帮助衡量尖峰流量的性能，例如，针对闪存销售。
* [New Relic](https://support.newrelic.com/)：查找导致性能变慢的站点进程和区域，并跟踪每个操作（如传输数据、查询、Redis等）的逗留时间。
* [WebPageTest](https://www.webpagetest.org/) （免费）和 [Pingdom](https://www.pingdom.com/) （付费）：实时分析不同来源位置的网站页面加载时间。

您也可以考虑 [缩小](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 用于CSS、JavaScript和HTML。

**相关文章：**

* [测试部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production.html) 在我们的开发人员文档中。
