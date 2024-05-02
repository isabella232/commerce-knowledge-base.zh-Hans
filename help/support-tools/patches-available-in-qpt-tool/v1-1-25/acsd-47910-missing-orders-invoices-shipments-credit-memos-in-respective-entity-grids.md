---
title: 'ACSD-47910：各个实体网格中缺少订单、发票、装运和贷项通知单'
description: 应用ACSD-47910补丁程序，以修复相应实体网格中缺少订单、发票、装运和贷项通知单的Adobe Commerce问题。
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910：各个实体网格中缺少订单、发票、装运和贷项通知单

ACSD-47910修补程序修复了各实体网格中缺少订单、发票、装运和贷项通知单的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.25。 修补程序ID为ACSD-47910。 将修复此问题的版本尚不可用。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在各自的实体网格中缺少订单、发票、装运和贷项通知单。

<u>重现问题的步骤</u>：

1. 启用 **[!UICONTROL Asynchronous indexing]** 在 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. 下两份订单。
1. 运行cron将这些订单同步到网格。
1. 打开其中一个订单，使其准备开票。 不要提交发票。
1. 做好新订单的准备工作，准备在前端投放。 不要单击“下单”按钮。
1. 添加 `sleep(30)` 在 `foreach` 在 `NotSyncedDataProvider::L43`.
1. 运行 `bin/magento cron:run`.
1. 现在下新订单。
1. 为上一订单开票。
1. 再次运行cron，期待同步新订单。
1. 转到管理员中的订单网格。

<u>预期结果</u>：

新订单应显示在订单网格上。

<u>实际结果</u>：

上一个订单更新已同步到网格(**[!UICONTROL status: Processing]**)。 新订单永远不会出现在网格上。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
