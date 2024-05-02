---
title: 'MDVA-33970修补程序：贷项通知单中的货币签名'
description: MDVA-33970修补程序解决了在贷项通知单中显示美元($)符号而非本地化货币的问题。 当**Website**范围用于**Price**属性时，会发生这种情况。
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# MDVA-33970修补程序：贷项通知单中的货币签名

MDVA-33970修补程序解决了在贷项通知单中显示美元($)符号而非本地化货币的问题。 这种情况发生于 **网站** 范围用于 **价格** 属性。

此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.15。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.4-p2

**与Adobe Commerce版本兼容：** 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.4 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>前提条件</u>：

在本例中，使用以下设置：

* 存在2个网站 — 每个网站都有 **存储** 和 **商店视图**.
* 此 **默认配置** 新加坡元作为 **货币** (**存储>配置>常规>货币设置**)：
   * **基础货币** = *新加坡元*
   * **默认显示货币** = *新加坡元*
   * **允许的货币** = *新加坡元*
* **网站1** 具有 **默认配置**.
* **网站2** 马来西亚林吉特 **货币**：
   * **基础货币** = *马来西亚林吉特*
   * **默认显示货币** = *马来西亚林吉特*
   * **允许的货币** = *马来西亚林吉特*
* 转到 **存储>货币符号**，并设置：
   * **MYR （马来西亚林吉特）** = *RM*
   * **新加坡元（新加坡元）** = *SGD* (**使用标准** = *已选中*)
* 部分 **产品** 已存在。

<u>重现问题的步骤</u>：

1. 建立 **订购** 从 **网站2** （您可以将其设置为“默认”以避免其他设置）。
1. 登录 **管理员**.
1. 打开新创建的订单。
1. 检查 **货币符号** = *RM*.
1. 创建 **发票**.
1. 检查 **货币符号** = *RM* 在发票中。
1. 创建 **贷项通知单**.
1. 检查 **货币符号**  ** ** = *RM* 在 **贷项通知单**.
1. 打开 **贷项通知单** tab in **订购**.
1. 查看 **货币符号** 在网格中。
1. 打开 **销售>贷项通知单**.
1. 查看 **货币符号** 在网格中。

<u>预期结果</u>：

使用正确的本地化货币符号（如预期）。

<u>实际结果</u>：

美元符号($)已使用，即使未在管理员设置中进行设置也是如此。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
