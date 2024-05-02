---
title: 'ACSD-47444： _[!UICONTROL Trying to access array offset on value of type bool]_访问PHP 7.4上已知产品的某些不存在类别路径时出错'
description: 应用ACSD-47444修补程序以修复存在_的Adobe Commerce问题[!UICONTROL Trying to access array offset on value of type bool]_在PHP 7.4上访问已知产品的某些不存在类别路径时出错。
exl-id: dfe803d0-bcff-40e6-a759-8c2243235ea8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-47444： _[!UICONTROL Trying to access array offset on value of type bool]_访问PHP 7.4上已知产品的某些不存在类别路径时出错

ACSD-47444修补程序可解决您所看到的问题 _[!UICONTROL Trying to access array offset on value of type bool]_访问PHP 7.4中已知产品的某些不存在类别路径时出错。此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.22。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

您遇到以下错误： _[!UICONTROL Trying to access array offset on value of type bool]_在访问已知产品的某些不存在的类别路径时，请参见PHP 7.4。

<u>先决条件</u>：

PHP 7.4。

<u>重现问题的步骤</u>：

1. 创建名为“test”的新产品。
1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** >设置 **[!UICONTROL Generate "category/product" URL Rewrites]** = _否_.
1. 转到店面并访问URL，如../abc/test.html（“abc” — 不应存在）。

<u>预期结果</u>：

404页。

<u>实际结果</u>：

500错误：

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
