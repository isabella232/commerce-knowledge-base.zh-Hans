---
title: 'MDVA-42326：会话超时后客户在签出时出错'
description: MDVA-42326修补程序解决了即使在启用了永久购物车的情况下，客户在会话超时后结账时出现错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8后，即可使用此修补程序。 修补程序ID为MDVA-42326。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326：会话超时后客户在签出时出错

MDVA-42326修补程序解决了即使在启用了永久购物车的情况下，客户在会话超时后结账时出现错误的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.8。 修补程序ID为MDVA-42326。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使启用了永久购物车，客户在会话超时后也会在结账时遇到错误。

<u>先决条件</u>：

1. 转到 **配置** > **常规** > **Web** > **默认Cookie设置** > **Cookie生命周期** 并设置为 **120**.
1. 转到 **配置** > **客户** > **客户配置** > **在线客户选项** 并将这两个值设置为 **2**.
1. 转到 **配置** > **客户** > **永久购物车** 并设置为 **启用**.
1. 转到 **配置** > **销售** > **支付方式** 并关闭所有支付方式，但 **支票/汇票** （应该启用它）。

<u>重现问题的步骤</u>：

1. 以客户身份登录并将一些产品添加到购物车。
1. 检查购物车。
1. 等待两分钟（在前提条件中设置）；会话应超时。
1. 单击 **转到结帐** 并且不要刷新页面。
1. 结帐为来宾，填写送货地址并选择送货方式。
1. 单击 **下一个**.
1. 在 **审核与支付** 页面，单击 **下单**. 由于只允许一种付款方式，因此客户无需选择付款方式即可下订单。

<u>预期结果</u>：

客户应该能够下订单。

<u>实际结果</u>：

客户收到以下错误： *地址验证失败：电子邮件的格式错误*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
