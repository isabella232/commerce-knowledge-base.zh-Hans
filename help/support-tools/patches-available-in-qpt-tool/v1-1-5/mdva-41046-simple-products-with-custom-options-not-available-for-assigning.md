---
title: 'MDVA-41046：无法分配具有自定义选项的简单产品'
description: MDVA-41046修补程序解决了具有自定义选项的简单产品无法分配给可配置/分组产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41046。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 01229a69-c72a-4189-9be5-1761073b74ee
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-41046：具有自定义选项的简单产品不可用于分配

MDVA-41046修补程序解决了具有自定义选项的简单产品无法分配给可配置/分组产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.5。 修补程序ID为MDVA-41046。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有自定义选项的简单产品无法分配给可配置/分组的产品。

<u>重现问题的步骤</u>：

1. 创建一个带有可自定义选项的简单产品，并为可配置属性设置一个值。
   * 使用 *颜色* 作为可配置的属性，然后选择 *黄色* 作为颜色值。
1. 保存简单产品。
1. 现在，转到创建可配置产品页面。
1. 浏览“创建配置”向导，并确保选择 *黄色* 作为属性颜色。
1. 不保存可配置产品，从选择下拉列表中选择“选择其他产品”选项。
1. 这将打开按颜色属性黄色过滤的产品网格。 现在，选择之前使用可自定义选项创建的简单产品。
1. 保存可配置产品。

<u>预期结果</u>：

带有自定义选项的简单产品可用于在步骤6中进行分配（在网格中可见）。

<u>实际结果</u>：

配置部分为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
