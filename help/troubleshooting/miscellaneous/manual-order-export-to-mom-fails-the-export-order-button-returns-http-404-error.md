---
title: 手动将订单导出到MOM失败。 “导出顺序”按钮返回HTTP 404错误
description: 本文讨论如何修复以下问题：在Commerce管理员中，单击订单视图上的**导出订单**按钮尝试将订单导出到Magento Order Management(MOM)时，会返回“ *404页面未找到* ”错误。
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 手动将订单导出到MOM失败。 “导出顺序”按钮返回HTTP 404错误

Magento Order Management本文讨论如何修复尝试通过单击 **导出顺序** 在Commerce中，订单视图上的按钮将返回&quot; *404页面未找到* “错误。

## 受影响的产品和版本

* Adobe Commerce 2.2.x和2.3.x
* MOM连接器2.3.0、2.4.0、3.2.0、3.3.0

## 问题

<u>重现问题的步骤：</u>：

1. 在Commerce管理员中，单击 **销售>订单**.
1. 单击 **创建新订单** 按钮。
1. 选择用户，添加项目，选择付款和配送方式，然后单击 **提交订单** 按钮。
1. 单击 **导出顺序** 按钮，然后 **确定**.

<u>预期结果</u>：

订单已发送给MOM。

<u>实际结果</u>：

A ” *404错误：页面未找到* ”页面将显示。

## 解决方案

* 将MOM Connector升级到3.4.0(适用于Adobe Commerce 2.3.x)，或将MOM Connector 2.5(适用于Adobe Commerce 2.2.x)。
* 如果无法升级MOM连接器，可以使用CLI命令将顺序导出为Magento Order Management：

```bash
$bin/magento oms:orders:sync
```

## 相关阅读

[Magento Order Management技术文档](https://omsdocs.magento.com/en/)
