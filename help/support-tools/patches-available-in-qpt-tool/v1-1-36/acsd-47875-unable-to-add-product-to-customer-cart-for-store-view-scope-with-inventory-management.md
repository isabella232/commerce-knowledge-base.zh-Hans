---
title: “ACSD-47875：无法通过库存管理将产品添加到购物车以商店查看范围”
description: 应用ACSD-47875修补程序以修复Adobe Commerce问题，该问题导致无法通过清单管理将产品从管理员添加到特定商店视图范围的客户购物车中。
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: fa5ecd65-704f-49bd-b3cc-3d60ff7e1dce
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-47875：无法通过库存管理将产品添加到购物车以商店查看范围

ACSD-47875修补程序修复了以下问题：在具有库存管理的特定商店视图范围内，无法从管理员将产品添加到客户购物车中。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.36。 修补程序ID为ACSD-47875。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员用户无法使用将产品添加到客户购物车 **[!UICONTROL Manage Shopping Cart]** 在管理员中为安装了MSI的特定存储视图范围提供的功能。

<u>先决条件</u>：

[!DNL Adobe Commerce Inventory Management (MSI)] 模块已安装并启用。

<u>重现问题的步骤</u>：

1. 创建网站、商店和商店视图。
1. 创建其他源，而不是 *默认*.
1. 创建一个新库存，并将其分配给新网站和新来源。
1. 为新网站创建新客户。
1. 仅将产品分配给新网站；从默认网站中取消分配。

   * 分配新来源并设置数量 *大于0* 新源和 *0* 作为默认源。

1. 转到 **[!UICONTROL Customer Edit]** 页面。 单击 **[!UICONTROL Manage Shopping Cart]**.
1. 将存储视图范围更改为新的存储视图。
1. 转到 **[!UICONTROL Products]** 和搜索产品。
1. 选择产品并单击 **[!UICONTROL Add selections to my cart]**.

<u>预期结果</u>：

产品即添加到购物车。

<u>实际结果</u>：

* 引发以下错误： *您尝试添加的产品不可用。*
* 产品未添加到购物车。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
