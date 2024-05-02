---
title: 'ACSD-49129：产品媒体API响应中未返回“Content”属性'
description: 应用ACSD-49129修补程序以修复Adobe Commerce问题，该问题导致“rest/V1/products/sku/media”产品媒体API响应中未返回*content*属性（*base64图像代码*）。
exl-id: b7022046-3f52-4880-81b8-977ed270773f
feature: REST, Attributes, Media, Page Content, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-49129：产品媒体API响应中未返回“Content”属性

ACSD-49129修补程序修复了 *内容* 属性(*[!UICONTROL base64 image code]*)不会返回到 `rest/V1/products/sku/media` 产品媒体API响应。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.30。 修补程序ID为ACSD-49129。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此 *内容* 属性(*[!UICONTROL base64 image code]*)不会返回到 `rest/V1/products/sku/media` 产品媒体API响应。

<u>重现问题的步骤</u>：

1. 创建带图像的产品。
1. 发送 *GETREST API* 请求给 `rest/V1/products/<sku>/media` 和 `rest/V1/products/<sku>/media/<entryId>`.
1. 检查API响应。

<u>预期结果</u>

此 *内容* 属性与数据，可通过REST API使用。

<u>实际结果</u>

此 *内容* API响应中不存在属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
