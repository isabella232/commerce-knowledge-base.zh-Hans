---
title: 'MDVA-33289修补程序：签出时地址中的Javascript'
description: MDVA-33289修补程序修复了Javascript在付费地址中显示的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-33289。 请注意，此问题已计划在Adobe Commerce 2.4.3中修复。
exl-id: 247e4f05-7e89-4d37-b3d4-c2cae7595267
feature: Checkout, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-33289修补程序：签出时地址中的Javascript

MDVA-33289修补程序修复了Javascript在付费地址中显示的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.19。 修补程序ID为MDVA-33289。 请注意，此问题已计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：** 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.4.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在启用Google Tag Manager (GTM)的情况下签出时，Javascript会在地址字段中显示。

<u>重现问题的步骤</u>：

1. 启用GTM。 请参阅 [Google Tag Manager](https://docs.magento.com/user-guide/marketing/google-tag-manager.html) ，以了解详细信息。
1. 在店面，添加一些产品到购物车。
1. 看吧。

<u>实际结果</u>：

地址部分会更新，但包含大量Javascript代码文本。

<u>预期结果</u>：

将显示地址。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
