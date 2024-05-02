---
title: '''ACSD-54989：公司管理员无法在以下情况下订购 [!UICONTROL Enable Purchase Orders] 设置为“是”并且 [!UICONTROL Purchase Order] 设置为否'
description: 应用ACSD-54989补丁以修复以下情况下公司管理员无法下单的Adobe Commerce问题 [!UICONTROL Enable Purchase Orders] 设置为“是”并且 [!UICONTROL Purchase Order] 设置为否。
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: c2850409-d310-4681-80ec-af8ba347854c
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54989：在以下情况下，公司管理员无法订购 *[!UICONTROL Enable Purchase Orders]* 设置为 *是* 和 *[!UICONTROL Purchase Order]* 设置为 *否*

ACSD-54989修补程序修复了以下情况下无法下订单的问题 **[!UICONTROL Enable Purchase Orders]** 设置为 *是* 和 **[!UICONTROL Purchase Order]** 设置为 *否*. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.40。 修补程序ID为ACSD-54989。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在以下情况下，公司管理员无法下订单 **[!UICONTROL Enable Purchase Orders]** 设置为 *是* 和 **采购订单** 设置为 *否*.

<u>先决条件</u>：

安装 [!DNL B2B] 模块。

<u>重现问题的步骤</u>：

1. 启用公司并离开 [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *否*.
1. 创建一个价格为100的简单产品。
1. 通过管理员创建新公司。
1. 设置 [!UICONTROL **启用采购订单**] 到 *是*.
1. 以公司管理员身份登录店面。
1. 将创建的简单产品添加到购物车。
1. 进入结账页面并单击 **[!UICONTROL Place Order]** 以完成购买。

<u>预期结果</u>：

您可以成功下订单。

<u>实际结果</u>：

此 **[!UICONTROL My Account]** 页面打开，但未下订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
