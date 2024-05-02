---
title: 'MDVA-28763：通过REST API管理产品图像时出现问题'
description: MDVA-28763修补程序解决了与使用REST API管理媒体集相关的多个问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5后，即可使用此修补程序。 计划在更高的Adobe Commerce版本中修复这些问题。
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763：通过REST API管理产品图像时出现问题

MDVA-28763修补程序解决了与使用REST API管理媒体集相关的多个问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.5。 计划在较新版本的Adobe Commerce中修复这些问题(请参阅 [问题](#issues).

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce内部部署2.3.2 - 2.3.3.x
* 云基础架构上的Adobe Commerce 2.3.2 - 2.3.3.x

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题 {#issues}

MDVA-28763修补程序修复了以下与介质集相关的问题：

* 使用REST API更新YouTube视频时(`PUT rest/V1/products/ {SKU}`，Adobe Commerce会显示视频的缩略图，但当您单击“播放”按钮时，视频播放器不会加载。 计划在Adobe Commerce 2.3.6中修复。
* `PUT /V1/products/:sku/media/:entryId` 调用将创建一个新条目，而不是替换现有条目。 已在Adobe Commerce 2.3.5中修复。
* 将产品分配给多个商店视图时，产品图像删除出现问题。 已在Adobe Commerce 2.3.4中修复。
* 现在，具有多个网站的商家可以使用REST创建和更新产品，同时保留图像和图像角色继承。 以前，当商家使用REST创建和更新产品，并为商店视图更新产品时，将为该商店视图加载并保存默认图像角色。 因此，存储视图图像角色在更新后停止从默认范围继承。 计划在Adobe Commerce 2.3.6中修复。
* 媒体属性（图像、缩略图、..） 存储视图中引用了已删除映像的值，这些映像未自动清理。 计划在Adobe Commerce 2.4.2中修复。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
