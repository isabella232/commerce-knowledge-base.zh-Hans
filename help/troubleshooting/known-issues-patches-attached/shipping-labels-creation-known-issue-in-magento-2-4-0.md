---
title: Adobe Commerce 2.4.0中的配送标签创建已知问题
description: 本文为已知的Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致无法创建送货标签。
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Adobe Commerce 2.4.0中的配送标签创建已知问题

本文为已知的Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致无法创建送货标签。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>先决条件</u>：使用FedEx、DHL、UPS或USPS配送方式创建订单。

### 方案1：添加发运时创建标签

<u>重现问题的步骤：</u>

1. 在“管理员”中的以下位置打开所下的订单： **销售** > **订购**.
1. 单击 **发货** 按钮。 此 **新建装运** 页面将打开。

<u>预期结果：</u>

此 **创建送货标签** 复选框显示在页面底部。

<u>实际结果：</u>

此 **创建送货标签** 复选框未显示。

### 方案2：为现有发运创建标签

<u>重现问题的步骤：</u>

1. 在“管理员”中的以下位置打开所下的订单： **销售** > **订购**.
1. 单击 **发货** 按钮。 此 **新建装运** 页面将打开。
1. 单击 **提交装运** 按钮。 已创建装运。
1. 打开新创建的装运。
1. 单击 **创建送货标签** 按钮。 此 **创建包** 对话框打开。

<u>预期结果：</u>

此 **将产品添加到包** 上的按钮 **创建包** 模态窗口显示包含订单项的字段。

<u>实际结果：</u>

此 **创建包** 模态窗口未正确显示，无法将订单项目添加到装运。

## 解决方案

应用本文中提供的修补程序。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[MC-35514-2.4.0-CE-composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

该修补程序也可在以下两个页面中下载： `.git` 和 `.composer`，格式位于 [Adobe Commerce下载](https://magento.com/tech-resources/download) 页面，在 **补丁程序** 在左列导航中。 搜索MC-35514修补程序。

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce版本2.4.0
* Adobe Commerce内部部署版本2.4.0

## 如何应用修补程序

请参阅 [如何应用Adobe提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以获取说明。

## 附加文件
