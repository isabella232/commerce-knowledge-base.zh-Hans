---
title: '''ACSD-56415：性能 [!UICONTROL Partial Price Indexing] 由于“DELETE”查询而减慢'
description: 应用ACSD-56415修补程序以修复Adobe Commerce问题，该问题导致 [!UICONTROL Partial Price Indexing] 当数据库有大量要索引的部分价格数据时，由于“DELETE”查询而减慢。
feature: Catalog Service
role: Admin, Developer
exl-id: 0b099570-9f27-4ae2-9384-6b69ea50bd98
source-git-commit: fe6269ac042326a85a2cab5ccf834ac3eff1c166
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-56415：性能 [!UICONTROL Partial Price Indexing] 由于以下原因而减慢 `DELETE` 查询

ACSD-56415修补程序修复了 [!UICONTROL Partial Price Indexing] 速度减慢，原因是 `DELETE` 查询时数据库中有大量的局部价格数据索引。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.45。 修补程序ID为ACSD-56023。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

性能 [!UICONTROL Partial Price Indexing] 速度减慢，原因是 `DELETE` 查询时数据库中有大量的局部价格数据索引。

<u>重现问题的步骤</u>：

1. 创建 *300000产品* 和 *10个网站* 使用大型性能配置文件。
1. 登录到“管理面板”。
1. 创建 *10个客户组*.
1. 执行以下查询以将产品添加到 `_cl` 表：

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. 执行以下命令以触发部分价格索引过程：

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>预期结果</u>：

SQL查询DELETE `main_table` 发件人 `catalog_product_index_price` 会快速执行。

<u>实际结果</u>：

SQL查询DELETE `main_table` 发件人 `catalog_product_index_price` 执行速度非常慢。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
