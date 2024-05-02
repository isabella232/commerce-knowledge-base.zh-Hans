---
title: 'ACSD-52606：用户单击“通知订单已准备好取货”时显示的错误消息'
description: 应用ACSD-52606修补程序以修复当用户单击**时显示错误消息的Adobe Commerce问题[!UICONTROL Notify Order is Ready for Pickup]**。
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606：用户单击“Notify Order is Ready for Pickup”（通知订单准备好提货）时显示的错误消息

ACSD-52606修补程序修复了错误消息的问题 *您的订单未准备好取货* 在用户单击时显示 **[!UICONTROL Notify Order is Ready for Pickup]**. 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.37。 修补程序ID为ACSD-52606。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误消息 *您的订单未准备好取货* 在用户单击时显示在屏幕上 **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>先决条件</u>：

清单模块已安装。

<u>重现问题的步骤</u>：

1. 安装新实例。
1. 创建新的源和库存。
1. 将新源分配给默认网站。
1. 为新创建的源启用取车地点。
1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** 并启用 **[!UICONTROL In-Store Delivery]**.
1. 创建 *有货* 简单的产品，带有 *数量=0* 所有库存和 *[!UICONTROL Manage Stock = No]* 并将其分配给两个源。
1. 使用上一步中创建的产品从前端创建订单，然后选择 *[!UICONTROL In-Store Pickup]* 作为投放方法。
1. 在Admin中，转到 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. 单击 **[!UICONTROL Notify order is ready for pickup]**.

<u>预期结果</u>：

您会收到无错误的通知。

<u>实际结果</u>：

您会收到以下错误消息： *您的订单未准备好取货*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
