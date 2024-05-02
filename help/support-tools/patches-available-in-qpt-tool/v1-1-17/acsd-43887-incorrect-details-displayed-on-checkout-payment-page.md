---
title: 'ACSD-43887：结账付款页面上显示的详细信息不正确'
description: ACSD-43887修补程序修复了在启用公司的采购订单时，在结账付款页面上显示不正确的详细信息的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17后，即可使用此修补程序。 修补程序ID为ACSD-43887。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: 07b17f96-5236-43a7-aeaf-6bfe36c551cf
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# ACSD-43887：结账付款页面上显示的详细信息不正确

ACSD-43887修补程序修复了在启用公司的采购订单时，在结账付款页面上显示不正确的详细信息的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.17。 修补程序ID为ACSD-43887。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用公司的采购订单时，结帐付款页面上显示的详细信息不正确。

<u>先决条件</u>：

1. 已安装B2B模块。
1. 启用公司设置为 _是_. 转到 **商店** > **配置** > **常规** > **B2B功能** > **启用公司** > **是**.
1. “启用采购订单”设置为 _是_. 转到 **订单审批配置** > **启用采购订单** > **是**.
1. 将PayPal Express配置为付款方式。

<u>重现问题的步骤</u>：

1. 创建虚拟产品。
1. 从前端向公司管理员注册公司帐户。
1. 批准后端中的公司帐户并设置 **启用采购订单** 作为 _是_ 批准公司时进行更改。
1. 转到前端，然后使用在步骤2中创建的公司管理员帐户登录。
1. 为公司创建“默认用户”。 转到 **公司用户** > **添加新用户**.
1. 为公司创建“批准规则”。 转到 **批准规则** > **添加新规则**.

   * 规则类型：订单合计
   * 订单合计：大于或等于$1
   * 需要获得以下审批：公司管理员

1. 注销并使用“Default User”帐户登录。
1. 将步骤1中创建的虚拟产品添加到购物车并继续结帐。
1. 选择PayPal Express作为付款方式，然后单击 **下达采购订单**.
1. 注销并使用公司管理员帐户登录。
1. 转到 **我的采购订单** 和自 **公司采购订单**，单击 **视图** ，以了解在步骤9中创建的订单。
1. 审批采购订单。 采购订单状态应为“Approved： Pending Payment”（已批准：待定付款）。
1. 注销并使用公司“默认用户”帐户登录。
1. 转到 **我的采购订单** > **视图** > **下单**.
1. 查看 **订单摘要**.

<u>预期结果</u>：

订单摘要显示正确的非零值。

<u>实际结果</u>：

订单汇总合计值为零。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
