---
title: 'MDVA-39153：在管理员中重新排序时计算的折扣金额不正确'
description: MDVA-39153修补程序修复了在管理员中重新排序期间折扣金额计算不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8后，即可使用此修补程序。 修补程序ID为MDVA-39153。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: d4d11bea-a528-4eb5-8a57-8a7330975e4a
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-39153：在管理员中重新排序时计算的折扣金额不正确

MDVA-39153修补程序修复了在管理员中重新排序期间折扣金额计算不正确的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.8。 修补程序ID为MDVA-39153。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在管理员中重新排序期间折扣金额计算不正确。

<u>重现问题的步骤</u>：

1. 转到 **管理员** > **商店** > **配置** > **销售** > **税金**.
1. 打开购物车中显示税项的运输税。
1. 启用并配置表费率配送方式($15)。
1. 为内置税率（适用于CA）创建税则。
1. 创建购物车价格规则，并将固定的$5折扣应用于整个购物车和装运金额。
1. 将价格为$12的产品添加到购物车，然后转到购物车页面。
1. 将折扣应用到购物车。
1. 将“预计”部分中的配送方式设置为“统一费率”。
1. 继续结帐，直到完成审阅步骤（请勿下订单）。
1. 转到主页，然后返回购物车。
1. 将“估计”部分中的配送方式更改为“表费率”。

<u>预期结果</u>：

折扣保持不变，为5美元。

<u>实际结果</u>：

折扣是6.31美元。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
