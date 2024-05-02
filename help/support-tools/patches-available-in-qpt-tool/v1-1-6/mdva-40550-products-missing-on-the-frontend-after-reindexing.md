---
title: 'MDVA-40550：重新索引后前端上缺少产品'
description: MDVA-40550修补程序解决了重新索引导致部分或所有店面类别缺少产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-40550。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 0aca6eb2-6eb2-4ac4-8ae1-052f671c14e5
feature: Categories, Console, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-40550：重新索引后前端上缺少产品

MDVA-40550修补程序解决了重新索引导致部分或所有店面类别缺少产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.6。 修补程序ID为MDVA-40550。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 创建产品。
1. 将索引器切换到 **按计划更新**.
   * 将产品分配给类别。
1. 在中启用xdebug并生成xdebug断点 `\Magento\Indexer\Model\Indexer::reindexAll` 和 `\Magento\Indexer\Model\IndexMutex::execute`.
1. 运行 **完全重索引** 之 `catalog_category_product` 使用命令：

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * 等待执行在断点上停止 `\Magento\Indexer\Model\Indexer::reindexAll`.

1. 在另一个控制台中，运行 **部分重索引** 与以下命令并行运行：

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 等待执行在断点上停止 `\Magento\Indexer\Model\IndexMutex::execute`. 它会锁定 `catalog_category_product` 索引器。
1. 恢复完全重新索引的执行 `catalog_category_product` 并等待锁定超时（60秒）。

<u>预期结果</u>：

控制台中没有错误消息。

<u>实际结果</u>：

您会收到以下错误：

*无法获取索引catalog_category_product的锁定。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
