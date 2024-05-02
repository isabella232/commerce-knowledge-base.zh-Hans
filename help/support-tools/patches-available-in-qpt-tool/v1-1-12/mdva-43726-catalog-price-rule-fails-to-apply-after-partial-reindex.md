---
title: 'MDVA-43726：对目录价格规则进行部分重新索引后无法应用'
description: MDVA-43726修补程序修复了在部分重新索引后无法应用基于存储级别属性匹配的目录价格规则的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43726。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726：部分重新索引后无法应用目录价格规则

MDVA-43726修补程序修复了在部分重新索引后无法应用基于存储级别属性匹配的目录价格规则的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.12。 修补程序ID为MDVA-43726。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在部分重新索引后，无法应用基于存储级别属性匹配的目录价格规则。

<u>重现问题的步骤</u>：

1. 将索引器模式设置为按计划运行。
1. 创建两个可配置的产品属性。 例如：颜色（可视样本）和大小（文本样本）。
1. 使用步骤2中创建的两个属性创建可配置产品。
1. 创建产品后，创建 **是/否** 键入attribute并使其在规则条件中可见。
1. 将此属性添加到默认属性集。
1. 创建在此属性设置为时应用的目录价格规则 **是**.
1. 打开与可配置产品相关的简单产品之一。
1. 更改范围以存储视图并将属性值更新为 **是**.
1. 运行 `CRON` 看看前方的价格。
1. 运行完全重新索引。 再次检查前端的价格。
1. 更新可配置产品类别。
1. 运行 `CRON` 再去前门检查一下价格。

<u>预期结果</u>：

无需使用增量索引器完全重新索引，目录规则即可正确应用。

<u>实际结果</u>：

如果不运行完整的重新索引，则不会应用目录规则。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
