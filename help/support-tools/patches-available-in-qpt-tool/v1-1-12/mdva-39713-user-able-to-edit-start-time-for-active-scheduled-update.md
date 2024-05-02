---
title: 'MDVA-39713：用户能够编辑活动计划更新的开始时间'
description: MDVA-39713修补程序修复了用户能够编辑活动计划更新的开始时间的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-39713。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713：用户能够编辑活动计划更新的开始时间

MDVA-39713修补程序修复了用户能够编辑活动计划更新的开始时间的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.12。 修补程序ID为MDVA-39713。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.3.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.3.6

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户能够编辑活动计划更新的开始时间。

<u>重现问题的步骤</u>：

1. 创建新的CMS页面。
1. 选择 **计划新更新** 并设置 **开始日期** 到当前+1分钟。
1. 通过运行命令激活计划更新 `bin/magento cron:run --group=staging` 在本地环境中。 等待几分钟，然后检查计划是否处于活动状态。
1. 一旦调度处于活动状态，请刷新该页。
1. 单击 **查看/编辑** （在计划更改部分）。
1. 通过添加+2分钟来编辑时间并保存更改。
1. 保存CMS页面。
1. 再次运行以下命令： `bin/magento cron:run --group=staging`.
1. 单击 **查看/编辑** 计划的更新的。

<u>预期结果</u>：

用户无法编辑活动计划更新的开始时间。

<u>实际结果</u>：

用户收到错误，例如 *已存在具有相同ID“11”的项目(Magento\Cms\Model\Page)。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
