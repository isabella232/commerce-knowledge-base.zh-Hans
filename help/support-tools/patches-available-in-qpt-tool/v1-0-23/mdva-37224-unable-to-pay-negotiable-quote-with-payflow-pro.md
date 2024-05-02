---
title: '''MDVA-37224：无法通过PayFlow Pro支付“可协商报价”'
description: MDVA-37224修补程序修复了客户无法使用Paypal PayFlow Pro支付**可转让报价**的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23后，即可使用此修补程序。 修补程序ID为MDVA-37224。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224：无法通过PayFlow Pro支付“可协商报价”

MDVA-37224修补程序修复了客户无法为 **可转让报价** 与Paypal PayFlow Pro. 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.23。 修补程序ID为MDVA-37224。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

* 该补丁是为Adobe Commerce on cloud infrastructure 2.3.6-p1设计的
* 该补丁还兼容本地Adobe Commerce和云基础架构2.3.3-2.4.2-p1上的Adobe Commerce

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

* 已安装B2B模块的Adobe Commerce
* 已启用公司功能
* **可转让报价** 功能已启用
* 公司用户已存在
* 已启用和配置PayPal PayFlow Pro支付方式
* PayPal PayFlow Pro付款方法允许用于B2B
* 已创建2个不同价格的产品

<u>重现问题的步骤</u>：

1. 打开店面。
1. 添加 **产品1** 到购物车。
1. 创建 **可转让报价** 对象 **产品1**.
1. 添加 **产品2** 到购物车。
1. 从管理员处接受 **可转让报价** 在步骤3中创建。
1. 从店面，打开这个 **可转让报价** 然后继续结帐。
1. 选择 **付款方式** = *PayPal PayFlow Pro* 在 **审核和支付** 步骤。
1. 下订单。

<u>预期结果</u>：

* 订单按预期成功下达。
* PayPal会按预期向客户发送包含正确信息的电子邮件。

<u>实际结果</u>：

* 网页挂起，无法完成订单。
* PayPal使用零值向客户发送确认，类似于以下示例：

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 
   * [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
