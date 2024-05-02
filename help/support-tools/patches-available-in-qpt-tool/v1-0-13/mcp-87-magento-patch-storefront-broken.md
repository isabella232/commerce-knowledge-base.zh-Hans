---
title: 'MCP-87 Adobe Commerce补丁：店面已损坏'
description: MCP-87 Adobe Commerce修补程序修复了目录的库存重新索引速度缓慢的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# MCP-87 Adobe Commerce修补程序：店面已损坏

MCP-87 Adobe Commerce修补程序修复了目录的库存重新索引速度缓慢的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.13。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构2.4.0上的Adobe Commerce 。

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.3.1 - 2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

大配置文件目录的股票重新指数非常慢。

<u>重现问题的步骤：</u>

1. 登录到“管理面板”。
1. 导航到： **产品** > **目录**.
1. 选择“产品”网格中的所有项目。
1. 选择 **更新属性** 在选择产品操作下拉列表中。 单击 **提交**.
1. 单击 **高级清单** 从“高级设置”选项卡。 更改 **库存可用性** 到 *有货*. 单击 **保存**.
1. 手动执行完全重新索引，从根目录执行以下命令： `bin/magento indexer:reindex`

<u>预期结果：</u>

股票索引器会快速重新编制指数。

<u>实际结果：</u>

Stock索引器运行速度非常慢和/或没有完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
