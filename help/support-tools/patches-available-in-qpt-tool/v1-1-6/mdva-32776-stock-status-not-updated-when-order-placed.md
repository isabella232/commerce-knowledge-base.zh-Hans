---
title: 'MDVA-32776：库存状态未随订单投放更新'
description: MDVA-32776修补程序修复了在下订单但未发送时，库存状态未更新的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-32776。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776：库存状态未随订单投放更新

MDVA-32776修补程序修复了在下订单但未发送时，库存状态未更新的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.1.6。 修补程序ID为MDVA-32776。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

Adobe Commerce（所有部署方法） 2.4.0

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订购但未发运时，库存状态不会更新。

<u>先决条件</u>：

1. 清单模块已安装。
1. 显示缺货产品设置为 *是*.

   若要设置，请转到 **商店** > **配置** > **目录** > **库存** > **显示缺货产品** = *是*.

<u>重现问题的步骤</u>：

1. 创建两个数量分别为11和22的简单产品。
1. 使用在第一步中创建的简单产品创建分组产品。
1. 通过将其中一个产品数量设置为11并使另一个简单产品缺货，将已分组的产品添加到购物车。
1. 完成结账并下订单。

<u>预期结果</u>：

分组的产品显示 `out-of-stock` 关联的简单产品缺货时的标签。

<u>实际结果</u>：

1. 数量= 11的简单产品缺货。
1. 分组的产品不显示 *缺货* 数量为11的产品消息。 但是，将此产品添加到购物车会 *缺货* 错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
