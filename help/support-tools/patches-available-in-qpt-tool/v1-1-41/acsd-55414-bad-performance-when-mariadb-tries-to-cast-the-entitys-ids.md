---
title: 'ACSD-55414：MariaDB尝试转换entitys_ids时性能不佳'
description: 应用ACSD-55414修补程序以修复Adobe Commerce问题。当MariaDB尝试将“entitys_ids”从字符串转换为整数时，它会妨碍重新索引的性能。
feature: Attributes
role: Admin, Developer
exl-id: 008a4fda-5d80-47e2-8fb4-c1e39d15a6ba
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-55414：当MariaDB尝试转换 `entitys_ids`

ACSD-55414修补程序修复了当MariaDB尝试转换时，重新索引的性能受到阻碍的问题 `entitys_ids` 从字符串到整数。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.41。 修补程序ID为ACSD-55414。 请注意，Adobe Commerce 2.4.6中已修复该问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当MariaDB尝试强制转换 `entitys_ids` 从字符串到整数。

<u>重现问题的步骤</u>：

1. 更新 `setup/performance-toolkit/profiles/ce/small.xml` 通过设置 *50000* 简单产品。
1. 通过执行以下命令生成此配置文件： `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. 运行重新索引： `bin/magento indexer:reindex catalog_product_attribute`.

<u>预期结果</u>：

重新索引需要合理的时间才能完成。

<u>实际结果</u>：

重新索引需要花费太多时间才能完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
