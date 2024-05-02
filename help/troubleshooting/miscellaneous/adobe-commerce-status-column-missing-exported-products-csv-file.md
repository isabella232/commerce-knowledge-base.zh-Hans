---
title: Adobe Commerce状态列缺少导出的产品CSV文件
description: 当您在包含已导出产品的CSV文件中找不到状态列时，本文提供了此问题的解决方案。
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Adobe Commerce状态列缺少导出的产品CSV文件

当您在包含导出产品的CSV文件中找不到状态列（即，指示产品是启用还是禁用）时，本文提供了此问题的解决方案。 产品的状态由 [!UICONTROL product_online] 列。

## 受影响的产品和版本

Adobe Commerce（所有部署方法）所有 [支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

您找不到 [!UICONTROL status] 包含已导出产品的CSV文件中的列。 因此，例如，您导出包含所有SKU的CSV及其状态，但该表似乎缺少 [!UICONTROL status] 列。

<u>重现问题的步骤：</u>

1. 在Adobe Commerce管理员中，选择 **[!UICONTROL System]**，下 **[!UICONTROL Data Transfer]** 选择 **[!UICONTROL Export]**.
1. 在 **[!UICONTROL Export Settings]** 部分，选择位于以下位置的 **[!UICONTROL Entity Type]** 下拉框 **[!UICONTROL Products]**.
1. 搜索 **[!UICONTROL status]**，列在 **[!UICONTROL Attribute Code]**. 您会在可用属性列表中看到该属性代码(**[!UICONTROL Enable Product]**)。
1. 单击 **[!UICONTROL Export]**.

<u>预期结果：</u>

在刚刚导出的CSV文件中，您会看到一列标记为 [!UICONTROL status].

<u>实际结果：</u>

您没有看到标记为的列 [!UICONTROL status] 在导出的csv文件中。

## 原因

已在CSV文件中重命名产品的状态属性。 现在是 [!UICONTROL product_online] 列。

## 解决方案

1. 选择 **[!UICONTROL System]**，下 **[!UICONTROL Data Transfer]** 选择 **[!UICONTROL Import]**.
1. 单击 **[!UICONTROL Download Sample File]**.
1. 您可以看到 [!UICONTROL product_online] 列（位于CSV文件中）。

## 相关阅读

* [使用CSV文件](https://docs.magento.com/user-guide/system/data-csv.html) 在我们的用户指南中。
* [产品导出属性参考](https://docs.magento.com/user-guide/system/data-attributes-product.html) 在我们的用户指南中。
