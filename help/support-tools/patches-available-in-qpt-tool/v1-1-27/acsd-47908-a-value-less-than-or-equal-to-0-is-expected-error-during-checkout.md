---
title: 'ACSD-47908： *应为小于或等于0的值*结账时出现错误'
description: 应用ACSD-47908修补程序以修复Adobe Commerce错误*在结帐期间在运输步骤中选择源和数量时，应提供一个小于或等于0的值*。
exl-id: fec90e4b-9cb8-4cd9-9e85-ccada840c896
feature: Admin Workspace, Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-47908： *应为小于或等于0的值* 结账时出错

ACSD-47908修补程序修复了错误 *应为小于或等于0的值* 在结帐期间在装运步骤中选择来源和数量时。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.27。 修补程序ID为ACSD-47908。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在结帐期间选择装运步骤中的来源和数量时，会引发以下错误： *应为小于或等于0的值*.

<u>先决条件</u>：

安装Adobe Commerce Inventory management (MSI)模块。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** 并配置多个源。
1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** 并创建新库存。
   * 现在将源分配给新库存。
1. 转到 **[!UICONTROL Catalog]** > **[!UICONTROL Products]** 并编辑至少一个产品。
   * 确保将产品分配给新来源，并指定可用数量。
1. 转到 **[!UICONTROL Sales]** > **[!UICONTROL Orders]** 并创建新订单。
1. 将这些产品添加到订单中并下单。
1. 单击 **[!UICONTROL Ship]**.
1. 选择要从中发运的来源。
1. 指定要发运的每个项目的数量。
1. 重新加载页面。
1. 单击 **[!UICONTROL Proceed to Shipment]**.

<u>预期结果</u>：

此时将打开新的装运页面，并且不会出现任何错误。

<u>实际结果</u>：

* 无法验证输入的数量。
* 引发以下错误： *请输入小于或等于0的值*.

  但是，该错误不一致，并且可能并不总是出现。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
