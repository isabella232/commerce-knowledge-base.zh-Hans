---
title: 'ACSD-53176：具有“为之一”条件的产品规则不匹配'
description: 应用ACSD-53176修补程序以修复Adobe Commerce问题，该问题导致相关的产品规则“是”条件无法正常用于“要匹配的产品”。
feature: Marketing Tools
role: Admin
exl-id: 91f05f5b-6a5e-4b93-9dfb-88cbeccb6c9e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-53176：使用的产品规则 `is one of` 条件不匹配

ACSD-53176修补程序修复了相关产品规则的问题 `is one of` 条件无法正常工作的对象 **要匹配的产品**. 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.36。 修补程序ID为ACSD-53176。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

相关产品规则 `is one of` 条件无法正常工作的对象 **要匹配的产品**.

<u>重现问题的步骤</u>：

1. 创建3-4个产品。
1. 创建新的相关产品规则。

   设置规则以匹配两个或更多产品：
   * `SKU is one of "S1,S2".`

   设置规则以显示两个或多个项目：
   * `Product SKU is one of constant value "S2,S3".`

1. 打开店面上的S1产品。

<u>预期结果</u>：

相关产品“S2”和“S3”会同时显示在产品页面“S1”和“S2”上。

<u>实际结果</u>：

相关产品不会显示在产品页面上。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
