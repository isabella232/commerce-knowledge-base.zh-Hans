---
title: CSV导入后，新客户未显示在客户网格中
description: 修复了从“.csv”文件导入后，在**Customers** &gt； **All customers**下看不到新客户的问题。 解决方案是将“customer_grid”索引器设置为“保存时更新”模式，并手动重新索引客户网格。
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# CSV导入后，新客户未显示在客户网格中

本文修复了在下看不到新客户的问题 **客户** > **所有客户** 从导入之后 `.csv` 文件。 解决方案是设置 `customer_grid` 索引器以“保存时更新”模式并手动重新索引客户网格。

## 受影响的版本

* Adobe Commerce内部部署2.2.0及更高版本
* Cloud Infrastructure 2.2.0及更高版本上的Adobe Commerce

## 问题

从导入新客户后 `.csv` 文件使用本机Adobe Commerce导入功能，您可能无法在下看到新的客户记录 **客户** > **所有客户** 在管理员中，直到手动重新索引 `customer_grid` 索引器。

## 原因

Adobe Commerce 2.2.0及更高版本中的“按计划更新”索引模式不支持 `customer_grid` 索引器性能问题。

## 解决方案

配置 `customer_grid` 使用“保存时更新”模式重新索引的索引器。 为此，请执行以下步骤：

1. 登录到Commerce管理员。
1. 单击 **系统** > **工具** > **索引管理**.
1. 选中Customer Grid索引器旁边的复选框。
1. 在 **操作** 下拉列表，选择 *保存时更新*.
1. 单击 **提交**.

我们还建议手动重新索引 `customer_grid` 索引器以确保索引是最新的并且可以与cron配合使用。 要手动重新索引，请使用以下命令：

`bin/magento indexer:reindex customer_grid`

## 更多信息

链接到我们的开发人员文档中的相关主题：

* [索引概述](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [管理索引器](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
