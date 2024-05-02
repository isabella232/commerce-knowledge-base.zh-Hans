---
title: 'ACSD-51497：无法按“下拉列表”类型的自定义属性对目录页面排序'
description: 应用ACSD-51497修补程序以修复客户无法按下拉类型的自定义属性对目录页面进行排序的Adobe Commerce问题。
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: 60a4f375-9b9a-4026-9dc7-d9f847a75656
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-51497：无法按类型的自定义属性对目录页进行排序 *下拉列表*

ACSD-51497修补程序修复了客户无法按类型的自定义属性对目录页面进行排序的问题 *下拉列表*. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.33。 修补程序ID为ACSD-51497。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户无法按该类型的自定义属性对目录页进行排序 *下拉列表*.

<u>重现问题的步骤</u>

1. 创建大约六个简单产品并将它们分配给单个类别。
1. 创建产品属性，以将其添加为列表页面上的排序选项。

   * 转到 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**.
   * 在 **[!UICONTROL Properties]** 选项卡，设置以下内容：

      * *[!UICONTROL Default Label]* = *测试*
      * *[!UICONTROL Catalog Input Type]* 对于商店所有者= *下拉列表*
      * *[!UICONTROL Options]*：

         * *第一*
         * *秒*
         * *第三*
         * *第四*

   * 在 **[!UICONTROL Storefront Properties]** 选项卡，设置以下内容：

      * *[!UICONTROL Used for sorting in product listing]* = *是*
      * 将所有其他选项保留为 *默认*.

1. 分配 *测试* 归因于 *默认* 属性集于 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. 将产品配置为 *测试* 属性值。

   * SKU： s00001，测试：第四
   * SKU： s00002，测试：第三
   * SKU： s00003，测试：秒
   * SKU：s00004，测试：第一个
   * SKU： s00005，测试：第四
   * SKU： s00006，测试：第三

1. 重新索引并清除缓存。
1. 转到店面上的类别。
1. 排序方式 *测试* 属性。

<u>预期结果</u>：

产品按 *测试* 属性。

<u>实际结果</u>：

产品不按 *测试* 属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
