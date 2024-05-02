---
title: 'ACSD-48234：目录搜索结果在以下情况下类别项计数不正确： [!UICONTROL Display Out of Stock Products] 已启用'
description: 应用ACSD-48234修补程序以修复Adobe Commerce问题：当 [!UICONTROL Display Out of Stock Products] 选项。
exl-id: 8e70fe73-d550-4e11-b25e-84955e136d12
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-48234：目录搜索结果显示错误的类别项目计数 **[!UICONTROL Display Out of Stock Products]** 已启用

ACSD-48234修补程序解决了以下问题：当 **[!UICONTROL Display Out of Stock Products]** 选项。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.25。 修补程序ID为ACSD-48234。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。


## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

目录搜索结果在以下情况下显示不正确的类别项计数： **[!UICONTROL Display Out of Stock Products]** 选项。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 并打开 **[!UICONTROL color]** 属性。
1. 添加两个选项，例如橙色和绿色。 保存属性。
1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** 并添加 **[!UICONTROL color]** 归因于 **[!UICONTROL Default]** 属性集。
1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** 并设置 **[!UICONTROL Display Out of Stock Products]** 到 _是_.
1. 创建类别“cat1”。
1. 创建两个产品：
   1. 名称：prod1，颜色：橙色，类别：cat1。
   1. 名称：prod2，颜色：绿色，类别：cat1。
1. 打开店面上的cat1类别。
1. 在分层导航中选择橙色。

<u>预期结果</u>：

只显示prod1产品。

<u>实际结果</u>：

此时会显示prod1和prod2产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
