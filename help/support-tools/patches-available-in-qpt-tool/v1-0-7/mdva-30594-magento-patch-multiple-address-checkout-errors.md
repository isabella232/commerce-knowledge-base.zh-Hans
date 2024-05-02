---
title: 'MDVA-30594：多个地址签出错误'
description: MDVA-30594修补程序解决了客户在多个地址下订单后看不到订单成功页面的问题。 在Commerce管理员中检查订单时，会显示两个订单，这些订单包含相同的产品，而不是正确的产品。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 已在Adobe Commerce 2.4.2中修复此问题。
exl-id: 7560cc39-ff0d-4313-979e-5cd588554c1d
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# MDVA-30594：多个地址签出错误

MDVA-30594修补程序解决了客户在多个地址下订单后看不到订单成功页面的问题。 在Commerce管理员中检查订单时，会显示两个订单，这些订单包含相同的产品，而不是正确的产品。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.7。 已在Adobe Commerce 2.4.2中修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

多个地址订单在订单成功页面中并不完成，且显示两个订单，其中包含相同的产品而不是正确的产品。

<u>先决条件</u>：

创建两个包含商店和商店视图的网站。

<u>重现问题的步骤</u>：

1. 设置 **目录价格范围** 对于网站目录(**商店** > **设置** > **配置** > **目录** > **目录** > **价格** > **范围**)。
1. 配置 **固定产品税(FPT)** (**商店** > **配置** > **销售** > **税金** > **固定产品税**)：

   * **启用FPT** = *是*
   * **在产品列表中显示价格** = *不包括FPT*
   * **在产品查看页面上显示价格** = *不包括FPT*
   * **在销售模块中显示价格** = *不包括FPT* (包括 **FPT** 说明和最终价格)。
   * **在电子邮件中显示价格** = *不包括FPT* (包括 **FPT** 说明和最终价格)。
   * **将税应用于FPT** = *是*
   * **将FPT包含在小计中** = *否*

1. 创建 **FPT属性**，并将其分配给默认属性集。 (请参阅 [配置FPT：创建FPT属性](https://docs.magento.com/user-guide/tax/fixed-product-tax-configuration.html#step-2-create-an-fpt-attribute) （在我们的用户指南中）。

1. 创建四个简单的产品，并将 **FPT** **属性值** (示例：设置 **FPT**   **属性值** = *澳大利亚*)。

1. 使用以下配置创建两个捆绑产品：

   * 定义 **FPT**.
   * 设置 **动态价格** = *否*.
   * 设置 **价格** = *100*.
   * 捆绑选项一起发货，所有选项均标记为默认的 **价格类型** = *固定*.
   * 添加在步骤4中创建的两个简单产品。

1. 在前端创建用户帐户。 使用澳大利亚地址更新地址(将国家/地区设置为“澳大利亚”或 **FPT** 设置)。

1. 将两个捆绑产品添加到购物车。

1. 转到购物车页面，并检查 **FPT** 正确显示。

1. 单击 **使用多个地址签出**.

1. 添加第二个地址。

1. 将每个产品分配给不同的地址。

1. 结账过程一直持续到 **下单**.

1. 单击 **下单** 按钮。

<u>预期结果</u>：

已成功下达多个地址的订单。

<u>实际结果</u>：

一条类似于“*出现错误。*“”将会出现。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
