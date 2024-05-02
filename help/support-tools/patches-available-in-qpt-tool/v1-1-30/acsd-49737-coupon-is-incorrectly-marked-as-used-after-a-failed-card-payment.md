---
title: 'ACSD-49737：在信用卡付款失败后，错误地标记为使用了优惠券'
description: 应用ACSD-49737修补程序以修复在失败信用卡支付后错误地标记为使用优惠券的Adobe Commerce问题。
exl-id: 77b5ec9c-3c4c-4da3-ba7e-8be3ccea04d0
feature: Orders, Payments
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49737：优惠券被错误地标记为 *已使用* 在信用卡付款失败后

ACSD-49737修补程序修复了优惠券被错误标记为的问题 *已使用* 在信用卡付款失败之后。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.30。 修补程序ID为ACSD-49737。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

优惠券被错误地标记为 *已使用* 在信用卡付款失败之后。

<u>先决条件</u>：

1. 配置 **[!UICONTROL Braintree sandbox payment]** 方法。
1. 确保 [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) 使用者已设置并正在运行。

<u>重现问题的步骤</u>：

1. 创建 **[!UICONTROL Cart Price Rule]** 自动生成优惠券代码。
1. 以客户身份登录。
1. 将产品添加到购物车。
1. 应用自动生成的优惠券代码。
1. 尝试以失败的付款下订单。
1. 检查中的优惠券使用情况 **[!UICONTROL Cart Price Rule]** 在 **[!UICONTROL Manage Coupon Codes]** 选项卡。

<u>预期结果</u>：

优惠券不应标记为 *已使用* 如果付款失败。

<u>实际结果</u>：

* 优惠券代码显示 — 已使用： *是*，使用时间： *1*
* 优惠券代码仅供一次性使用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 安装修补程序后所需的其他步骤

（本节为可选内容；在应用修补程序后，可能需要执行一些步骤来修复此问题。） 

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
