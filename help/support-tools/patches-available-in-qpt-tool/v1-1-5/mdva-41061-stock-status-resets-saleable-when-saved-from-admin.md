---
title: 'MDVA-41061：从管理员保存产品时，库存状态将重置为可销售'
description: MDVA-41061修补程序修复了在从管理员保存产品时，库存状态重置为可销售的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41061。 QPT 1.1.15中提供了最新的修补程序版本，带有MDVA-41061-V3修补程序ID。 请注意，Adobe Commerce 2.4.4中已修复该问题。
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061：从管理员保存产品时，库存状态将重置为可销售

MDVA-41061修补程序修复了在从管理员保存产品时，库存状态重置为可销售的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.1.5。 修补程序ID为MDVA-41061。 QPT 1.1.15中提供了最新的修补程序版本，带有MDVA-41061-V3修补程序ID。 请注意，Adobe Commerce 2.4.4中已修复该问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.2-p2、2.4.3 - 2.4.3-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从管理员保存产品后，库存状态将重置为可销售。

<u>先决条件</u>：

清单模块已安装。

<u>重现问题的步骤</u>：

1. 创建数量= 1的简单产品。
1. 使用在第1步中创建的产品下订单。
1. 运行cron — 确保 `inventory.reservations.updateSalabilityStatus` 此时将执行队列，并且产品库存状态已在中更改为零 `cataloginventory_stock_status` 表格。
1. 检查前端产品。 它应标记为 **缺货**.
1. 将产品保存在管理员中，不做任何更改。

<u>预期结果</u>：

* 库存状态不应更新。
* 产品应为 **缺货** 在前面。

<u>实际结果</u>：

* 简单产品标记为 **有货** 在前面。
* 用户获得 *请求的数量不可用* 在尝试将其添加到购物车时出现消息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
