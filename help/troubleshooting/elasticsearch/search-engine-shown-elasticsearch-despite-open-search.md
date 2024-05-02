---
title: ’[!DNL Elasticsearch] 显示为搜索引擎，尽管 [!DNL OpenSearch] 安装
description: 本文为以下问题提供了解决方案： [!DNL Elasticsearch] 即使安装或升级到，仍显示为云上Adobe Commerce的搜索引擎 [!DNL OpenSearch].
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: 1a36e74807e6d32b0810416b6fb61aeca6f9be94
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# [!DNL Elasticsearch] 显示为搜索引擎，尽管 [!DNL OpenSearch] 安装

本文为以下问题提供了解决方案： [!DNL Elasticsearch] 即使安装或升级到，仍显示为云上Adobe Commerce的搜索引擎 [!DNL OpenSearch].

## 受影响的版本

Adobe Commerce on cloud 2.4.3-p2 - 2.4.5-p6

>[!NOTE]
>
>[!DNL OpenSearch] 可作为搜索引擎从Adobe Commerce 2.4.6开始提供。

## 问题

[!DNL Elasticsearch] 即使安装或升级到，仍显示为云上Adobe Commerce的搜索引擎 [!DNL OpenSearch].

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. 检查搜索引擎。 它将会显示 [!DNL Elasticsearch7].

## 原因

Adobe Commerce进行了硬编码以指定 [!DNL Elasticsearch7] 作为搜索引擎。

## 解决方案

验证是否 [!DNL OpenSearch] 已安装，请运行以下命令：

**方法1**：

* 在服务器上运行以下命令： `curl 127.0.0.1:9200`. 它应该会返回 [!DNL OpenSearch] 包含其版本。

**方法2**：

* 在Magento云CLI上使用以下命令： `magento-cloud relationships -p <project_id>`. 使用该命令后，找到 [!DNL OpenSearch].

## 相关阅读

[设置OpenSearch服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html) 云基础架构上的Commerce指南中的。
