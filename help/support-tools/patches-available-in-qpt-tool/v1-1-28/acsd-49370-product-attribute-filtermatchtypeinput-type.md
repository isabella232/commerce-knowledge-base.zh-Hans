---
title: “ACSD-49370：产品属性在GraphQL架构中具有‘FilterMatchTypeInput’类型”
description: 应用ACSD-49370修补程序以修复Adobe CommerceGraphQL架构中产品属性具有“FilterMatchTypeInput”类型的问题。
exl-id: 132eee3a-30b0-4810-b2f0-0d05d0a9f009
feature: Admin Workspace, Attributes, GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-49370：产品属性具有 `FilterMatchTypeInput` 在GraphQL架构中键入

ACSD-49370修补程序修复了产品属性具有 `FilterMatchTypeInput` 键入GraphQL架构。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.28。 修补程序ID为ACSD-49370。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品属性具有 `FilterMatchTypeInput` 键入GraphQL架构。

<u>重现问题的步骤</u>：

1. 创建 *日期和时间* 产品属性。

   * [!UICONTROL Type]： [!UICONTROL DateTime]
   * [!UICONTROL Default Label]： [!UICONTROL Date Time]
   * [!UICONTROL Use in Search]： [!UICONTROL Yes]
   * [!UICONTROL Visible in Advanced Search]： [!UICONTROL Yes]

1. 查询 *GQL API* 文档 `ProductAttributeFilterInput` 类型定义。
1. 观察已创建属性的输入类型。

<u>预期结果</u>：

此 *日期时间* 属性显示过滤器输入类型 `FilterRangeTypeInput`.

<u>实际结果</u>：

此 *日期时间* 属性显示过滤器输入类型 `FilterMatchInputType`.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
