---
title: 'MDVA-30972：订单状态错误通过REST API创建的装运'
description: MDVA-30972修补程序解决了在通过REST API创建发运期间订单状态更改不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972：通过REST API创建的订单状态错误装运

MDVA-30972修补程序解决了在通过REST API创建发运期间订单状态更改不正确的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.7。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0到2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当通过REST API从管理员为订单创建部分发运时，具有 *可疑欺诈* 订单状态，订单状态已更改为 *正在处理*. 它应该留在 *可疑欺诈*.

<u>先决条件</u>：

* 设置PayPal EC或其他在线支付方式。
* 设置了REST API的集成。

<u>重现问题的步骤</u>：

1. 创建包含两个或多个项目的订单。
1. 登录 **管理员** > **销售** > **订购**. 打开您刚刚创建的订单。
1. 在订单详情页面上，向下滚动至 **订单总计**. 单击 **状态** 下拉并选择 *可疑欺诈*. 然后单击 **提交评论** 按钮。
1. 检查订单是否具有 *可疑欺诈* 状态。
1. 使用REST API从订单中创建一个物料的发运：

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. 再次在“管理员”中打开订单并检查其状态。

<u>预期结果</u>：

* 订单状态= *可疑欺诈*.
* 如果从管理员创建相同的装运，则订单状态不会更改。

<u>实际结果</u>：

订单状态= *正在处理*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
