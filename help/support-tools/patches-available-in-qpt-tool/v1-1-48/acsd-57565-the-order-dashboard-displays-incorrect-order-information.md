---
title: 'ACSD-57565：订单仪表板显示错误的订单信息'
description: 应用ACSD-57565修补程序以修复Adobe Commerce问题，该问题导致订单仪表板在更新时段之前显示错误的订单信息。
feature: Roles/Permissions
role: Admin, Developer
exl-id: 5b292fef-23f6-479f-bf76-adad53d30cf4
source-git-commit: fdf6e6e85f903a26a7b44674937ccf88ee769d06
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57565：订单控制面板显示的订单信息不正确

ACSD-57565修补程序修复了订单功能板在更新时间段之前显示错误订单信息的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.48。 修补程序ID为ACSD-57565。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序

## 问题

订单仪表板显示的订单信息不正确。

<u>重现问题的步骤</u>：

1. 启用 **[!UICONTROL dashboard charts]**.
1. 创建订单并开票。
1. 在创建订单后至少等待24小时。
1. 查看 **[!UICONTROL dashboard chart]** 数据。
1. 记录完整的订单计数。
1. 将时间更改为 *当前月份*，然后将其改回 *今天*.

<u>预期结果</u>：

仪表板图表应始终显示正确的统计信息。

<u>实际结果</u>：

仪表板图表在首次加载时显示不正确的统计信息。 图表的准确统计信息会在时段之后更新。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
