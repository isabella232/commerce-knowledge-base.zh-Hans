---
title: 'ACSD-52824：为公司客户显示的已禁用付款方法'
description: 应用ACSD-52824修补程序以修复Adobe Commerce问题，其中 [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] 尽管已在“公司”设置中禁用付款方法，但仍会为公司客户显示付款方法。
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 03496fb1-d492-4f02-9cdc-466cb571a2eb
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52824：为公司客户显示的已禁用付款方法

ACSD-52824修补程序修复了以下问题 [!DNL PayPal Express]， [!DNL Google Pay]、和 [!DNL Apple Pay] 尽管已在“公司”设置中禁用付款方法，但仍会为公司客户显示付款方法。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.45。 修补程序ID为ACSD-52824。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

为公司客户显示禁用的付款方法。

<u>重现问题的步骤</u>：

1. 配置并启用 [!DNL PayPal Express Checkout]. 导航到 **[!UICONTROL Basic Settings]** >选择 **[!DNL PayPal Express Checkout]** 并设置以下项的选项： **[!UICONTROL Display on Shopping Cart]** 到 *是*.
1. 配置 [!DNL Braintree] 并启用 [!DNL Apple Pay] 和 [!DNL Google Pay] 到 [!DNL Braintree].
1. 导航到 **[!UICONTROL Customers]** > **[!UICONTROL Companies]** 并创建一家新公司。
1. 单击 **[!UICONTROL Advanced Settings]**，找到 **[!UICONTROL Applicable Payment Methods]** 并选择 **[!UICONTROL Selected Payment Methods]**.
1. 下 **[!UICONTROL Selected Payment Methods]**，选择已启用且未关联的支付方式 *[!DNL PayPal Express Checkout]*， *[!DNL Apple Pay]*，或 *[!DNL Google Pay]*. 例如，选择 **[!UICONTROL Check/Money Order]**.
1. 选择适当的付款方法后，创建一个新客户并将它们与之前创建的公司关联。
1. 使用与公司关联的客户帐户登录，然后继续将商品添加到购物车。
1. 在结账过程中，请注意迷你购物车、购物车和支付步骤。

<u>预期结果</u>：

付款选项来源 [!DNL PayPal] 和 [!DNL Braintree] 在迷你购物车和购物车中不可见。

<u>实际结果</u>：

付款选项来源 [!DNL PayPal] 和 [!DNL Braintree] 在迷你购物车和购物车中保持可见。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
