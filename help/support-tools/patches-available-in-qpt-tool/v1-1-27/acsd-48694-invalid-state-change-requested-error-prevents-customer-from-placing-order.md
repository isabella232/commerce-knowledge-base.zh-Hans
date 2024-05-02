---
title: 'ACSD-48694：请求的状态更改无效错误阻止客户下订单'
description: 应用ACSD-48694修补程序以修复Adobe Commerce问题，该问题导致错误*请求的状态更改无效*阻止客户下订单。
exl-id: edf79424-6c4f-4cfd-ab7e-19f95b9bc685
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-48694： *请求的状态更改无效* 错误导致客户无法下订单

ACSD-48694修补程序修复了错误的问题 *请求的状态更改无效* 防止客户下订单。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.27。 修补程序ID为ACSD-48694。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.37-p4、2.4.1 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误 *请求的状态更改无效* 防止客户下订单。

<u>重现问题的步骤</u>：

1. 在此期间添加稍微延迟 `/estimate-shipping-methods` 通过包含 `sleep()` 在 `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` 函数，因此 `/estimate-shipping-methods` 请求在以下时段后完成 `/shipping-information` 在结帐期间从送货步骤到付款步骤时。
1. 配置要使用的会话 [!DNL Redis] 使用 *disable_locking： 1* 设置。
1. 打开 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** 并启用 *[!UICONTROL Persistent Shopping Cart]*.
1. 以客户身份登录并将产品添加到购物车。
1. 让客户会话过期。 永久性Cookie和购物车仍然存在。
1. 现在，转到结帐，添加送货地址并导航到付款部分。
1. 返回主页或任何其他页面，然后使用客户帐户登录。
1. 让会话再次过期。
1. 现在，直接转到结账页面并导航到付款步骤。
1. 尝试下订单。

<u>预期结果</u>：

* 没有错误。
* 订单已成功下达，并且 *谢谢* 页面中显示。

<u>实际结果</u>：

错误 *请求的状态更改无效* 显示，但已下达订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
