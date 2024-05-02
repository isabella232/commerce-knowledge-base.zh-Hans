---
title: 'ACSD-53347：价格指数表现逐渐变差'
description: 应用ACSD-53347修补程序以修复重新索引大型产品目录的价格时性能逐渐降低的Adobe Commerce问题。
feature: Price Indexer
role: Admin
exl-id: 28795673-54b0-4282-bd43-344401cbe140
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-53347：价格索引性能逐渐降低

ACSD-53347修补程序修复了在重新索引大型产品目录的价格时性能逐渐降低的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.38。 修补程序ID为ACSD-53347。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当重新索引大型产品目录的价格时，在索引过程中执行的查询的性能逐渐降低。

<u>重现问题的步骤</u>：

1. 创建一个大型简单目录并向这些产品分配自定义选项（自定义选项在索引期间使用临时表）。
1. 创建至少200个或更多客户组以提高问题的可见性。
1. 创建十个或更多网站，并将所有产品分配给每个网站。
1. 请注意，导入的产品几乎完全相同，只是SKU和名称不同。
1. 启用 **[!UICONTROL DB Logging]**.
1. 执行 `bin/magento index:reindex catalog_product_price` 命令。
1. 检查 *DELETE来源`catalog_product_index_price_opt_agr_temp`* 在 `db.log`.

<u>预期结果</u>：

执行 *数据库查询* 运行高效。

<u>实际结果</u>：

性能 *数据库查询* 在临时表上逐渐变慢，因此完成价格索引表需要花费大量时间。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
