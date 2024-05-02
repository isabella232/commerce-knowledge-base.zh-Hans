---
title: 'ACSD-49849：客户电子邮件已由PayPal电子邮件取代'
description: 应用ACSD-49849修补程序以修复Adobe Commerce问题，该问题导致在通过GraphQL向PayPal Express下订单时，客户电子邮件被替换为PayPal电子邮件。
exl-id: 826ea90a-ac10-43e8-aa88-bd69b152ded8
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-49849：客户电子邮件已替换为 [!DNL PayPal] 电子邮件

ACSD-49849修补程序修复了将客户的电子邮件替换为 [!DNL PayPal's] 在下订单时发送电子邮件 [!DNL PayPal Express] 通过GraphQL。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.29。 修补程序ID为ACSD-49849。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户的电子邮件已替换为 [!DNL PayPal's] 在下订单时发送电子邮件 [!DNL PayPal Express] 通过GraphQL。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. 启用和配置 [!DNL PayPal Express] 并设置 **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. 转到 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**，并创建一个简单的产品。
1. 使用GraphQL完成访客签出。 有关更多信息，请参阅 [GraphQL签出教程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) 请参阅Adobe Commerce开发人员文档。
1. 使用 [!DNL PayPal Express] 作为付款方式。
1. 请注意您在步骤中使用的电子邮件 [为购物车设置电子邮件](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) 请参阅Adobe Commerce开发人员文档。
1. 下订单后，转到Adobe Commerce管理员，然后查看已创建订单中的电子邮件。

<u>预期结果</u>：

电子邮件与结账时设置的相同。

<u>实际结果</u>：

在签出期间设置的电子邮件将被中设置的电子邮件覆盖 [!DNL PayPal] 帐户。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
