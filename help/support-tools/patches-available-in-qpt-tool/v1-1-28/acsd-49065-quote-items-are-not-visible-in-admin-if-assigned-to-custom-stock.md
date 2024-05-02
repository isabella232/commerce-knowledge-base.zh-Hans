---
title: 'ACSD-49065：报价项在管理员中不可见'
description: Adobe Commerce应用ACSD-49065修补程序以修复以下问题：如果报价项目仅分配给自定义库存，则无法在管理员中看到这些报价项目。
exl-id: 3a5ceb4c-4c94-4938-98d9-9171f2633056
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-49065：报价单项目在管理员中不可见

ACSD-49065修补程序修复了报价单项目仅分配给自定义库存时无法在管理员中显示的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.28。 修补程序ID为ACSD-49065。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果报价项目仅分配给自定义库存，则无法在管理员中显示。

先决条件：

**[!UICONTROL B2B]** 和 **[!UICONTROL Inventory]** 必须安装模块。

<u>重现问题的步骤</u>：

1. 启用 **[!UICONTROL Company]** 和 **[!UICONTROL B2B Quote]** 下 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. 创建辅助 **[!UICONTROL Inventory Source]** 并将其分配给辅助节点 **[!UICONTROL Inventory Stock]**.
1. 通过仅分配次产品（非默认）创建新产品 **[!UICONTROL Inventory Source]**.
1. 转到店面并创建新公司帐户。 登录身份 **[!UICONTROL Company Admin]**，然后将创建的产品添加到购物车。
1. 导航到购物车并 *[!UICONTROL Request a Quote]*.
1. 转到管理员并在以下位置查看所请求的报价： **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.

<u>预期结果</u>：

项目会显示在使用新产品创建的新报价中，而无需重新保存产品。

<u>实际结果</u>：

此 *[!UICONTROL Items Quoted]* 部分为空。 如果重新保存新创建的产品，则会显示相应的项目。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
