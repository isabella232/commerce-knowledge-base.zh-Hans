---
title: 'MDVA-41236：无法为产品创建新计划更新或编辑现有计划更新'
description: MDVA-41236修补程序修复了以下问题：如果之前删除了“结束日期”，则用户无法为产品创建新的计划更新或编辑现有的计划更新。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41236。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236：无法为产品创建新的或编辑现有的计划更新

MDVA-41236修补程序修复了以下问题：如果之前删除了“结束日期”，则用户无法为产品创建新的计划更新或编辑现有的计划更新。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.1.5。 修补程序ID为MDVA-41236。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果用户之前删除了“结束日期”，则无法创建新计划或编辑产品的现有计划。

<u>重现问题的步骤</u>：

1. 创建状态设置为的产品 *disable*.
1. 添加计划更新以启用此产品。
   * 添加未来的开始和结束日期。
1. 通过删除 **结束日期**.
1. 再次编辑计划并尝试添加 **结束日期**. 将发生错误。
1. 刷新页面，然后再次转到 **编辑计划的更新**.
1. 单击 **从更新中删除** > **删除更新**.
1. 现在，您不应在产品编辑页面顶部看到计划更新。
1. 尝试创建与上一个持续时间重叠的新计划更新。

<u>预期结果</u>：

* 步骤4中没有错误。 由于计划尚未激活，管理员能够更新计划更新而不会出现任何错误。
* 管理员用户能够删除以前的更新并创建新更新。

<u>实际结果</u>：

用户将收到以下错误消息：

*错误：此时间范围内已存在将来更新。 请设置其他范围，然后重试。*


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
