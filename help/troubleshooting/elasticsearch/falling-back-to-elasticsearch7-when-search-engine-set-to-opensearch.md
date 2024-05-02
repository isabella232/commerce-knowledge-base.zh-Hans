---
title: 回退到 [!DNL Elasticsearch7] 当搜索引擎设置为 [!DNL Opensearch]
description: 本文为当*回退到以下位置时的问题提供了解决方案 [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] 在Adobe Commerce中。
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: 6b8eecb3df0bb32344a5861a604a40402bb4d392
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# 回退到 [!DNL Elasticsearch7] 当搜索引擎设置为 [!DNL Opensearch]

本文为以下情况下出现的问题提供了解决方案： *回退到[!DNL Elasticsearch7]* 将搜索引擎设置为时出现错误 [!DNL OpenSearch] 在Adobe Commerce中。

## 受影响的版本

云基础架构上的Adobe Commerce 2.4.4 - 2.4.5

>[!NOTE]
>
>[!DNL OpenSearch] 可作为搜索引擎从Adobe Commerce 2.4.6开始提供。

## 问题

您设置了 **搜索引擎** 到 **[!DNL OpenSearch]**，但在中看到此类错误 `var/log/support_report.log` 文件：

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>重现问题的步骤</u>：

1. 验证 [!DNL OpenSearch] 通过运行此命令安装： `curl 127.0.0.1:9200`<br>
如果它指示 *1.2.4*，则 [!DNL OpenSearch] 已安装。
1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 检查搜索引擎。 它将会显示 [!DNL Elasticsearch7].

## 原因

即使您的版本支持 [!DNL OpenSearch]，则应用程序将仅识别/接受 [!DNL Elasticsearch7] 作为搜索引擎。

从Adobe Commerce版本2.4.6开始，应用程序已更新为允许 [!DNL OpenSearch] 选为搜索引擎。
如果您转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** 在非云环境中，您将能够更改此选项，如 **解决方案** 下。
(注意：在云环境中，此字段无法更改，因为搜索引擎已锁定在 `app/etc/env.php` 文件。)

## 解决方案

更新 `SEARCH_CONFIGURATION` 中的变量 `.magento.env.yaml` 文件，并确保 **搜索引擎** 设置为 *[!DNL elasticsearch7]*.

## 相关阅读

[设置OpenSearch服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) 云基础架构上的Commerce指南中的。
