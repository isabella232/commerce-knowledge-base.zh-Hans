---
title: 'MDVA-38468：保存CMS页面时收到错误消息'
description: “MDVA-38468 Adobe Commerce修补程序修复了用户在保存CMS页面时收到错误消息：*具有相同ID“PAGE_ID”的项目已存在*的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26后，即可使用此修补程序。 修补程序ID为MDVA-38468。 请注意，Adobe Commerce 2.3.6中已修复此问题。'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468：保存CMS页面时收到错误消息

MDVA-38468 Adobe Commerce修补程序修复了用户收到错误消息的问题： *已存在具有相同ID“PAGE_ID”的项目，* 保存CMS页面时。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.26。 修补程序ID为MDVA-38468。 请注意，Adobe Commerce 2.3.6中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
云基础架构上的Adobe Commerce 2.3.2-p2

**与Adobe Commerce版本兼容：**
Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.2-2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在尝试保存CMS页面时，您会收到以下错误消息： *已存在具有相同ID“PAGE_ID”的项目。*

<u>重现问题的步骤</u>：

1. 创建新网站+商店+商店回顾。
1. 再创建一个网站+商店+商店回顾。
1. 转到 **内容** > **层级** >将任何现有的CMS页添加到层次结构树。
1. 转到 **内容** > **页面** > **添加新页面**：
   * 添加任何标题。
   * 在“网站中的页面”部分中，分配给两个已创建的审核。
   * 在“层次结构”部分中，分配给任何类别。
   * **保存并继续编辑**.

<u>预期结果</u>：

保存页面时，不会出现任何错误。

<u>实际结果</u>：

页面已保存，但您会收到以下错误消息： *已存在具有相同ID“PAGE_ID”的项目(Magento\VersionsCms\Model\Hierarchy\Node)。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
