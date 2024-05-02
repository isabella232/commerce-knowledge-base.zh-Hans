---
title: 'MDVA-29446：可用于签出的不相关配送方式'
description: MDVA-29446修补程序解决了以下问题：在结账送货方法选项上显示不适用的送货方法，并且如果选中此项，则会显示错误消息“*未找到具有此类方法的运营商null，统一费率*”。 显示。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。 该问题计划在其后Adobe Commerce版本中修复。
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446：可用于签出的不相关配送方式

MDVA-29446修补程序解决了以下问题：在“结帐送货方法”选项中显示不适用的送货方法，如果选中该选项，则显示错误消息&#39;&#39;*未找到具有此类方法的空的固定速率*“ 显示。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.6。 该问题计划在其后Adobe Commerce版本中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.3.3-2.4.0。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

您有一个不适用的配送方式，但仍显示在结帐配送方式选项中，您可以选择此不相关的配送方式。

<u>重现问题的步骤</u>：

1. 安装clean 2.3-develop。
1. 启用统一速率并设置：

   * 发运至适用的国家/地区= *特定国家/地区*
   * 发运至特定国家/地区= *南极洲*
   * 显示方法（如果不适用）= *是*

1. 禁用所有其他配送方式。
1. 转到前端，创建一个具有美国地址的客户。
1. 选择项目并单击 **添加到购物车**.
1. 单击购物车，然后单击 **继续操作直到进入结账流程**.

<u>实际结果</u>：

1. 在 **配送** 页面中，您会看到以下内容：

   * 统一比率可见
   * 统一费率是$0
1. 用户单击后 **下一个**，用户会收到以下错误：

*“未找到具有此类方法的运营商：null、flatrate”*

<u>预期结果</u>：

* 如果配送方式不适用，则配送方式的价格将不可见。
* 此 **下一个** 按钮不应处于活动状态。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
