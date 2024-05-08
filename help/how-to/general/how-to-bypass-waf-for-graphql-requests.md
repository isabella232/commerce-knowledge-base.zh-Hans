---
title: 如何为GraphQL请求绕过WAF
description: 本文介绍了如何为GraphQL请求绕过WAF。
feature: GraphQL
source-git-commit: c35d4ba82fbe1657756e160a73fd575c736b4e1c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 如何为GraphQL请求绕过WAF

本文说明在执行以下操作时，如何为GraphQL请求跳过WAF： [!DNL Fastly] WAF正在阻止您的GraphQL请求。

## 受影响的产品和版本

云基础架构上的Adobe Commerce（所有版本）

## 原因

由于GraphQL请求的内在特性，可能会出现大量重复字符，这些字符会触发对请求的误报阻止。 [!DNL Fastly] WAF。

## 解决方案

1. 通过添加自定义代码片段，绕过这些请求的WAF [!DNL Fastly] Magento模块：

   类型：recv优先级： 15内容：

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. 单击 **[!UICONTROL Upload VCL to Fastly]**.

## 相关阅读

* [Web应用程序防火墙(WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service) 《云基础架构上的Commerce指南》中的。
* [自定义VCL快速入门](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets) 《云基础架构上的Commerce指南》中的。

