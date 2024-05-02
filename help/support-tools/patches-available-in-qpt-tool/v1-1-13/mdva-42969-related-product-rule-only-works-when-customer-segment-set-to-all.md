---
title: 'MDVA-42969：仅当客户区段设置为全部时，相关产品规则才有效'
description: MDVA-42969修补程序修复了相关产品规则仅在客户区段设置为全部时才有效的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-42969。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 2877ba7a-2681-4de2-9c37-228de232424f
feature: Customer Service, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42969：仅当客户区段设置为全部时，相关产品规则才有效

MDVA-42969修补程序修复了相关产品规则仅在客户区段设置为全部时才有效的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.13。 修补程序ID为MDVA-42969。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

仅当客户区段设置为全部时，相关产品规则才有效。

<u>重现问题的步骤</u>：

1. 转到 **商店** > **配置** > **目录** > **基于规则的产品关系** 并设置 **显示相关产品** = **仅基于规则**.
1. 转到 **客户** > **区段** 并创建新区段： **应用于** = **访客和注册客户**.
1. 转到 **营销** > **相关产品规则** 并创建新规则。

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. 打开店面中的匹配产品，验证是否显示了要显示的产品。
1. 修改在步骤3中创建的规则并设置 **客户区段** = **特定** > **区段** 从第二步开始。
1. 打开店面上的匹配产品。

<u>预期结果</u>：

基于规则的相关产品会显示在店面上，以供产品上的访客使用，因为客户区段是使用以下配置创建的：

**应用于** = **访客和注册客户**

<u>实际结果</u>：

不显示相关产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
