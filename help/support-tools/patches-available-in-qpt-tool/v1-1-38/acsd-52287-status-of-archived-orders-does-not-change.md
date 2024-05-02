---
title: 'ACSD-52287：已存档订单的状态不会更改'
description: 应用ACSD-52287修补程序以修复在提交贷项通知单后，网格上存档订单的状态不会从*已完成*更改为*已关闭*的Adobe Commerce问题。
feature: Orders, Checkout
role: Admin, Developer
exl-id: c88c5c87-eec7-4105-9e4e-815d0888a34b
source-git-commit: 178023177975f210ebf7dd07e8c75cfe3ac89ff1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-52287：已存档订单的状态不会更改

ACSD-52287修补程序修复了已存档订单的状态不会更改的问题 *已完成* 到 *已关闭* 在提交贷项通知单之后的GRID上。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.38。 修补程序ID为ACSD-52287。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

已存档订单的状态不会从 *已完成* 到 *已关闭* 在提交贷项通知单之后的GRID上。

<u>重现问题的步骤</u>：

1. 配置 *[!UICONTROL Asynchronous Indexing]*.
   * 在管理员侧边栏上，转到 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * 在左侧面板中，展开 **[!UICONTROL Advanced]** 部分并选择 **[!UICONTROL Developer]** 下方。
   * 展开 **[!UICONTROL Grid Settings]** 部分。
   * 设置 *[!UICONTROL Asynchronous indexing]* 到 *是*.
   * 单击 **[!UICONTROL Save Config]**.
1. 配置 *[!UICONTROL Order Archive]*.
   * 在管理员侧边栏上，转到 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * 在左侧面板中，展开 **[!UICONTROL Sales]** 部分并选择 **[!UICONTROL Sales]** 下方。
   * 展开 **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** 部分。
   * 设置 *[!UICONTROL Enable Archiving]* 到 *是* （其余配置保留为默认设置）。
   * 单击 **[!UICONTROL Save Config]**.
1. 在前端下订单。
1. 运行 [!DNL cron]  以便显示在 *[!UICONTROL Admin Order Grid]*.
1. 开票并发运要更新订单状态的订单 *完成*.
1. 运行 [!DNL cron]  更新 *[!UICONTROL Sales Order Grid]* 具有最新订单状态。
1. 存档订单。
1. 转到 *[!UICONTROL Archived order grid]*.
1. 打开已存档的订单，并通过创建 [!UICONTROL Credit Memo] 以使 [!UICONTROL Order status]： *已关闭*.
1. 运行 [!DNL cron] 好几次。
1. 查看 *[!UICONTROL Archived order grid]* 新订单状态的信息。

<u>预期结果</u>：

顺序显示为 *已关闭*.

<u>实际结果</u>：

顺序显示为 *完成*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
