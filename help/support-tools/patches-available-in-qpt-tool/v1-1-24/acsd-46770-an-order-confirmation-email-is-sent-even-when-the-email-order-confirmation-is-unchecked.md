---
title: 'ACSD-46770：即使在 [!UICONTROL Email Order Confirmation] 已取消选中'
description: 应用ACSD-46770补丁以修复在下列情况下发送订单确认电子邮件的Adobe Commerce问题 [!UICONTROL Email Order Confirmation] 未选中。
exl-id: 9cbf3a57-1f59-4030-b432-0e6cad410a27
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46770：即使在以下情况下也发送订单确认电子邮件 **[!UICONTROL Email Order Confirmation]** 未选中

ACSD-46770修补程序修复了以下问题：即使在 **[!UICONTROL Email Order Confirmation]** 未选中。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.24。 修补程序ID为ACSD-46770。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使出现以下情况，也会发送订单确认电子邮件 **[!UICONTROL Email Order Confirmation]** 未选中。

<u>重现问题的步骤</u>：

1. 创建客户帐户。
1. 转到 **[!UICONTROL Sales]** > **[!UICONTROL Order]** 并单击  **[!UICONTROL Create New Order]**.
1. 选择客户，将产品添加到订单中，填写地址，然后选择送货和付款方式。
1. 在提交订单之前，取消选择 **[!UICONTROL Email Order confirmation]** 复选框。
1. 单击 **[!UICONTROL Submit Order]** 以创建订单。

<u>预期结果</u>：

如果出现以下情况，则不应发送订单确认电子邮件 **[!UICONTROL Email Order Confirmation]** 未选中。

<u>实际结果</u>：

无论是否取消选择，都会发送订单确认电子邮件 **[!UICONTROL Email Order Confirmation]** 复选框。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
