---
title: 'ACSD-56621：更新后的名称未显示在公司管理员用户的问候语标题中'
description: 应用ACSD-56621修补程序以修复Adobe Commerce问题，该问题导致更新的公司管理员用户的名字和姓氏未反映在问候语标头部分。
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 4ad9c878-b617-4e6a-939c-be15faf7124b
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621：更新后的名称未显示在公司管理员用户的问候语标头中

ACSD-56621修补程序修复了公司管理员用户的更新后名字和姓氏未反映在问候语标头部分的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.46。 修补程序ID为ACSD-56621。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

更新的名称不会显示在公司管理员用户的问候语标题中。

<u>重现问题的步骤</u>：

1. 导航至 **[!UICONTROL Admin]** 面板。
1. 转到 **[!UICONTROL Stores]** 并选择 **[!UICONTROL Configuration]**.
1. 在 **[!UICONTROL General]** 部分，选择 **[!UICONTROL B2B]** 以启用B2B公司功能。
1. 转到 **[!UICONTROL Storefront]** 注册一家新公司。
1. 以公司管理员用户身份登录。
1. 转到 **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** 并根据需要修改名字和姓氏字段。

<u>预期结果</u>：

问候语标头部分中用户的名字和姓氏会立即更改。

<u>实际结果</u>：

仅当用户注销并再次登录时，才会更改用户的名字和姓氏。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
