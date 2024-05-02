---
title: 'MDVA-33281修补程序：清单不一致问题'
description: MDVA-33281修补程序修复了三个清单不一致问题。 单击问题部分下面的链接问题，查看重现这些错误的步骤。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14后，即可使用此修补程序。
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-33281修补程序：清单不一致问题

MDVA-33281修补程序修复了三个清单不一致问题。 单击问题部分下面的链接问题，查看重现这些错误的步骤。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.14。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5-p1

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

该修补程序修复了清单不一致问题，例如：

* **PHP致命错误** 运行时 `bin/magento inventory:reservation:list-inconsistencies` 在CLI中，因为错误的SKU参数类型。
* **重复数据** 在不一致列表中。
* **新建预订** 将在下订单前创建（先前实现基于下订单后的预订）。 如果订购过程中出现错误，将添加额外的预订以进行补偿。

>[!NOTE]
>
>此外，还有一个修补程序MDVA-30112，它解决了意外出现大量修补程序的问题， [预订不一致](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) 在我们的开发人员文档中的 `inventory_reservation` 表格。 有关解决方案，请参阅 [MDVA-30112Magento修补程序：大量保留不一致](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) 在我们的支持知识库中。

## PHP致命错误

<u>重现问题的步骤</u>：

运行时出现PHP致命错误 `bin/magento inventory:reservation:list-inconsistencies`.

要获取保留不一致列表，请登录到生产服务器，然后在CLI中运行以下命令（ — r开关 — 原始输出）：

<pre>bin/magento清单:reservation:list-inconsistency -r</pre>

<u>预期结果</u>：

将创建保留不一致列表。 这些将以下列格式返回

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>实际结果</u>：

PHP致命错误已输出。

## 重复数据

重复数据位于 `inventory_reservation table`.

<u>重现问题的步骤</u>：

要对保留不一致问题进行故障诊断，请运行以下命令：

<pre>按元数据、SKU、COUNT(*) &gt; 1的数量从inventory_reservation组中选择*、COUNT(*)</pre>

<u>预期结果</u>：

无重复项。

<u>实际结果</u>：

存在重复项。

## 新建预订

<u>重现问题的步骤</u>：

在下单前创建的新预订：

1. 导入数据库。
1. 运行 `bin/magento setup:upgrade` 在终端机里。
1. 通过运行列出不一致 `bin/magento inventory:reservation:list-inconsistencies        -i -r` 在终端机里。

<u>预期结果</u>：

没有循环，结果更快。

<u>实际结果</u>：

相同的结果会显示在无限循环中，否则命令会失败 `memory_limit`，具体取决于系统设置。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
