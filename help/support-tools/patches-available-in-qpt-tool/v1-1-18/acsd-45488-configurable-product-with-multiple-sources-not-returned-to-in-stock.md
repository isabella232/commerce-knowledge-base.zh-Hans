---
title: 'ACSD-45488：具有多个来源的可配置产品不会自动退货'
description: ACSD-45488修补程序解决了具有多个来源的可配置产品无法自动退订的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18后，即可使用此修补程序。 修补程序ID为ACSD-45488。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488：具有多个来源的可配置产品不会自动退货

ACSD-45488修补程序解决了具有多个来源的可配置产品无法自动退订的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.18。 修补程序ID为ACSD-45488。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有多个来源的可配置产品不会自动返回到库存中。

<u>重现问题的步骤</u>：

1. 创建辅助库存来源。
1. 创建具有两个关联虚拟产品的可配置产品。
1. 将关联产品分配给默认库存来源，并将数量设置为1。
1. 查看 `stock_status` 从 `cataloginventory_stock_status`.
1. 将两个关联产品设置为 *缺货*.
1. 查看 `stock_status` 从 `cataloginventory_stock_status`.
1. 将两个关联产品设置为 *有货*.
1. 查看 `stock_status` 从 `cataloginventory_stock_status`.

<u>预期结果</u>：

可配置产品的库存状态将更新为 *有货* 当关联产品设置为有库存时。

<u>实际结果</u>：

可配置产品的库存状态不会更新到 *有货* 当关联产品设置为有库存时。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
