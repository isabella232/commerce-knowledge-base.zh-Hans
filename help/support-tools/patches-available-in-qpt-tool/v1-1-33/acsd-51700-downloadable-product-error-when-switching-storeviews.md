---
title: 'ACSD-51700：在可下载的产品编辑页面上切换商店视图时出错'
description: 应用ACSD-51700补丁以修复在管理员的可下载产品编辑页面上切换商店视图时出现错误的Adobe Commerce问题。
feature: Products
role: Admin
exl-id: 652876a5-275d-437f-9cb3-baf4e7b23aae
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51700：在可下载的产品编辑页面上切换商店视图时出错

ACSD-51700修补程序修复了在管理员的可下载产品编辑页面上切换存储视图时出现错误的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.33。 修补程序ID为ACSD-51700。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p1

## 问题

在管理员的可下载产品编辑页面上切换商店视图时出现错误。

<u>重现问题的步骤</u>：

1. 创建名称为的可下载产品， [!DNL SKU]、和价格。 不要添加任何链接，并保存产品。
1. 从所有存储视图切换到默认存储视图。
1. 为可下载产品创建链接并保存。
1. 从默认存储视图切换到所有存储视图。

<u>预期结果</u>：

链接的产品可见。

<u>实际结果</u>：

将显示以下错误：

*已弃用的功能： number_format()：将null传递给float类型的参数#1 ($num)在vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php的第228行中已弃用*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
