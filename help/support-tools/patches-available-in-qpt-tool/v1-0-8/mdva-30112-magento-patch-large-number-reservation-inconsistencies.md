---
title: 'MDVA-30112：大量预订不一致'
description: MDVA-30112修补程序解决了“inventory_reservation”表中意外出现大量[保留不一致](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies)的问题。 预订不一致包括未注册的未结订单和未注册的完整订单。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.2中已修复此问题。
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112：大量预订不一致

MDVA-30112修补程序可解决以下问题： [预订不一致](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) 在 `inventory_reservation` 表格。 预订不一致包括未注册的未结订单和未注册的完整订单。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.8。 请注意，Adobe Commerce版本2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.4 - 2.3.5-p2、2.4.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此 [簇大小](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) value表示一次加载多少订单。 当订单数超过此值时，Adobe Commerce会将状态为待定状态的订单视为不一致。

>[!NOTE]
>
>有一个修补程序MDVA-33281，它修复了其他三个清单不一致问题。 这包括在运行时出现PHP致命错误 `bin/magento inventory:reservation:list-inconsistencies` 在CLI中。 另一个已修复的问题是不一致列表中的数据重复。 此外，在发出订单之前创建预订的问题（以前实现基于发出订单之后的预订）。 有关解决方案，请参阅 [MDVA-33281：库存不一致问题](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) 在我们的支持知识库中。

<u>先决条件</u>：

在CLI中运行以下命令以列出 `inventory_reservation` 表：

```
magento inventory:reservation:list-inconsistencies
```

您会看到意外的大量预订不一致和/或命令从不完成。

<u>重现问题的步骤</u>：

1. 在CLI中运行以下命令以解决不一致问题：

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. 下三张订单：
   * 为每个产品分配一个产品。
   * 使用支票/汇票付款方式，因此订单状态将为“待定”。
1. 您可以在中看到三个数量为–1的记录 `inventory_reservation` 表格。 在CLI中运行以下命令以查看任何不一致：

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   这不会返回任何结果，这是正确的。

1. 在CLI中运行以下命令：

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   您会看到“挂起”状态订单显示为不一致。

1. 在CLI中运行以下命令：

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>预期结果</u>：

Adobe Commerce不应解决“挂起”状态订单不一致的问题。 对于处于“完成”、“已关闭”和“已取消”状态的订单，应解决库存不一致问题。

<u>实际结果</u>：

当订单数超过指定的束团大小值时，Adobe Commerce会将状态为“待处理”的订单视为不一致，并为同一订单添加多个不一致问题解决记录。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
