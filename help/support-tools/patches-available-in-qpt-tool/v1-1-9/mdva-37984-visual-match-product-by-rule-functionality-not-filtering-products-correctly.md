---
title: 'MDVA-37984：应用暂存更新时，可视化促销程序无法正常工作'
description: MDVA-37984修补程序解决了在应用暂存更新时，可视化促销器的“按规则匹配产品”功能无法正确筛选产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-37984。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: d806b94c-3b22-4d4c-8afb-7b57a0ebfe46
feature: Categories, Merchandising, Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-37984：应用暂存更新时，可视化促销程序无法正常工作

MDVA-37984修补程序解决了在应用暂存更新时，可视化促销器的“按规则匹配产品”功能无法正确筛选产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.9。 修补程序ID为MDVA-37984。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

应用暂存更新时，可视促销器的“按规则匹配产品”功能无法正确筛选产品。

<u>重现问题的步骤</u>：

1. 为任何现有产品创建计划更新。
   * 为设置不同的值 `entity_id` 和 `row_id`.
1. 创建一个新的可配置产品，然后创建一个简单的产品(因此，该新产品 `entity_id` 和 `row_ids` 也不一样)。
   * 为了更便于复制问题，请为简单产品设置可区分的数量值，例如5000。
1. 转到类别> **类别中的产品** 并启用 **按规则匹配产品**.
1. 现在，选择“数量”作为属性，“大于”作为运算符，“4500”作为值。
1. 单击 **保存**.

<u>预期结果</u>：

将列出新创建的可配置产品。

<u>实际结果</u>：

新创建的可配置产品未列出。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
