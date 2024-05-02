---
title: “MDVA-35982：无法发送某些订单”
description: MDVA-35982修补程序修复了以下错误：仅限特定网站的管理员用户无法为同一网站上的订单创建装运。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-35982。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982：无法发运某些订单

MDVA-35982修补程序修复了以下错误：仅限特定网站的管理员用户无法为同一网站上的订单创建装运。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.19。 修补程序ID为MDVA-35982。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

商家无法发送某些订单。

<u>重现问题的步骤</u>：

1. 选择产品的任意产品网站（默认商店除外）。 请参阅 [网站中的产品](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) 详细步骤。
1. 为具有自定义角色范围的管理员创建用户角色，其中未选择默认网站/商店。 请参阅 [定义角色](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) 详细步骤。
1. 在编辑模式下打开产品，并在中设置此产品的组价格 **高级定价**. 请参阅 [组价格](https://docs.magento.com/user-guide/catalog/product-price-group.html) 详细步骤。
1. 使用此产品创建订单。
1. 使用此用户角色以管理员身份登录并创建装运。 请参阅 [创建发运](https://docs.magento.com/user-guide/sales/shipments-create.html) 详细步骤。

<u>预期结果</u>：

将创建装运。

<u>实际结果</u>：

将显示以下错误：

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
