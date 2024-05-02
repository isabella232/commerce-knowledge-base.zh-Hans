---
title: “MDVA-35155：选项标题更改后无法购买捆绑产品”
description: MDVA-35155修补程序解决了更改选项标题后无法购买捆绑包产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-35155。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 79770c69-1bb0-48d8-acdf-c8c1272f9da8
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-35155：选项标题更改后无法购买捆绑产品

MDVA-35155修补程序解决了更改选项标题后无法购买捆绑包产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.19。 修补程序ID为MDVA-35155。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.0-2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

更改选项标题后无法购买捆绑包产品。

<u>重现问题的步骤</u>：

1. 通过以下方式创建新的捆绑包产品 **产品导入**.
1. 产品在管理员和前端中都是正常的（有库存，可以添加到购物车中）。
1. 使用中名称的更改更新同一产品 `bundle_values` 并重新导入产品。

<u>预期结果</u>：

现有包选项将更新为新名称，并在其中保留相同的项目。

<u>实际结果</u>：

* 管理员尝试将具有相同SKU的产品合并到单个捆绑选项部分中，从而导致选项部分为空。
* 产品在前端没有库存（即使是在重新指数之后）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
