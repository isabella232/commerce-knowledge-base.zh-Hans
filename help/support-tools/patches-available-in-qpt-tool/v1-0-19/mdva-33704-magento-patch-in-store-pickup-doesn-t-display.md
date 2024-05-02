---
title: “MDVA-33704修补程序：不显示店内收取情况”
description: MDVA-33704修补程序解决了具有店内取货选项的产品无法显示为配送方式的问题。
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# MDVA-33704修补程序：不显示店内收取情况

MDVA-33704修补程序解决了具有店内取货选项的产品无法显示为配送方式的问题。

此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.19。 修补程序ID为MDVA-33704。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.4.0-2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：<br>

**在商店中挑选** 已启用

<u>重现问题的步骤</u>：

1. 将产品添加到购物车。
1. 转到“结帐”。
1. 添加配送信息，然后选择店内取货之外的任何配送方式。
1. 选择 **继续付款**，但不转到支付页面。
1. 而是返回到 **联系人和送货** 部分。
1. 选择 **取车**.
1. 选择 **存储** 和 **单击以付款**.
1. 请注意，您的送货地址会自动输入为帐单地址。
1. 刷新网页。

<u>预期结果</u>：

店内装货选项将按预期显示为配送方式。

<u>实际结果</u>：

店内取货选项不会显示为配送方式。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
