---
title: 'MDVA-31343修补程序：计划更新删除类别的主体类'
description: MDVA-31343修补程序修复了在计划更新期间删除为类别分配的布局正文CSS类的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 Adobe Commerce 2.4.2中计划修复此问题。
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-31343修补程序：计划更新删除类别的主体类

MDVA-31343修补程序修复了在计划更新期间删除为类别分配的布局正文CSS类的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.7。 Adobe Commerce 2.4.2中计划修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.4 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

布局正文类在计划更新后从类别中删除。

<u>重现问题的步骤</u>：

1. 在Commerce管理员中，创建一个类别。
1. 设置 **布局** = *类别 — 全宽* 在 **设计** 部分。
1. 保存类别。
1. 转到类别前端页面。 在页面源中，注意

   ```css
   page-layout-category-full-width
   ```

   css类。
1. 下 **目录** > **类别**，单击 **计划新更新** 在 *计划的更改* 部分。
1. 等待计划更新开始，运行cron并刷新缓存。
1. 转到前端上的类别页面并检查页面源。

<u>预期结果</u>：

在页面正文中，您会看到

```css
page-layout-category-full-width
```

css类。

<u>实际结果</u>：

在页面正文中，您会看到

```css
page-layout-2columns-left
```

CSS类，该类是类别页面的默认类。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
