---
title: 无法更改“app/etc/env.php”中的搜索引擎
description: 本文解决了一个问题：您尝试在Commerce管理员中更改搜索引擎，但字段被锁定。
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 无法更改中的搜索引擎 `app/etc/env.php`

本文为您尝试从删除搜索引擎配置的问题提供了解决方案。 `app/etc/env.php` 文件，但在重新部署后，配置将恢复为以前的设置或更改为 [!DNL OpenSearch] 默认情况下。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce， [所有受支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

您尝试在Commerce管理员中更改搜索引擎，但字段被锁定。

## 原因

搜索引擎配置已锁定在 `app/etc/env.php` 文件，或中明确定义搜索引擎 `.magento.env.yaml` 文件。

## 解决方案

1. 查看 `.magento.env.yaml` 在部署阶段下文件，并查看 `SEARCH_CONFIGURATION` 变量已配置。 示例：

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. 是  `SEARCH_CONFIGURATION` 变量是否存在？ 如果不存在，则搜索引擎配置将被锁定到 [!DNL OpenSearch] 默认情况下。 要更改配置，必须将变量添加到 `.magento.env.yaml` 具有搜索引擎相应值的文件。 如果 `SEARCH_CONFIGURATION` 变量存在，并且您希望修改引擎，请替换中引擎的现有值 `.magento.env.yaml`. 可能/已知值： [!DNL opensearch]， [!DNL livesearch]， [!DNL elasticsuite]， [!DNL amasty_elastic]、和 [!DNL amasty_elastic_opensearch].
1. 重新部署实例。
1. 管理员中的搜索引擎字段将保持锁定状态，但应该使用您指定的值更新该字段。

## 相关阅读

* [Commerce管理员中的锁定字段](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) 《Commerce on Cloud Infrastructure指南》中的。
