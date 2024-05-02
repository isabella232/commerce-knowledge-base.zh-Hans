---
title: 'MDVA-37182：Elasticsearch6和7中的搜索结果不一致'
description: MDVA-37182修补程序修复了Elasticsearch版本6和版本7中的搜索行为不一致的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22后，即可使用此修补程序。 修补程序ID为MDVA-37182。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 6c4e2d2f-cced-487d-b253-fd0c80bc6067
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-37182：Elasticsearch6和7中的搜索结果不一致

MDVA-37182修补程序修复了Elasticsearch版本6和版本7中的搜索行为不一致的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.22。 修补程序ID为MDVA-37182。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.4.1-2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

搜索行为不一致。

<u>重现问题的步骤</u>：

1. 创建具有以下详细信息的产品：
   * 名称： “5127AC”、“5127SS”、“5127AB”
   * SKU：“product1”、“product2”、“product3”
1. 将搜索引擎设置为Elasticsearch6 (ES6)。
1. 运行完全重新索引。
1. 在店面搜寻“5127s”
1. 将搜索引擎设置为Elasticsearch7 (ES7)。
1. 运行完全重新索引。
1. 在店面搜寻“5127s”

<u>实际结果：</u>：

ES6：搜索未返回任何结果。ES7：搜索返回三个产品。

<u>预期结果：</u>：

对于两个版本，搜索将返回一个产品。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
