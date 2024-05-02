---
title: 不可见 [!DNL reCAPTCHA] 结账时失败，导致订单无法下达
description: 应用ACSD-54656修补程序以修复不可见的Adobe Commerce问题 [!DNL reCAPTCHA] 在结账期间无法正常工作，从而导致订单无法下达。
feature: Checkout, Gift
role: Admin, Developer
exl-id: dc26659e-ca34-461e-af91-b230c5afa919
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54656：不可见 [!DNL reCAPTCHA] 在结账期间无法正常工作，从而导致订单无法下达。

ACSD-54656修补程序修复了不可见的问题。 [!DNL reCAPTCHA] 在结账期间无法正常工作，从而导致订单无法下达。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.46。 修补程序ID为ACSD-54656。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

不可见 [!DNL reCAPTCHA] 在结账期间无法正常工作，从而导致订单无法下达。

<u>重现问题的步骤</u>：

1. 启用任何类型 [!DNL reCAPTCHA] 用于上的礼品卡 [!UICONTROL Checkout] 页面。
1. 将产品添加到购物车并转到 **[!UICONTROL Checkout]** 页面。
1. 展开礼品卡表单并填写有效的礼品卡优惠券。
1. 单击 **[!UICONTROL See balance and apply]** 按钮。

<u>预期结果</u>：

已成功应用礼品卡。

<u>实际结果</u>：

出现以下错误消息： *[!DNL reCAPTCHA]验证失败，请重试*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
