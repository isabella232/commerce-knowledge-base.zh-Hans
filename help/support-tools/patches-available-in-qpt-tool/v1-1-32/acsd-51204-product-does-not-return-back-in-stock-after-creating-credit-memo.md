---
title: 'ACSD-51204：创建贷项通知单后，产品未返回库存'
description: 应用ACSD-51204补丁以修复Adobe Commerce问题，该问题导致产品在创建贷项通知单后未重新补充库存。
feature: Orders, Products, Returns
role: Admin
exl-id: 302033bc-2ca5-40d6-b692-24ae46b21c31
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204：创建贷项通知单后，产品未返回库存

ACSD-51204修补程序修复了在创建贷项通知单后产品未重新上架的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.32。 修补程序ID为ACSD-51204。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

已售出的产品在创建贷项通知单后未返回库存。

<u>重现问题的步骤</u>：

1. 安装 **[!UICONTROL Adobe Commerce]** 并启用 **[!UICONTROL Inventory Management Module]** 默认 *源* 和 *stock* 仅限。
1. 添加 **[!UICONTROL new product]** 具有数量 *10*.
1. 将产品分配给 **[!UICONTROL default stock]**.
1. 在店面，将产品添加到购物车中，并下达整个可用数量10的订单。
1. 在管理面板中，生成 *发票* 和 *装运* 订单的订单。
1. 创建 **[!UICONTROL Credit Memo]** 使用 *返回股票* 选中复选框。
1. 检查产品的 **[!UICONTROL Salable Quantity]** 在“管理员”中。

<u>预期结果</u>：

产品的销售量必须返回到 *10*.

<u>实际结果</u>：

产品的可销售数量保留为 *0*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
