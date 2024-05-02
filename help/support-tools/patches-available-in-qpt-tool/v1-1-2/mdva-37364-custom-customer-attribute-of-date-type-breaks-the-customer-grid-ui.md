---
title: 'MDVA-37364：日期类型的自定义客户属性破坏网格UI'
description: MDVA-37364修补程序解决了日期类型的自定义客户属性破坏客户网格UI的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-37364。 请注意，该问题计划在Adobe Commerce版本2.4.4中修复。
exl-id: d25baabf-45eb-403c-9f88-9c2448cc7b49
feature: Attributes, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37364：日期类型的自定义客户属性破坏了网格UI

MDVA-37364修补程序解决了日期类型的自定义客户属性破坏客户网格UI的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.2。 修补程序ID为MDVA-37364。 请注意，该问题计划在Adobe Commerce版本2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0-2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

日期类型的自定义客户属性破坏了客户网格UI。

<u>重现问题的步骤</u>：

1. 创建具有日期类型的自定义属性：
   * 转到 **商店** > **属性** > **添加属性**.
   * 将“输入类型”设置为“日期”。
   * 将“添加至列选项”设置为“是”。
   * 保存属性。
1. 转到 **管理员** > **客户** > **所有客户**.
   * 将新添加的自定义属性从列选项添加到网格。
1. 创建/编辑客户并设置已创建的自定义日期属性字段的值。
1. 保存、重新索引和清除缓存。
1. 转到 **客户** > **所有客户**.
   * 检查客户网格。

<u>预期结果</u>：

管理客户网格显示包括新日期自定义属性在内的所有数据，而不破坏客户网格UI。

<u>实际结果</u>：

管理客户网格UI已损坏。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
