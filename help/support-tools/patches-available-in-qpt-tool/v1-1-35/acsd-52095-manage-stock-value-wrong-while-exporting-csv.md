---
title: 'ACSD-52095：导出CSV时管理股票值错误'
description: 应用ACSD-52095修补程序以修复导出CSV时Adobe Commerce产品管理库存值错误的问题。
feature: Inventory, Products
role: Admin, Developer
exl-id: 9e599931-e9b1-4216-b78d-3993d9c3132d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-52095： [!UICONTROL Manage Stock] 导出CSV时值错误

ACSD-52095修补程序修复了产品的问题 `manage_stock` 导出CSV时值错误。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.35。 修补程序ID为ACSD-52095。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此 `manage_stock` 产品导出后，CSV文件中的值未正确设置为0。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** 并设置 **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. 创建新产品并保存它。
1. 转到 **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. 选择 *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* 并导出产品。
1. 检查生成的CSV文件： `manage_stock` = 0， `use_config_manage_stock` = 1.
1. 再次转到 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]**，并设置  **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. 转到 **系统** > **导出**.
选择 *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. 检查生成的CSV文件： `manage_stock` = 0， `use_config_manage_stock` = 1.
1. 在管理员中打开产品，转到 **[!UICONTROL Advanced Inventory]** 并查看 **[!UICONTROL Manage Stock]** 值。

<u>预期结果</u>

此 **[!UICONTROL Manage Stock]** 值为 *1* 为产品启用时。

<u>实际结果</u>

此 **[!UICONTROL Manage Stock]** 值为 *0* 为产品启用时。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
