---
title: “MDVA-24201：目录价格规则不起作用”
description: MDVA-24201修补程序解决了数据库中的活动目录价格规则不适用于前端的问题。
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201：目录价格规则不起作用

MDVA-24201修补程序解决了数据库中的活动目录价格规则不适用于前端的问题。

此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.14。 请注意，Adobe Commerce版本2.3.5中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.3

**与Adobe Commerce版本兼容：** 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.3.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

安装包含示例数据的新Magento实例。

<u>重现问题的步骤</u>：

1. 登录 **管理面板** > **营销** > **目录价格规则** > **添加新规则**&#x200B;进行以下设置：
   1. 设置 **规则名称**.
   1. 设置 **活动** = *不适用。*
   1. 设置条件： **类别** = *4*. （例如：包）
   1. 设置操作：
      1. 设置 **应用为**   **原始内容的百分比**.
      1. 设置 **折扣金额** = *10*.
      1. 保存，然后继续编辑。
   1. 单击 **计划新更新**：
      * 设置 **规则名称**.
      * 设置 **活动** = *是*.
      * 保存。
1. 转到后端并运行：

   `php    bin/magento cron:run`

<u>预期结果</u>：

按照目录价格的规定，第四类袋装产品的价格按原价的百分之十降价。

<u>实际结果</u>：

即使目录价格规则处于活动状态，也不会发生价格更改。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
