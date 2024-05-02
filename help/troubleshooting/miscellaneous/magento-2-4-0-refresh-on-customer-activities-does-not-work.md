---
title: “Adobe Commerce 2.4.0：无法刷新客户活动”
description: 本文为管理员用户为客户创建订单并且客户的“活动”侧面板上的“刷新”按钮不起作用时Adobe Commerce 2.4.0已知问题提供了解决方案。
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：无法刷新客户的活动

本文为管理员用户为客户创建订单并且客户的“活动”侧面板上的“刷新”按钮不起作用时Adobe Commerce 2.4.0已知问题提供了解决方案。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>重现问题的步骤</u>：

1. 转到 **管理面板** > **销售** > **订购**.
1. 单击 **创建新订单** 按钮。
1. 选择已创建的客户。
1. 以创建的客户身份转到店面。
1. 转到 **产品** 页面。 单击 **刷新** 上的按钮 **最近查看的产品** 部分 **客户活动**.
1. 回到店面。
1. 使用创建的产品下订单。
1. 返回 **管理面板** 然后单击 **刷新** 的按钮 **上次订购的项目** 部分 **客户活动**.
1. 回到店面。 将创建的产品添加到 **比较列表**.
1. 返回 **管理面板**. 单击 **刷新** 的按钮 **比较列表中的产品** 部分 **客户活动**.
1. 回到店面。
1. 从删除创建的产品 **比较列表**.
1. 返回 **管理面板**.
1. 单击 **刷新** 的按钮 **最近比较的产品** 部分 **客户活动**.
1. 回到店面。

<u>预期结果</u>：

产品的名称应显示在 **最近查看的产品**， **上次订购的项目**， **比较列表中的产品**、和 **最近比较的产品** 部分。

<u>实际结果</u>：

每次在页面上 **刷新** 已单击按钮。 产品的名称未显示在相应的部分中。

## 解决方案

解决方法是管理员用户可以更新 **客户活动** 通过单击 **更新更改** 按钮进行标记。 计划在Adobe Commerce 2.4.1修补程序中解决此问题。

![mceclip0.png](assets/mceclip0.png)

## 相关阅读

* [Adobe Commerce 2.4.0已知问题：Braintree支付方式未显示在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0中的配送标签创建已知问题](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知问题：店面中显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
