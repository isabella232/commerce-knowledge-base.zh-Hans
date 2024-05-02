---
title: “ACSD-55427：管理员无法取消分配产**[!UICONTROL Product in Shared Catalogs]**在产品页面上”
description: 应用ACSD-55427修补程序以修复无法从**中取消分配产品的Adobe Commerce问题[!UICONTROL Product in Shared Catalogs]**。
feature: Products, B2B
role: Admin, Developer
exl-id: 1e08def1-07f6-42e0-b600-9f0bfdd6477a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427：管理员无法从取消分配产品 **[!UICONTROL Product in Shared Catalogs]** 在产品页面上

ACSD-55427修补程序修复了无法从取消分配产品的问题 **[!UICONTROL Product in Shared Catalogs]** 位于Commerce管理员目录中的产品页面。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.44。 修补程序ID为ACSD-55427。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

不能从取消分配产品 **[!UICONTROL Product in Shared Catalogs]** 位于Commerce管理员目录中的产品页面。

<u>重现问题的步骤</u>：

先决条件：同时安装了Adobe Commerce和B2B **[!UICONTROL Shared Catalogs]** 已启用。
1. 创建产品。
1. 导航到共享目录仪表板，然后打开默认的共享目录。
1. 将产品分配给默认目录，并设置低于产品价格的价格。
1. 保存共享目录。
1. 运行 [!UICONTROL CRON] 更新使用者/索引器。
1. 打开产品，然后从下的移除产品 **[!UICONTROL Product in Shared Catalogs]** 部分。

<u>预期结果</u>：

应该从下的移除产品 **[!UICONTROL Product in Shared Catalogs]** 部分。

<u>实际结果</u>：

产品仍显示在 **[!UICONTROL Product in Shared Catalogs]** 部分。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
