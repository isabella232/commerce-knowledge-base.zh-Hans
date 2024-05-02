---
title: 'ACSD-53204： *无法保存产品*向图库添加图像的并发请求出错'
description: 应用ACSD-53204修补程序以修复以下Adobe Commerce问题：*无法保存产品*在使用rest/V1/products/&lt；sku&gt；/media端点向产品库添加图像的并发请求时，会引发错误。
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: dcea2621-66cf-49d1-bba6-b61c70716e84
source-git-commit: e1ab32a4540ea7483f7f2b8464ef3e4b0ecbbac7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53204： &quot;*无法保存产品*&#x200B;向图库添加图像的并发请求出现“错误

ACSD-53204修补程序修复了以下问题：*无法保存产品*&#x200B;使用向产品库添加图像的并发请求时引发“错误 `rest/V1/products/<sku>/media` 端点。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.39。 修补程序ID为ACSD-53204。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

&quot;*无法保存产品*&#x200B;使用向产品库添加图像的并发请求时引发“错误 `rest/V1/products/<sku>/media` 端点。

<u>重现问题的步骤</u>：

1. 登录到“管理面板”。
1. 使用SKU p1创建产品。
1. 向发出多个并发请求 `rest/V1/products/<sku>/media` 端点可同时上传多个图像。

<u>预期结果</u>：

保存图像时不会出错。

<u>实际结果</u>：

&quot;*无法保存产品*“错误会不时返回。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
