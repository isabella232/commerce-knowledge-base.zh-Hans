---
title: '''ACSD-53925：无法保存CMS块 [!UICONTROL Product Carousel]’'
description: Adobe Commerce应用ACSD-53925修补程序以修复以下问题：将“catalog_product_price”的维度模式设置为website时，管理员无法通过产品轮播保存CMS块。
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: 6ef6d8ff-4ebb-4adb-9fb7-0d4a81a25f50
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-53925：无法保存CMS块 *[!UICONTROL Product Carousel]*

ACSD-53925修补程序修复了管理员无法保存的CMS块的问题 *[!UICONTROL Product Carousel]* 当维模式用于 `catalog_product_price` 设置为网站。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.43。 修补程序ID为ACSD-53925。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员无法保存包含的CMS块 *[!UICONTROL Product Carousel]* 当维模式用于 `catalog_product_price` 设置为网站。

<u>重现问题的步骤</u>：

1. 创建两个简单的产品：
   * 简单1 - $10
   * 简单2 - 20美元
1. 创建捆绑产品&#39;*bundle1-dyn*”提供了两个基于简单产品SKU的选项。
1. 为产品价格索引器设置维度模式：

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. 转到 **[!UICONTROL Content]** > **[!UICONTROL Blocks]**，并创建新的CMS块。
1. 编辑内容，使用 [!DNL Page Builder]：
   * 添加 *[!UICONTROL Row]* 元素
   * 添加 *[!UICONTROL Products]* 元素
   * 选择 *[!UICONTROL Product Carousel]*
   * 输入产品SKU - *bundle1-dyn*
1. 保存CMS块。

<u>预期结果</u>：

用户能够添加产品轮播且没有错误。

<u>实际结果</u>：

* UI中会引发一条消息： *很抱歉，生成此内容时出错*
* `var/log/exception.log` 包含以下错误：

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
