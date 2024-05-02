---
title: “ACSD-45241：虚拟产品的库存数量计算错误”
description: ACSD-45241修补程序修复了在创建贷项通知单后虚拟产品的库存数量计算错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17后，即可使用此修补程序。 修补程序ID为ACSD-45241。 请注意，Adobe Commerce 2.4.4中已修复此问题。
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241：虚拟产品的库存数量计算错误

ACSD-45241修补程序修复了在创建贷项通知单后虚拟产品的库存数量计算错误的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.17。 修补程序ID为ACSD-45241。 请注意，Adobe Commerce 2.4.4中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

创建贷项通知单后，虚拟产品的库存数量计算错误。

<u>重现问题的步骤</u>：

1. 在Commerce管理员中创建可配置产品，并将虚拟产品作为子产品。
1. 请确保在步骤1中创建的两个产品均有库存。
1. 将步骤1中创建的虚拟产品的数量标记为100，同时保留可销售数量100。
1. 将产品添加到购物车。
1. 使用在步骤1中创建的虚拟产品下订单。
1. 将订单状态保持为“待处理”。 无需处理付款。
1. `order_created` 记录创建于 `inventory_reservation`. 虚拟产品数量显示为100，可销售数量为99。
1. 打开订单并转到 **发票** > **提交发票**.
1. `invoice_created` 记录创建于 `inventory_reservation`. 现在，虚拟产品数量为99，可销售数量也为99。
1. 创建贷项通知单，但不选择 **返回股票**.

<u>预期结果</u>：

在中未创建新记录 `inventory_reservation`，而虚拟产品的库存数量保持不变。

<u>实际结果</u>：

A `creditmemo_created` 记录创建于 `inventory_reservation`，将虚拟产品库存数量调整为98，可销售数量为99。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
