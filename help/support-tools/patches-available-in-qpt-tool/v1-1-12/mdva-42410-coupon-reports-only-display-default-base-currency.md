---
title: 'MDVA-42410：优惠券报表仅显示默认基本货币'
description: MDVA-42410修补程序修复了优惠券报表仅显示基础货币的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42410。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410：优惠券报表仅显示默认基本货币

MDVA-42410修补程序修复了优惠券报表仅显示基础货币的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.12。 修补程序ID为MDVA-42410。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

优惠券报表仅显示默认基础货币。

<u>重现问题的步骤</u>：

1. 创建其他网站、商店和商店视图。
1. 为此新网站设置其他货币。 例如，欧元。
1. 转到 **商店** > **汇率** 并将汇率配置到 **欧元**.
1. 创建 **购物车价格规则** 有特定优惠券 —  **测试**.
1. 前往前端，使用 **测试** 新网站上的优惠券。
1. 转到 **报表** > **销售** > **优惠券**.
1. 在范围下拉列表中选择新网站。
1. 刷新统计信息并运行报告。

<u>预期结果</u>：

优惠券报表会将新网站的货币显示为欧元。

<u>实际结果</u>：

新网站的优惠券报表中使用默认基本货币（本例中为USD）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
