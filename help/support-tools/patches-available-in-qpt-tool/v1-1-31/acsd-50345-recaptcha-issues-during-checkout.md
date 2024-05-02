---
title: 'ACSD-50345：签出期间出现reCAPTCHA问题'
description: 应用ACSD-50345修补程序以修复Adobe Commerce问题，该问题导致在下订单时和结账过程中reCAPTCHA v2和v3验证失败。
exl-id: ac8c8130-0e4d-4610-9a55-afa779cce7a0
feature: Checkout, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-50345：在签出期间出现reCAPTCHA问题

ACSD-50345修补程序修复了在下订单和结账期间reCAPTCHA v2和v3验证失败的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.31。 修补程序ID为ACSD-50345。 请注意，该问题已在Adobe Commerce 2.4.6中部分修复，并计划在Adobe Commerce 2.4.7中完全修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

**用例#1**

提交失败的付款后，Google reCAPTCHA v2未重新加载。

<u>重现问题的步骤</u>

1. 配置 **[!UICONTROL Google reCAPTCHA v2]** (*我不是机器人*)。
1. 启用 **[!UICONTROL reCAPTCHA]** 结帐。
1. 尝试在不单击的情况下下订单 **[!UICONTROL reCAPTCHA]**.
1. 用户收到有关缺少的reCAPTCHA的错误消息后(*reCAPTCHA验证失败，请重试*)，然后单击 **[!UICONTROL reCAPTCHA]** 然后尝试下订单。

<u>预期结果</u>

订单的reCAPTCHA不正确。

<u>实际结果</u>

引发错误 —  *reCAPTCHA验证失败，请重试* 和 *没有ID为4的此类购物车*

**用例#2**

Google reCAPTCHA v3 Invisible在签出时不起作用，无法下订单。 `PlaceOrder` 事件未触发。

<u>重现问题的步骤</u>

1. 配置 **[!UICONTROL reCAPTCHA v3 Invisible]** 从 **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**.
1. 启用 **[!UICONTROL reCAPTCHA v3 Invisible]** ，以结帐/下订单 **[!UICONTROL Storefront]** 选项卡。
1. 尝试使用 [!UICONTROL Check/Money order] 付款方式。

<u>预期结果</u>

订单应与 **[!UICONTROL reCAPTCHA]** 打开。

<u>实际结果</u>

单击 **[!UICONTROL Place Order]** 按钮，它会被禁用，并且不会发生任何进一步的情况。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
