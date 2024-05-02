---
title: 'MDVA-43491：通过CSV导入时，基本图像标签未更新'
description: MDVA-43491修补程序修复了在通过多商店网站的CSV文件导入时，“base_image_label”不会更新的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-43491。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491：通过CSV导入时，基本图像标签未更新

MDVA-43491修补程序修复了 `base_image_label` 通过多商店网站的CSV文件导入时，不会更新。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.13。 修补程序ID为MDVA-43491。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此 `base_image_label` 为多商店网站使用CSV文件导入时，不会更新。

<u>先决条件</u>：

一个或多个现有的非默认网站、商店和商店视图。

<u>重现问题的步骤</u>：

1. 创建新产品。

   * 上传图像。
   * 将产品分配给新创建的网站。

1. 将产品导出为CSV。
1. 更新 `base_image_label` ，方法是复制CSV文件的默认行。
1. 导入CSV文件。 它会正确更新每个商店的标签，这可以在 **图像和视频** 选项卡。
1. 再次导出CSV文件并更新 `base_image_label` 具有不同值的列。
1. 再次导入CSV文件。
1. 在“管理员”中打开产品，并检查每个商店视图的标签是否已更新。

<u>预期结果</u>：

替代文本（图像标签）将根据CSV文件使用特定于存储的值更新。

<u>实际结果</u>：

替换文本（图像标签）未更新为 `base_image_label` CSV文件中的值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
