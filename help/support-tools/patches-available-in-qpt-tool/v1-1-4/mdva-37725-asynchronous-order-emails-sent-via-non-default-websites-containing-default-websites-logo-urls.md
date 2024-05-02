---
title: “MDVA-37725：通过非默认站点发送的电子邮件包含默认站点的徽标URL”
description: MDVA-37725修补程序修复了以下问题：通过包含默认网站的徽标URL的非默认网站发送异步订单电子邮件。
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725：通过非默认站点发送的电子邮件包含默认站点的徽标URL

>[!WARNING]
>
> 已弃用MDVA-37725修补程序。

MDVA-37725修补程序修复了以下问题：通过包含默认网站的徽标URL的非默认网站发送异步订单电子邮件。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.1.4。 修补程序ID为MDVA-37725。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

异步订单电子邮件通过包含默认网站徽标URL的非默认网站发送。

<u>先决条件</u>：

1. 必须已创建第二个网站/商店/商店视图。
1. **异步发送** 必须从以下位置启用配置： **商店** > **设置** > **配置** > **销售** > **销售电子邮件** > **常规设置**.
1. **将存储代码添加到URL** 为便于访问辅助网站，已打开配置 **商店** > **设置** > **配置** > **URL选项**.

<u>重现问题的步骤</u>：

1. 从第一家和第二家商店下订单。
1. 运行cron以发送销售电子邮件。
1. 检查来自第二个网站的电子邮件。

<u>预期结果</u>：

电子邮件的徽标URL包含第二个网站的URL。

<u>实际结果</u>：

电子邮件的徽标URL包含默认网站的URL。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
