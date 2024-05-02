---
title: 'MDVA-26639：新订单确认电子邮件模板中没有订单项'
description: MDVA-26639修补程序修复了在创建新订单时，确认电子邮件模板中缺少订单项的问题。
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639：新订单确认电子邮件模板中没有订单项

MDVA-26639修补程序修复了在创建新订单时，确认电子邮件模板中缺少订单项的问题。

此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.20。 修补程序ID为MDVA-26639。 请注意，Adobe Commerce 2.3.6中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.3-p1

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 转到 **商店** > **配置** > **销售** > **销售电子邮件** > **新订单确认** 并选择 **模板：新建装货单**.
1. 转到 **销售** > **订单：选择订单**，然后转到 **信息**，并选择 **发送邮件**.

<u>预期结果</u>：

订单项目按预期显示在客户订单电子邮件中。

<u>实际结果</u>：

客户订单电子邮件中缺少订单项目。 如果您创建新模板并选择模板“新订单”或“新订单(Luma)”，则同样适用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
