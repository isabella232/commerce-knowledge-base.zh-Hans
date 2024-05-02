---
title: '''ACSD-50234：使用订购的确认电子邮件中的客户名称不正确 [!DNL PayPal]’'
description: Adobe Commerce应用ACSD-50234修补程序以修复以下问题：在使用下订单的确认电子邮件中，客户名称显示不正确 [!DNL PayPal].
exl-id: b2e9c25a-5dd5-4b37-81e3-ca960078da77
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50234：使用下达的订单的确认电子邮件中的客户名称不正确 [!DNL PayPal]

ACSD-50234修补程序修复了以下问题：在使用下订单的确认电子邮件中，客户名称显示不正确 [!DNL PayPal]. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.29。 修补程序ID为ACSD-50234。 请注意，Adobe Commerce 2.4.5中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订单的确认电子邮件，使用 [!DNL PayPal] 显示错误的客户名称。

<u>重现问题的步骤</u>

1. 启用 **[!UICONTROL PayPal Express Checkout]**.
1. 作为来宾导航到前端。
1. 将产品添加到购物车。
1. 使用结帐 **[!UICONTROL PayPal Express Checkout]** 作为付款方式。
1. 检查订单确认电子邮件。

<u>预期结果</u>

订单确认电子邮件、发票电子邮件以及所有与发运相关的电子邮件均以客户的名称发送。

<u>实际结果</u>

订单确认电子邮件、发票电子邮件以及所有与发运相关的电子邮件均发送至 *来宾*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
