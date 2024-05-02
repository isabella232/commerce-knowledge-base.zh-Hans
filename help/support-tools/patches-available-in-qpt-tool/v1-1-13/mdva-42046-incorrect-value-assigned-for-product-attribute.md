---
title: 'MDVA-42046：为产品属性分配的值不正确'
description: MDVA-42046修补程序修复了在更新具有日期输入字段的产品时，为产品属性分配的值不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-42046。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 837f5582-849c-43a3-ae02-87f71fb96061
feature: Attributes, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-42046：为产品属性分配的值不正确

MDVA-42046修补程序修复了在更新具有日期输入字段的产品时，为产品属性分配的值不正确的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.13。 修补程序ID为MDVA-42046。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.3.5-p2和2.4.0 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用保存产品后 `news_from_date` 和/或 `news_to_date` 这两个字段的值会重置为默认值。

<u>重现问题的步骤</u>：

1. 创建一个简单的产品。
1. 导出在第一步中创建的产品。
1. 在导出的CSV文件中，将一些值放入 `news_from_date` 和 `news_to_date` 字段。 例如，2021-05-15和2021-06-18。
1. 使用修改后的CSV文件导入产品。
1. 向产品网格中添加其他列“将产品设置为新的开始日期”和“将产品设置为新的结束日期”。
1. 打开产品的编辑页面，在不进行任何更改的情况下，单击 **保存**.
1. 返回产品网格，然后检查产品的数据。

<u>预期结果</u>：

“将产品设置为新的开始日期”和“将产品设置为新的结束日期”都与保存前相同。

<u>实际结果</u>：

* “将产品设置为新起始日期”和“将产品设置为新起始日期”列中的值已更改。

* “将产品设置为新起始日期”列显示当前日期，“将产品设置为新起始日期”列为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
