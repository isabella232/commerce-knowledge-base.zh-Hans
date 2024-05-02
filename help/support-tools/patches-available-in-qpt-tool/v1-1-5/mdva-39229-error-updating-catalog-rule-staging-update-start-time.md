---
title: 'MDVA-39229：更新目录规则暂存更新开始时间时出错'
description: MDVA-39229修补程序修复了用户在更新目录规则暂存更新的开始时间后收到错误的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-39229。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229：更新目录规则暂存更新开始时间时出错

MDVA-39229修补程序修复了用户在更新目录规则暂存更新的开始时间后收到错误的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.1.5。 修补程序ID为MDVA-39229。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

Adobe Commerce（所有部署方法） 2.3.4-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户更新目录规则暂存更新的开始时间后收到错误。

<u>重现问题的步骤</u>：

1. 创建目录价格规则。
1. 创建并执行任何暂存更新。
1. 运行查询并验证是否已创建暂存标志。


   `select * from flag;`


1. 创建新的暂存更新，以在5分钟后开始。
1. 打开 **内容** > **暂存** > **仪表板** > **新建更新** 并延迟开始时间一分钟。
1. 等六分钟。
1. 运行cron。

<u>预期结果</u>：

更新开始时间已更改，并且应用了更新。 旧更新将从 `staging_update` 表格。

<u>实际结果</u>：

用户收到以下错误：

*report.ERROR： Cron作业staging_synchronize_entities_period有错误：无法删除活动更新。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
