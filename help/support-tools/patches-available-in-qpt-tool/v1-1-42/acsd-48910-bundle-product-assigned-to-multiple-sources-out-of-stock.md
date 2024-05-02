---
title: 'ACSD-48910：分配了多个来源的捆绑产品在开具发票和发货后缺货'
description: 应用ACSD-48910修补程序以修复Adobe Commerce问题：在开票和发运订单后，分配给多个来源的捆绑产品会缺货，即使该订单仍然具有非零数量。
feature: Products, Inventory
role: Admin, Developer
exl-id: 6ac3dedf-1c28-4874-b963-44a429b37983
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-48910：分配了多个来源的捆绑产品在开具发票和发运后缺货

ACSD-48910修补程序修复了在为订单开票和发运订单后，即使订单仍然具有非零数量，分配给多个来源的捆绑产品也会缺货的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.42。 修补程序ID为ACSD-48910。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

分配给多个来源的捆绑产品在开具发票和发运后即使“可用”也会缺货。

<u>重现问题的步骤</u>：

1. 创建两个网站。
1. 创建两个商店/商店视图（每个网站一个）。
1. 创建两个简单的产品（数量= 10），并将它们同时分配给股票和网站。
1. 创建捆绑产品，并将这些简单的产品添加到其中。 将捆绑产品分配给两个网站。
1. 转到店面并将捆绑产品添加到购物车。
1. 结帐下单。
1. 从管理员处开具发票并发送订单。

<u>预期结果</u>：

捆绑产品有库存，因为我们只购买了10件商品中的1件。

<u>实际结果</u>：

捆绑产品将其状态更改为缺货。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
