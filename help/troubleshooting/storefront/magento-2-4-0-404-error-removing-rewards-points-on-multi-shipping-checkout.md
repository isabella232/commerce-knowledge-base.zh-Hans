---
title: 'Adobe Commerce 2.4.0：在多送货结帐中删除奖励点时出现404错误'
description: 本文为Adobe Commerce 2.4.0中的一个已知问题提供了解决方法，即在删除多配送结账页面上的奖励点时，出现“*404 Not Found*”网页错误。 目前，在多配送结账页面上，当尝试删除用于支付订单的奖励点时，会显示“*404 Not Found*”页面而不是成功的奖励点取消。 此问题将在Adobe Commerce 2.4.1补丁版本中得以解决。
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：在多送货结帐中删除奖励点时出现404错误

本文为“ ”的Adobe Commerce 2.4.0中的已知问题提供了解决方法&#x200B;*404未找到*“在多配送结算页面上删除奖励点时出现网页错误。 目前，在多配送结账页面上，当尝试删除用于支付订单的奖励点时，出现“*404未找到* ”页面而不是成功取消奖励点数。 此问题将在Adobe Commerce 2.4.1补丁版本中得以解决。

## 受影响的产品和版本

* Adobe Commerce 2.4.0（所有部署方法）

## 问题

<u>重现问题的步骤</u>

1. 导航到店面并以客户身份登录。
1. 将至少两个产品添加到 **购物车**.
1. 打开 **迷你购物车**.
1. 单击 **查看和编辑购物车** 链接。
1. 单击 **使用多个地址签出** 链接。
1. 在上选择配送地址 **收货地址多个** 页面。
1. 单击 **转到送货信息** 按钮。
1. 选择 **统一费率 — 固定配送方式** 每个地址。
1. 单击 **继续查看账单信息** 按钮。
1. 查看 **使用您的奖励积分** 上的复选框 **帐单信息** 页面。
1. 单击 **转到查看您的订单** 按钮。
1. 单击 **移除** 用于移除奖励积分的任何地址的链接。

<u>预期结果</u>

* 此 **购物车** 页面应会显示。
* “*您已从此订单中删除奖励积分。* ”消息应会出现。

<u>实际结果</u>

A ”*404未找到* 出现“错误”页面。

## 解决方法

解决方法是让采购员返回至 **购物车** 并将奖励积分从 **购物车** 网页。 Adobe Commerce版本2.4.1修补程序预计将于2020年第4季度发布，可解决此问题。

## 相关阅读

* [Adobe Commerce 2.4.0已知问题 — 无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：Storefront上显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知问题：订单显示错误](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
