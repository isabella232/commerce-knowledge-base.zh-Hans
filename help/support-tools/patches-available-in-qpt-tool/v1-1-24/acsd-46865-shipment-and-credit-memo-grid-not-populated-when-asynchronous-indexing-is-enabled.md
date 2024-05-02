---
title: 'ACSD-46865： [!UICONTROL shipment] 和 [!UICONTROL credit memo] 未填充于 [!UICONTROL asynchronous indexing] 已启用'
description: 应用ACSD-46865修补程序以修复Adobe Commerce问题，其中 [!UICONTROL shipment] 和 [!UICONTROL credit memo] 以下情况下不会填充网格： [!UICONTROL asynchronous indexing] 已启用。
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865： [!UICONTROL shipment] 和 [!UICONTROL credit memo] 未填充于 [!UICONTROL asynchronous indexing] 已启用

ACSD-46865修补程序修复了以下问题 [!UICONTROL shipment] 和 [!UICONTROL credit memo] 以下情况下不会填充网格： [!UICONTROL asynchronous indexing] 已启用。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.24。 修补程序ID为ACSD-46865。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!UICONTROL Shipment] 和 [!UICONTROL credit memo] 以下情况下不会填充网格： [!UICONTROL asynchronous indexing] 已启用。

<u>重现问题的步骤</u>：

1. 在 [!DNL Commerce] 管理员，转到 **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *是*.
2. 再次转到 **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. 清理配置缓存。
4. 为简单产品下新的访客订单。
5. 运行cron。
6. 在中打开订单 [!UICONTROL Commerce] 管理员，转到 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** 并生成发票和贷项通知单。
7. 将订单移至 [!UICONTROL Archive].
8. 为简单产品创建另一个订单。
9. 运行cron。
10. 转至新订单并生成新发运、发票和贷项通知单。
11. 运行cron。
12. 查看 [!UICONTROL shipments]， [!UICONTROL invoices]、和 [!UICONTROL credit memo] 管理中的网格。

<u>预期结果</u>：

新建 [!UICONTROL shipment]， [!UICONTROL invoice] 和 [!UICONTROL credit memo] 将显示。

<u>实际结果</u>：

新建 [!UICONTROL shipment]， [!UICONTROL invoice]、和 [!UICONTROL credit memo] 不会显示。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
