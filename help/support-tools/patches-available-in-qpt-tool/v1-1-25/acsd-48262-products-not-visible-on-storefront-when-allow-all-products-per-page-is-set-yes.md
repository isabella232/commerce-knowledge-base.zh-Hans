---
title: '''ACSD-48262：产品在店面中不可见，当时 [!UICONTROL Allow All Products Per Page] 已设置 [!UICONTROL Yes]’'
description: Adobe Commerce应用ACSD-48262修补程序以修复以下问题：当 [!UICONTROL Allow All Products Per Page] 设置已设置为 [!UICONTROL Yes].
exl-id: 327cad03-441d-4adb-8a10-802f06d3fcd1
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-48262：以下情况下店面中看不到产品： [!UICONTROL Allow All Products Per Page] 已设置 *[!UICONTROL Yes]*

ACSD-48262修补程序修复了以下问题： [!UICONTROL Allow All Products Per Page] 设置已设置为 *[!UICONTROL Yes]*. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.25。 修补程序ID为ACSD-48262。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）>=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

ACSD-48262修补程序修复了以下问题： [!UICONTROL Allow All Products Per Page] 设置已设置为 *[!UICONTROL Yes]*.

<u>重现问题的步骤</u>：

1. 创建测试类别。
1. 在测试类别中创建测试产品。
1. 浏览产品以测试店面上的类别页面，并确保产品可见。
1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** 并设置 [!UICONTROL Allow All Products Per Page] 将设置为 *[!UICONTROL Yes]*.
1. 清除缓存。
1. 检查店面的类别页面。

<u>预期结果</u>：

产品可见。

<u>实际结果</u>：

产品不可见。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。


## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
