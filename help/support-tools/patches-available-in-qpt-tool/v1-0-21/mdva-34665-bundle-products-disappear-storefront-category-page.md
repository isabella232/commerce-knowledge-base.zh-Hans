---
title: 'MDVA-34665：捆绑包产品消失店面类别页面'
description: MDVA-34665修补程序修复了类别页面上缺少捆绑产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21后，即可使用此修补程序。 修补程序ID为MDVA-34665。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 2b393f91-de0d-4c54-89db-5e2af13f93a6
feature: Categories, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# MDVA-34665：捆绑包产品消失店面类别页面

MDVA-34665修补程序修复了类别页面上缺少捆绑产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.21。 修补程序ID为MDVA-34665。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.4-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.4-2.3.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

**用例1：**

<u>先决条件</u>：

1. 创建一个简单的产品作为捆绑选项来创建15,000个捆绑产品。 请勿将相同的简单产品与多个捆绑产品一起使用。
1. 简单产品应设置为 *无法单独显示*.

<u>重现问题的步骤</u>：

1. 将15,000个捆绑产品分为两个类别，每个类别7,500个。
1. 选择所有简单产品(15k)并使用产品批量属性更新来更新库存。 我们的目标是在search cl表中拥有多个id（cl表是索引器用来了解哪些记录需要更新的表）。
1. 确保您拥有15K ID `catalogsearch_fulltext_cl` 表格。
1. 确保 `indexer_update_all_views` 执行索引器。
1. 连续查询类别页面并观察产品计数。

<u>预期结果</u>：

产品数应保持重新索引后的状态。

<u>实际结果</u>：

一段时间后，产品数量降至7450件。 即便在指数编制完成后，该指数仍维持在7450点。

**用例2：**

<u>重现问题的步骤</u>：

1. 创建一个捆绑产品，并将关联的简单产品作为选项。
1. 将索引器模式更改为 *按计划更新*.
1. 将捆绑产品分配给类别。
1. 将简单产品的库存状态更改为 *缺货*.
1. 执行cron；捆绑产品从店面消失。
1. 将库存添加回简单产品并保存。
1. 执行cron索引器。
1. 刷新类别页面。

<u>预期结果</u>：

产品仍然缺席。

<u>实际结果</u>：

捆绑产品将重新出现。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
