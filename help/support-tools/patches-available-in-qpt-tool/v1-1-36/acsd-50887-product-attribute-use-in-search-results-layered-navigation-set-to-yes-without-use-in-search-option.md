---
title: 'ACSD-50887： *[!UICONTROL Use in Search Results Layered Navigation]*设置为Yes，不使用*[!UICONTROL Use in Search]*选项'
description: 应用ACSD-50887修补程序以修复产品属性属性为*的Adobe Commerce问题[!UICONTROL Use in Search Results Layered Navigation]*可以设置为*是*，而不使用*[!UICONTROL Use in Search]*选项也设置为*是*。
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
exl-id: b597709b-7489-41a0-b1ff-d68d0def0b46
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-50887： *[!UICONTROL Use in Search Results Layered Navigation]* 设置为 *是* 不使用 *[!UICONTROL Use in Search]* option

ACSD-50887修补程序修复了产品属性属性存在的问题 *[!UICONTROL Use in Search Results Layered Navigation]* 可以设置为 *是* 不使用 *[!UICONTROL Use in Search]* 选项也设置为 *是*. 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.36。 修补程序ID为ACSD-50887。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品属性属性 *[!UICONTROL Use in Search Results Layered Navigation]* 可以设置为 *是* 不使用 *[!UICONTROL Use in Search]* 选项也设置为 *是*.

这些设置旨在一起使用。 应用修补程序后，当 *[!UICONTROL Use in Search]* 选项设置为 *否*， *[!UICONTROL Use in Search Results Layered Navigation]* 选项已隐藏，可像也设置为一样工作 *否*.

<u>重现问题的步骤</u>：

1. 在管理员中，导航到 **[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]** 和创建具有多选类型的属性，并设置以下内容：

   * *[!UICONTROL Use in Search]=否*
   * *[!UICONTROL Use in Layered Navigation]=（任何选项）*
   * *[!UICONTROL Use in Search Results Layered Navigation]=是*
   * *名称=测试属性*
   * *选项*：
      * *贴纸*
      * *选取器*

1. 将新属性添加到默认属性集。
1. 创建两个产品：

   1. 第一个产品：
      * 名称=贴纸
      * 将价格、数量、重量设置为1
      * Test_attribute =选择选项 *贴纸*

   1. 第二个产品：
      * 名称=选取器
      * 将价格、数量、重量设置为1
      * Test_attribute =同时选择两个选项

1. 运行 `catalogsearch_fulltext` 重新索引：

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. 按词搜索 *贴纸* 在店面。

<u>预期结果</u>：

仅产品 *贴纸* 返回，因为 [!DNL Elasticsearch] 在以下情况下不会索引Test_attribute： *[!UICONTROL Use in Search]* 已设置为 *否*.

<u>实际结果</u>：

这两种产品都会被退回。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
