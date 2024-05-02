---
title: 'ACSD-50512：更新可下载产品暂存更新的开始日期时出错'
description: 应用ACSD-51892修补程序以修复Adobe Commerce性能问题，该问题导致以下错误*可下载链接与产品无关。请验证该链接，然后重试*，此错误会在更新可下载产品暂存更新的开始日期时发生。
feature: Products, Staging
role: Admin
exl-id: 873357ef-49c3-48f8-a98e-41c48cb9ba8b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-50512：更新可下载产品暂存更新的开始日期时出错

ACSD-50512修补程序修复了错误的问题 *可下载的链接与产品无关。 请验证链接并重试*，在更新可下载产品暂存更新的开始日期时发生。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.33。 修补程序ID为ACSD-51502。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误 *可下载的链接与产品无关。 请验证链接并重试*，在更新可下载产品暂存更新的开始日期时发生。

<u>重现问题的步骤</u>：

1. 创建可下载的产品，使用 *可下载的链接* 和 *示例链接*.
1. 为同一产品创建计划更新并保存该产品。
1. 编辑预配置的计划更新（步骤2）并更改开始日期。
1. 保存计划的更新。

<u>预期结果</u>：

已成功保存对计划更新所做的更改。

<u>实际结果</u>：

您收到以下错误： *可下载的链接与产品无关。 请验证链接并重试*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
