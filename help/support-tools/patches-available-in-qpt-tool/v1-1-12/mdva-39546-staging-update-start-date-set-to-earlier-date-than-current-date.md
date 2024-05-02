---
title: 'MDVA-39546：可以将暂存更新开始日期设置为早于当前日期的日期'
description: MDVA-39546修补程序修复了将暂存更新的开始日期设置为比当前日期更早的日期的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-39546。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: a66b5d83-2eba-45a6-9eb9-4ba39ef20e16
feature: Staging
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MDVA-39546：可以将暂存更新开始日期设置为早于当前日期的日期

MDVA-39546修补程序修复了将暂存更新的开始日期设置为比当前日期更早的日期的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.12。 修补程序ID为MDVA-39546。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可以将暂存更新的开始日期设置为早于当前日期的日期。

<u>重现问题的步骤</u>：

1. 为具有未来开始日期的产品计划新更新。
1. 编辑更新来源 **内容** > **内容暂存** > **仪表板** 并使用更早的日期更新开始日期并保存更改。
1. 重新打开上述更新。

<u>预期结果</u>：

以前的数据会显示在编辑表单中。

<u>实际结果</u>：

表单中的值缺失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
