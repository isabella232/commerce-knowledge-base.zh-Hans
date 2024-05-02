---
title: 'ACSD-51574：用其他图像替换时，图像未在前端更新'
description: 应用ACSD-51574补丁以修复Adobe Commerce问题，该问题导致在将图像替换为其他图像后，图像前端未更新。
feature: Configuration
role: Admin
exl-id: a6f26126-71c3-43c2-bba4-60a914d7ec11
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-51574：用其他图像替换时，图像未在前端更新

ACSD-51574修补程序修复了将图像替换为其他图像后，未在前端更新图像的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.37。 修补程序ID为ACSD-51574。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.7

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将图像替换为其他图像后，不会在前端更新图像。

<u>重现问题的步骤</u>：

1. 创建带有几个图像的产品。
1. 编辑产品并上传具有已知名称的图像(例如： *image.jpg*)。
1. 保存产品。
1. 再次编辑产品并删除图像的旧版本，然后上传具有相同名称的新版本图像。 **确保新版本明显不同，这样才能解决问题。**
1. 保存产品。 管理员和前端都会显示图像。
1. 再次编辑产品并重新上传相同的新图像（使用相同名称）。
1. 保存产品并在前端查看产品页面。

<u>预期结果</u>：

第二次上传的图像应该是新图像，以及重命名的图像名称。

<u>实际结果</u>：

第二次上传的图像是之前已删除的旧版图像，而不是相同的新图像。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
