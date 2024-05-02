---
title: 'Adobe Commerce 2.3.5、2.3.5-p1修补程序：国家/地区付款问题'
description: 此补丁解决了Adobe Commerce中店面结账工作流未显示任何为特定国家/地区启用的支付方法的问题，Klarna和Amazon Pay除外。
exl-id: e205e35e-9ffe-4826-b951-3a3caf1e0621
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Adobe Commerce 2.3.5、2.3.5-p1修补程序：国家/地区付款问题

此补丁解决了Adobe Commerce中店面结账工作流未显示任何为特定国家/地区启用的支付方法的问题，Klarna和Amazon Pay除外。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.5和2.3.5-p1
* Adobe Commerce内部部署2.3.5和2.3.5-p1

## 问题

当店铺具有Amazon Pay和分配给不同国家/地区的另一个付款时，并且选择了其中一个国家/地区和付款方法时，付款方法和下单按钮不可见。

刷新网页是解决此问题的一种方法。

为了解决此问题并删除错误，我们创建了 [patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip).

<u>先决条件</u>：

* 创建简单产品。
* **支票/汇票** 仅对特定国家/地区启用(位于 **存储** > **配置** > **销售** > **支付方式**)。

* 实例：适用国家/地区的付款=特定国家/地区
* 实例：来自特定国家/地区的付款=英国

<u>重现问题的步骤</u>：

1. 以客人身份去店面。
1. 将简单产品添加到购物车。
1. 转到“结帐”。
1. 使用有效数据填写表单。

   * 国家/地区= *美国*

1. 选择配送费率并单击 **下一个**.

   * 付款步骤已打开。
   * 没有可用的付款。
   * 消息： **无可用的支付方式。**
   * 没有 **下单** 按钮。

1. 返回 **配送步骤** 并将值更改为：

   * 国家/地区= *英国*

1. 选择配送费率并单击 **下一个**.

<u>预期结果</u>：

此时将打开付款步骤。

* **货到付款** 显示。
* **支票/汇票** 显示。
* 此 **下单** 按钮出现。

<u>实际结果</u>：

此时将打开付款步骤。

* 没有可用的付款。
* 消息： *无可用的支付方式。*
* 没有 **下单** 按钮。

## 解决方案

[应用修补程序](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip) 下。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[下载BUNDLE-2546\_EE\_2.3.5-p1.composer.patch](assets/BUNDLE-2546_EE_2.3.5-p1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.3.5和2.3.5-p1
* Adobe Commerce内部部署2.3.5和2.3.5-p1

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce版本2.3.4 - p2 - 2.2.6

## 如何应用修补程序

请参阅 [如何应用Adobe Commerce提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我们的支持知识库中获取说明。

## 附加文件
