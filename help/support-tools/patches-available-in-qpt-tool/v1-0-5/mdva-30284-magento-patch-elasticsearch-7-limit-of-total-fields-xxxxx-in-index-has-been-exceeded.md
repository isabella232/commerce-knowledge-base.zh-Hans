---
title: 'MDVA-30284修补程序：Elasticsearch7 — 已超过索引中总字段[XXXXX]的限制'
description: MDVA-30284修补程序解决了在使用Elasticsearch7时收到错误消息“超出索引中总字段\[XXXXX\]的限制”的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.5后，即可使用此修补程序。 修补程序ID为MDVA-30284。
exl-id: cf840558-891a-4a7e-8900-b8434f703be0
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-30284修补程序：Elasticsearch7 — 总字段数限制 [XXXXX] 已超出索引范围

MDVA-30284修补程序解决了在使用Elasticsearch7时收到错误消息“超出索引中总字段\[XXXXX\]的限制”的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装v.1.0.5。 修补程序ID为MDVA-30284。

## 受影响的产品和版本

* 该补丁是为Adobe Commerce on cloud infrastructure 2.3.5-p2设计的
* Elasticsearch7与Adobe Commerce 2.3.5和2.4.x兼容

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Elasticsearch字段限制错误，导致在执行\[catalogsearch\_fulltext\]索引器时出现以下错误：

*总字段数限制 [xxx] 在索引中 [xxxxxx] 已超出*

当您具有大量产品属性时，会发生此问题。 此问题由Elasticsearch计算字段计数的方式触发。 有时，当有属性具有分配给它们的字段时，这些字段将作为单独的索引器索引。 这会导致超出限制警告。

<u>重现问题的步骤：</u>

<u>先决条件</u>

* 已安装module-elasticsearch 100.3.5。
* 已安装Elasticsearch7。
* 将Elasticsearch设置为搜索后端。

1. 为产品创建1000多个属性。
1. 为每个系列创建产品。
1. 运行索引器。

<u>预期结果：</u>

Elasticsearch索引中提供了所有产品。

<u>实际结果：</u>

1. Elasticsearch错误：

   ```
    {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"}],"type":"illegal_argument_exception","reason":"Limit
    of total fields [3000] in index [magento2_product_2_v11] has been exceeded"},"status":400}
   ```

1. 新产品未编制索引。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
