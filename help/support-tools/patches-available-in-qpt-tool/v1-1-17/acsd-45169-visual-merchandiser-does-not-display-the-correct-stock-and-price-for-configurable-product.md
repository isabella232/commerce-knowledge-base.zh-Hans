---
title: 'ACSD-45169：Visual Merchandiser显示可配置产品的不正确库存和价格'
description: ACSD-45169修补程序修复了在应用暂存更新后，可视化促销程序无法显示可配置产品的正确库存和价格的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17后，即可使用此修补程序。 修补程序ID为ACSD-45169。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: 5a7987c8-f276-4917-98f7-645402f4c454
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-45169：Visual Merchandiser显示可配置产品的不正确库存和价格

ACSD-45169修补程序修复了在应用暂存更新后，可视化促销程序无法显示可配置产品的正确库存和价格的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.17。 修补程序ID为ACSD-45169。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

应用暂存更新后，Visual Merchandiser不显示可配置产品的正确库存和价格。

<u>重现问题的步骤</u>：

1. 创建一个简单的产品。
1. 为简单产品创建任何计划更新（您只需要拥有不同的行和实体ID）。
1. 创建可配置的产品。
1. 将可配置产品分配给类别。
1. 打开类别并在Visual Merchandiser部分下观察可配置产品。

<u>预期结果</u>：

Visual Merchandiser显示正确的库存和价格。

<u>实际结果</u>：

Visual Merchandiser显示的库存和价格不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
