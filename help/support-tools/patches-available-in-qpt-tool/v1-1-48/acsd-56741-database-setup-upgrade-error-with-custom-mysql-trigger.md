---
title: 'ACSD-56741：使用自定义MySQL触发器解决数据库设置错误'
description: 应用ACSD-56741修补程序以修复Adobe Commerce问题，该问题导致在“setup：upgrade”期间出现错误消息*尝试访问null类型的值上的阵列偏移*，这是因为数据库中存在与索引和无关的自定义MySQL触发器。 [!DNL MView].
feature: Install
role: Admin, Developer
source-git-commit: 216ce1035584e4c049029073ee0017d3616cdbd6
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56741：使用自定义MySQL触发器解决数据库设置错误

ACSD-56741修补程序修复了错误消息的问题 *正在尝试访问类型为null的值上的数组偏移* 出现于 `setup:upgrade` 由于数据库中的自定义MySQL触发器与索引和无关， [!DNL MView]. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.48。 修补程序ID为ACSD-56741。 请注意，该问题计划在Adobe Commerce 2.5.0中修复

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误消息 *正在尝试访问类型为null的值上的数组偏移* 出现于 `setup:upgrade` 由于数据库中的自定义MySQL触发器与索引和无关， [!DNL MView].

<u>重现问题的步骤</u>：

1. 运行 `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. 运行 `php bin/magento c:f`.
1. 运行 `php bin/magento setup:upgrade`.

<u>预期结果</u>：

安装程序升级完成，没有出现错误。

<u>实际结果</u>：

安装程序升级退出，并出现以下错误消息：

*警告：正在尝试访问类型为null的值上的数组偏移*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
