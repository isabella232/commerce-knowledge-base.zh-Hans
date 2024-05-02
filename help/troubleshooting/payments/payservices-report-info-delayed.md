---
title: 延迟支付服务报表数据
description: 本文解释了为什么支付服务中的报表数据可能会延迟。
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 延迟支付服务报表数据

本文解释了为什么支付服务中的报表数据可能会延迟。

## 受影响的产品和版本

* [支付服务](https://marketplace.magento.com/magento-payment-services.html) 现在与Adobe Commerce版本2.4.0到2.4.4兼容。

## 问题

付款和订单付款状态报表的Payment Services报表数据可能不会立即同步。

例如，在您开票（捕获）订单或发出订单的贷项通知单之后，订单的状态可能无法立即使用。

<u>重现问题的步骤</u>：

前提条件：使用“付款服务”功能下达订单。

1. 订单为 [已开发票](https://docs.magento.com/user-guide/sales/invoice-create.html) (或 [已取消](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order) 或 [通过贷项通知单退款](https://docs.magento.com/user-guide/sales/credit-memos.html)) [管理员](https://docs.magento.com/user-guide/stores/admin.html).
1. 定位至“订单付款状态”报表，以查看有关该订单的信息。
1. 状态显示为 `AUTHORIZED`，即开票或其他订单操作之前的订单状态。

   Commerce尚未同步数据并将其发送到Payment Services，因此报表尚未识别新订单状态。

>[!NOTE]
>
>这只是一个常见用例。 在以下情况下，可能会出现其他用例 [订购操作](https://docs.magento.com/user-guide/sales/order-actions.html) 发生，并且相关数据无法立即在适用的报表中可用。

<u>预期结果</u>：对订单执行操作后，会立即填充报表数据。

<u>实际结果</u>：刚刚完成的订单操作在可见报表数据方面可能会有所延迟。 付款报告可能会延迟24-48小时。 订单付款状态报告可能会延迟几小时。

## 原因

有两个因素会影响“管理员”中可见数据的延迟：

* 您选择通过以下方式从Commerce同步（导出和保留）数据的频率 [管理员中的配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html).
* PayPal发布报表数据的时间范围。

## 解决方案

对于订单付款状态报表：

1. 导航到 **销售** > **支付服务**.
1. 单击 **订单付款状态** 查看订单付款状态报表表格。
1. 通过单击 **强制重新同步** 图标（位于报表表的右上角）。
1. 您应会看到报表表中上次更新的时间戳更改和新加载的事务。

对于PayPal支付报告而言，由于依赖于PayPal的数据发布时间范围，预计结果将延迟24至48小时。
