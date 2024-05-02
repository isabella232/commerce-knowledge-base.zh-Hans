---
title: 'MDVA-35773：发票上显示的税有100%折扣'
description: MDVA-35773修补程序修复了发票上折扣为100%的订单的Grand Total未显示为零的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22后，即可使用此修补程序。 修补程序ID为MDVA-35773。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773：税显示在发票上，折扣为100%

MDVA-35773修补程序修复了发票上折扣为100%的订单的Grand Total未显示为零的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.22。 修补程序ID为MDVA-35773。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.6

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.6-2.3.7和2.4.1-2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 导航到 **商店** > **设置** > **配置** > **销售** > **税金**.
1. 设置 **目录价格** 和 **应用价格折扣** 到 *含税*.
1. 导航到 **商店** > **税则** > **添加新税则**.
1. 创建税则（例如：税率为10%的所有美国）并应用它。
1. 导航到 **营销** > **购物车价格规则**、和 **添加新规则**.
1. 使用以下方式创建规则 **所有用户100%折扣**.
1. 在店面下订单：

   * 选择 **免费送货**.
   * 应用 **优惠券代码**.

1. 导航到 **销售** > **订购**，然后打开您的订单。
1. 为订单创建发票，然后将其打开。

<u>预期结果</u>：

发票总计= *0.00美元*.

<u>实际结果</u>：

发票总计= *税额* 创建。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
