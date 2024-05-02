---
title: 'MDVA-36021：用户在打开订单详细信息时收到错误消息'
description: MDVA-36021修补程序解决了用户在尝试打开订单详细信息时收到*成员函数getId()*调用错误消息的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1后，即可使用此修补程序。 修补程序ID为MDVA-36021。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 73b1f3c6-5dc4-48e4-8f3f-681be84f7638
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-36021：用户在打开订单详细信息时收到错误消息

MDVA-36021修补程序解决了以下问题： *调用成员函数getId()* 尝试打开订单详细信息时出现错误消息。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.1。 修补程序ID为MDVA-36021。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.4.1、2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当用户尝试打开订单详细信息时，管理员的订单详细信息页面上会显示以下错误消息： *report.CRITICAL：错误：在/magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml：62中调用数组上的成员函数getId()*.

<u>先决条件</u>：

系统应具有税设置和具有特定税率的订单。

<u>重现问题的步骤</u>：

1. 登录到Commerce管理员。
1. 转到 **销售** > **订购** > **未结订单**.

<u>预期结果</u>：

订单打开时没有出现错误。

<u>实际结果</u>：

您会收到类似于以下内容的错误消息： *report.CRITICAL：错误：在/magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml：62中调用数组上的成员函数getId()*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
