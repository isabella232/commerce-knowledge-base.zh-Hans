---
title: 'MDVA-43983：设置为“单独不可见”的产品将显示在搜索结果中'
description: MDVA-43983修补程序解决了设置为“不可见”的产品仍然显示在目录高级搜索结果中的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-43983。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983：设置为“单独不可见”的产品将显示在搜索结果中

MDVA-43983修补程序解决了设置为“不可见”的产品仍然显示在目录高级搜索结果中的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.14。 修补程序ID为MDVA-43983。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

设置为“单独不可见”的产品仍会显示在目录高级搜索结果中。

<u>重现问题的步骤</u>：

1. 创建属性，使用 **商店所有者的目录输入类型** 作为 **下拉列表** 或 **可视色板** （例如，颜色）。
1. 设置 **在搜索中使用** 作为 **是** 和 **在高级搜索中可见** 作为 **是**.
1. 添加一些属性选项。
1. 创建产品，使用 **可见性** 作为 **无法单独显示**.
1. 指定颜色属性选项。
1. 转到 **目录高级搜索** 在店面上写了那篇文章。
1. 从“颜色”属性字段中仅选择“颜色”属性选项，并将其余字段留空或保持原样。
1. 提交高级搜索表单。
1. 观察搜索结果。

<u>预期结果</u>：

设置为“不可见”的产品不会出现在目录高级搜索结果中。

<u>实际结果</u>：

设置为“单独不可见”的产品将显示在目录高级搜索结果中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
