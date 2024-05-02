---
title: “MDVA-34680：客户帐户未在客户网格中正确过滤”
description: MDVA-34680修补程序修复了在00:00 UTC之后创建的客户帐户未在客户网格中正确过滤的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26后，即可使用此修补程序。 修补程序ID为MDVA-34680。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 2e506d7a-8cde-41eb-84b2-1a5ff8015428
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-34680：客户网格中的客户帐户未正确过滤

MDVA-34680修补程序修复了在00:00 UTC之后创建的客户帐户未在客户网格中正确过滤的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.26。 修补程序ID为MDVA-34680。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.4.1和2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.6-2.3.7和2.4.1-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当客户帐户在00:00 UTC之后创建，并且您尝试按该日期过滤帐户时，它不会返回此客户。

<u>重现问题的步骤</u>：

1. 转到 **商店** > **配置** > **常规** 并将时区设置为东部标准 [美国/纽约].
1. 在00:00 UTC后创建新的客户帐户。
1. 转到 **客户** > **所有客户** 并按今天的日期过滤帐户。

<u>预期结果</u>：

客户帐户筛选器显示今天00:00 UTC之后创建的新帐户。

<u>实际结果</u>：

客户帐户筛选器不显示今天创建的新帐户。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
