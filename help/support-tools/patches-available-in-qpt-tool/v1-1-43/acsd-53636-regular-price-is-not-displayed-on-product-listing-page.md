---
title: 'ACSD-53636：不显示正常价格 [!UICONTROL Product Listing] page'
description: 应用ACSD-53636补丁以修复未在上显示正常价格的Adobe Commerce问题*[!UICONTROL Product Listing]*包含具有特价子产品的可配置产品的页面。
feature: Catalog Management, Products
role: Admin, Developer
exl-id: 97b4eb64-92d1-4db1-8e5b-915b16115663
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-53636：正常价格不显示在 *[!UICONTROL Product Listing]* 页面

ACSD-53636修补程序修复了常规价格未显示在 *[!UICONTROL Product Listing]* 包含具有特价子产品的可配置产品的页面。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.43。 修补程序ID为ACSD-53636。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

正常价格不显示在 *[!UICONTROL Product Listing]* 包含具有特价子产品的可配置产品的页面。

<u>重现问题的步骤</u>：

1. 登录到管理员并转到 **[!UICONTROL Admin]** > **[!UICONTROL Catalog]**，并创建或打开任何可配置的产品。
2. 打开子产品，并为所有或其中一个子产品添加特殊价格并保存该产品。
3. 前往前端并打开 **[!UICONTROL Product Detail]** 页面；在具有特殊价格的子产品的色板上，您将看到 *[!UICONTROL Regular price]* 删除了（预期）。
4. 前往前端并打开 **[!UICONTROL Product Listing]** ，查看带有特殊价格的可配置产品的页面；要了解的是，可配置产品色板更改不会显示常规价格，这与 *[!UICONTROL Product Detail Page]* 和其他简单产品。

<u>预期结果</u>：

在 *[!UICONTROL Product Listing]* 页面上，可配置产品显示其子产品的常规价格。

<u>实际结果</u>：

在 *[!UICONTROL Product Listing]* 页面时，可配置产品不显示其子产品的常规价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
