---
title: “MDVA-40399：无法通过API同时创建同一订单的部分发票”
description: MDVA-40399修补程序修复了无法通过Rest API同时创建同一订单的部分发票的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4后，即可使用此修补程序。 修补程序ID为MDVA-40399。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 2444ba57-b30b-4fdf-9e5d-988cf7fa8dd1
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MDVA-40399：无法通过API同时创建同一订单的部分发票

MDVA-40399修补程序修复了无法通过Rest API同时创建同一订单的部分发票的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.1.4。 修补程序ID为MDVA-40399。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

不能使用Rest API同时创建相同订单的部分发票。

<u>先决条件</u>：

一种具有至少两个变体的可配置产品。

<u>重现问题的步骤</u>：

1. 将可配置产品的两个变体添加到购物车。
1. 下订单。
1. 通过Rest API同时为订单创建两张发票。

<u>预期结果</u>：

* 必须成功创建这两张发票。
* `qty_invoiced` 应更新以下两张发票的 `sales_order_item` 表格。
* 这两种产品都应该有开票数量。

<u>实际结果</u>：

* 已成功创建这两张发票。
* `qty_invoiced` 不会根据 `sales_order_item` 表格。
* 在管理员的 **订单视图** 页上，则只显示一个产品的发票数量。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
