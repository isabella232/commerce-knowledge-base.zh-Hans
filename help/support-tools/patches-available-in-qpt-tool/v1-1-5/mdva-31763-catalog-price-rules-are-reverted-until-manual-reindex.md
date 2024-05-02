---
title: 'MDVA-31763：将还原目录价格规则，直到手动重新索引为止'
description: MDVA-31763修补程序解决了在手动重新索引之前恢复目录价格规则的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-31763。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763：将还原目录价格规则，直到手动重新编入索引

MDVA-31763修补程序解决了在手动重新索引之前恢复目录价格规则的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.5。 修补程序ID为MDVA-31763。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.3.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

时间 `catalogrule_product` 部分索引器是在可配置产品上执行的，目录规则消失了。

<u>重现问题的步骤</u>：

1. 登录到管理员后端。
1. 转到 **商店** > **属性** > **产品** 并搜索“制造商”属性。
   * 添加几个选项并将“用于促销规则条件”设置为 *是*.
1. 转到 **商店** > **属性** > **属性集**.
   * 选择默认属性集并添加“manufacturer”属性。
1. 创建具有几个变体的可配置产品。
1. 为之前创建的可配置产品设置“制造商”属性值。
1. 创建目录规则：
   * 活动=是
   * 网站=主网站
   * 客户组=未登录
   * 条件：制造商= \&lt;selected value=&quot;&quot; for=&quot;&quot; configurable=&quot;&quot; product=&quot;&quot;>
   * 操作：任何折扣
1. 执行完整索引。
1. 检查PDP上的产品价格，并确保价格正确。
1. 更新已创建的可配置产品的“权重”属性。
1. 检查PDP上的产品价格。

<u>预期结果</u>：

在部分重新索引期间，不会删除针对可配置产品设置的目录价格规则。

<u>实际结果</u>：

对可配置产品设置的目录价格规则在部分重新索引期间消失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
