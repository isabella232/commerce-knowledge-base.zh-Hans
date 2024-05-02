---
title: '''ACSD-51857：''aggregate_sales_report_bestsellers_data''的慢cron作业影响性能'''
description: 应用ACSD-51857修补程序以修复Adobe Commerce问题，该问题导致慢速cron作业“aggregate_sales_report_bestsellers_data”影响大型“sales_order”和“sales_order_item”数据库表。
exl-id: 444ab283-c98b-46b3-a492-706f0ce34a27
source-git-commit: a33364531d2efd572cd1b1847dd45e0f427af03b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51857：的CRON作业缓慢 `aggregate_sales_report_bestsellers_data` 影响性能

ACSD-51857修补程序修复了cron作业速度缓慢的问题 `aggregate_sales_report_bestsellers_data` 影响大 `sales_order` 和 `sales_order_item` 数据库表。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.34。 修补程序ID为ACSD-51857。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Cron作业性能 `aggregate_sales_report_bestsellers_data` 慢于 `sales_order` 和 `sales_order_item` 数据库表。

要解决此问题，为报表获取数据的主要数据查询已重写为更高效的表单。 现在，它使用子查询来确定数据子集。

为了使子查询尽快运行，为添加了新索引 `sales_order` 数据库表： `SALES_ORDER_STORE_STATE_CREATED` 基于 `store_id`， `state`、和 `created_at` 列。

<u>先决条件</u>

确保每天有大量订单。

<u>重现问题的步骤</u>

1. 执行 `aggregate_sales_report_bestsellers_data` cron作业。
1. 检查要在管理员功能板中显示的数据，在 **[!UICONTROL Bestsellers]** 选项卡。

<u>预期结果</u>：

*[!UICONTROL Quantity per source]* 在 **[!UICONTROL Configuration]** 选项卡不应为空。

<u>实际结果</u>：

*[!UICONTROL Quantity per source]* 在 **[!UICONTROL Configuration]** 选项卡为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
