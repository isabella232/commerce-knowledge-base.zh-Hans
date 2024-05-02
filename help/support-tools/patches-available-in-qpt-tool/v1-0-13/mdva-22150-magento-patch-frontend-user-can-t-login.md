---
title: “MDVA-22150 Adobe Commerce修补程序：前端用户无法登录”
description: MDVA-22150修补程序解决了前端用户在使用优惠券中止购买后无法登录的问题。 当前端用户在完成购买之前被禁用的产品上使用优惠券代码时，会发生这种情况。 结果是前端用户无法再登录并收到503错误。 此问题的另一个影响是，在管理员中管理客户的购物车的功能停止工作。
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# MDVA-22150 Adobe Commerce修补程序：前端用户无法登录

MDVA-22150修补程序解决了前端用户在使用优惠券中止购买后无法登录的问题。 当前端用户在完成购买之前被禁用的产品上使用优惠券代码时，会发生这种情况。 结果是前端用户无法再登录并收到503错误。 此问题的另一个影响是，在管理员中管理客户的购物车的功能停止工作。

此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.13。 请注意，Adobe Commerce版本2.3.4中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.2

**与Adobe Commerce版本兼容：** 云基础架构上的Adobe Commerce和Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤：</u>

1. 登录到管理员并创建可配置的产品。
1. 转到 **购物车规则**，并创建一个带有折扣的优惠券代码。
1. 在前端创建客户帐户。
1. 将产品添加到购物车，执行结账过程，然后输入优惠券。
1. 输入优惠券后，请勿提交订单，但会中止订单并注销。
1. 返回管理员并禁用整个可配置产品。

<u>预期结果：</u>

产品未显示在店面的购物车中，或随相应的错误消息一起显示，说明产品已按预期禁用。

<u>实际结果：</u>

* 尝试重新登录到前端时，您将陷入无限循环（这最终会在一段时间后显示异常）。
* 在管理员中管理客户的购物车的功能停止工作。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
