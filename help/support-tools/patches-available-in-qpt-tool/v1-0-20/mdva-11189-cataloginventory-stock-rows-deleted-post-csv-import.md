---
title: 'MDVA-11189：CSV导入后删除了cataloginventory_stock行'
description: 11189于MDVA的Adobe Commerce修补程序修复了在导入.csv文件以更新产品库存后，删除“cataloginventory_stock”表中的行时出现的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20后，即可使用此修补程序。 修补程序ID为MDVA-1189。 请注意，Adobe Commerce 2.3.5中已修复此问题。
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189：CSV导入后删除了cataloginventory_stock行

MDVA-11189 Adobe Commerce修补程序修复了在导入.csv文件以更新产品库存后，来自 `cataloginventory_stock` 表格将被删除。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.20。 修补程序ID为MDVA-1189。 请注意，Adobe Commerce 2.3.5中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.2.3

**与Adobe Commerce版本兼容：** Adobe Commerce（所有部署方法） 2.3.0-2.3.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了导入后的问题 `.csv` 要更新产品库存，请将 `cataloginventory_stock` 表格将被删除。

<u>重现问题的步骤：</u>

1. 在数据库中，运行以下MySQL命令： `select count(*) from cataloginventory_stock_status;`
1. 记下行数。
1. 按如下方式设置crontab： `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. 转到中的“管理”面板 **系统** > **工具** > **索引管理**.
1. 将索引器设置为 *按计划更新。*
1. 转到 **系统** > *数据传输* > **导出**.
1. 设置 **实体类型** 等于 *产品* > **继续**.
1. 打开已保存的 `.csv` 文件>移除除SKU和QTY之外的所有列。
1. 将所有产品的数量更新为150。
1. 保存 `.csv` 文件。
1. 转到 **系统** > *数据传输* > **导入** .
1. 设置以下值：
   1. 实体类型： *产品*
   1. 导入行为： *添加/更新*
   1. 将所有其他值保留为默认值。
   1. 选择“文件”以选择目录产品电子表格。
1. 单击 **检查数据** > **导入**. 等待5-10分钟通过。
1. 在数据库中，运行以下MySQL命令：
   `select count(*) from cataloginventory_stock_status;`

<u>实际结果：</u>

中的行数 `cataloginventory_stock` 在CSV导入后减少以更新库存。

<u>预期结果：</u>

中的行数 `cataloginventory_stock` 在CSV导入后应保持不变以更新库存。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
