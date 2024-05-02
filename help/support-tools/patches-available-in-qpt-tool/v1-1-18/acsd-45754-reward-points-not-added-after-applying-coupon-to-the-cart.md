---
title: 'ACSD-45754：将优惠券应用到购物车后未添加奖励积分'
description: ACSD-45754修补程序解决了将优惠券应用到购物车后未添加奖励点数的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18后，即可使用此修补程序。 修补程序ID为ACSD-45754。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: 957713c0-3e2e-4dc9-8924-2ae84c817e47
feature: Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-45754：将优惠券应用到购物车后未添加奖励积分

ACSD-45754修补程序解决了将优惠券应用到购物车后未添加奖励点数的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.18。 修补程序ID为ACSD-45754。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.1 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将优惠券应用到购物车后，不会添加奖励积分。

<u>先决条件</u>：

已配置PayPal支付方式。

<u>重现问题的步骤</u>：

1. 通过以下方式创建奖励点汇率： **存储** > **其他设置** > **奖励汇率**.
1. 创建带有优惠券的购物车价格规则，为登录的客户应用100个奖励积分。
1. 以具有PayPal和优惠券代码的登录客户身份查看产品。
1. 检查管理员中客户帐户下的奖励点历史记录。

<u>预期结果</u>：

根据价格规则向客户添加奖励积分。

<u>实际结果</u>：

不会向客户添加奖励积分。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
