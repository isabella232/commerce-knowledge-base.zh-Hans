---
title: Adobe Commerce 2.4.0Braintree虚拟终端页面已损坏
description: 本文为已知的Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致“Braintree虚拟终端”页面未加载正确的UI元素，或者如果未配置Braintree，则显示正确的错误消息。
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Adobe Commerce 2.4.0Braintree虚拟终端页面已损坏

本文为已知的Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致“Braintree虚拟终端”页面未加载正确的UI元素，或者如果未配置Braintree，则显示正确的错误消息。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

### 方案1：配置Braintree支付方式

<u>重现问题的步骤：</u>

在Commerce Admin中，转到 **销售** > **Braintree虚拟终端** .** **

<u>预期结果：</u>

此 **Braintree虚拟终端** 页面会通过正确的UI加载。

<u>实际结果：</u>

的UI **Braintree虚拟终端** 页面已损坏。

### 方案2：配置Braintree支付方式

<u>重现问题的步骤：</u>

在Commerce Admin中，转到 **销售** > **Braintree虚拟终端** .** **

<u>预期结果：</u>

此 **Braintree虚拟终端** 页面通过适当的UI加载，并显示一条警告，告知Braintree尚未配置。

<u>实际结果：</u>

的UI **Braintree虚拟终端** 页面已损坏，不显示任何警告。

## 解决方案

应用本文中提供的修补程序。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 如何应用修补程序

请参阅 [如何应用Adobe提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以获取说明。

## 附加文件
