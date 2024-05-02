---
title: 'ACSD-48587：产品小部件不适用于包含HTML字符的SKU'
description: 应用ACSD-48587补丁以修复Adobe Commerce问题，该问题导致在产品构件匹配规则中HTML特殊字符无法显示匹配产品。
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587：产品小部件不适用于包含HTML字符的SKU

ACSD-48587修补程序修复了以下问题：在产品构件匹配规则中HTML特殊字符会阻止它们显示匹配产品。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.26。 修补程序ID为ACSD-48587。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品小组件无法使用包含的SKU *“&amp;”* 符号。

<u>重现问题的步骤</u>：

1. 创建包含以下内容的产品 *“&amp;”* （例如，s000&amp;01）。
1. 在上编辑CMS页面的内容 *页面生成器*.
1. 添加产品小组件。
1. 编辑构件并设置 **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. 输入包含的SKU *“&amp;”* 在产品SKU字段中。
1. 保存内容和CMS页面。
1. 查看 *CMS页面* 的内容 *Page Builder预览* 和产品店面。

<u>预期结果</u>：

使用的产品 *“&amp;”* SKU中的页面会显示在页面生成器的预览和店面中。

<u>实际结果</u>：

使用的产品 *“&amp;”* SKU中的页面不会显示在页面生成器预览中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
