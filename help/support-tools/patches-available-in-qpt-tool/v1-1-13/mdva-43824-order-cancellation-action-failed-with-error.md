---
title: '''MDVA-43824：订单取消操作失败，出现错误“您未取消项目”'
description: 'MDVA-43824修补程序解决了订单取消操作失败的问题，并出现错误：*您尚未取消项目*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-43824。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。'
exl-id: e4d839d6-84ed-4157-80a1-fd482fef897c
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-43824：订单取消操作失败，错误为“尚未取消项目”

MDVA-43824修补程序解决了订单取消操作失败并出现错误的问题： *您尚未取消该项目*. 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.13。 修补程序ID为MDVA-43824。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.6 - 2.3.7 - p3、2.4.1 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法取消由已登录的客户下达的订单。 订单取消操作失败，出现以下错误：

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>重现问题的步骤</u>：

1. 创建销售规则（优惠券类型为“特定优惠券”或“无优惠券”）。
1. 转到店面，以客户身份登录，然后将产品添加到购物车。
1. 如果购物车价格规则具有优惠券作为“特定优惠券”，请转到购物车并应用购物车价格规则。 购物车价格规则应成功应用。
1. 前往结账并使用任何付款方式下订单。
1. 转到Commerce管理员> **销售** > **订购**.
1. 打开在步骤4中下达的订单。
1. 单击 **取消** 按钮。

<u>预期结果</u>：

已成功取消订单，且没有错误。

<u>实际结果</u>：

订单取消操作失败，出现以下错误： *您尚未取消该项目。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
