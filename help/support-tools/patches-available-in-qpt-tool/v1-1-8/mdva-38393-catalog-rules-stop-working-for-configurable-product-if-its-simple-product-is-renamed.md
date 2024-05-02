---
title: 'MDVA-38393：如果简单产品被重新命名，目录规则将停止为可配置产品工作'
description: MDVA-38393修补程序修复了当简单产品被重新命名时，目录规则停止为可配置产品工作的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8后，即可使用此修补程序。 修补程序ID为MDVA-38393。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: a20856c4-8aff-427b-a404-7afe706be06f
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38393：如果对可配置产品的简单产品进行了重新命名，则目录规则将停止对其工作

MDVA-38393修补程序修复了当简单产品被重新命名时，目录规则停止为可配置产品工作的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.8。 修补程序ID为MDVA-38393。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.3.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果对可配置产品的简单产品进行了重新命名，则目录规则将停止使用该产品。

<u>重现问题的步骤</u>：

1. 使用关联的简单产品创建可配置产品。
1. 创建类别。
1. 仅将可配置产品分配给新类别。
1. 创建新目录规则：
   * 条件=类别包含\&lt;new category=&quot;&quot; id=&quot;&quot;>
   * 操作= 50%折扣
   * 活动=是
1. 执行重新索引。
1. 检查前端的可配置产品（应应用折扣）。
1. 查看 `catalogrule_product` 表（简单产品应当有折扣）。
1. 转到管理员并更改简单产品的名称。 这会将记录添加到 `catalogrule_product_cl` 表格。
1. 执行cron或 `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1` 命令。
1. 查看 `catalogrule_product` 表格。

<u>预期结果</u>：

可配置产品具有折扣。

<u>实际结果</u>：

* 中缺少为简单产品创建的折扣记录 `catalogrule_product` 表格。
* 前端的可配置产品具有完整的原始价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
