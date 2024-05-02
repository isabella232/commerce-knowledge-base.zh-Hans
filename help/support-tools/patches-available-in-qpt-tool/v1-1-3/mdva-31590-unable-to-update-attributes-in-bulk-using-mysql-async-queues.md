---
title: 'MDVA-31590：无法使用MySQL异步队列批量更新属性'
description: MDVA-31590修补程序解决了用户无法使用MySQL异步队列批量更新属性的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3后，即可使用此修补程序。 修补程序ID为MDVA-31590。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 57db28dd-a739-4a77-927d-6339af4fa4a6
feature: Attributes, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---

# MDVA-31590：无法使用MySQL异步队列批量更新属性

MDVA-31590修补程序解决了用户无法使用MySQL异步队列批量更新属性的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.3。 修补程序ID为MDVA-31590。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.0

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0-2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户无法使用MySQL异步批量更新属性。

<u>重现问题的步骤</u>：

1. 在后端的产品网格上，执行批量操作以更新几个产品的属性值。
   * 检查产品并选择 **更新属性** （从操作下拉菜单中）。
1. 设置所需属性的值并将产品分配给网站并保存。
1. 重新加载页面后，它将显示如下消息：
   *任务“更新N个选定产品的属性”：已计划更新1个项目。*
1. 等待几秒钟，然后重新加载后端页面。

<u>预期结果</u>：

1. 该页面将显示成功的更新消息，如下所示： *已成功更新1个项目。*
1. 相关产品的属性值已更新。
1. 在数据库中，会在两个数据库中创建新记录 `magento_bulk` 表格和 `magento_operation` 表（与批量相关的操作）。
1. 新记录创建于 `queue_message` 表（与队列相关） `product_action_attribute.update` 和/或 `product_action_attribute.website.update`)。
1. `queue_message_status` 表具有状态为“4”的记录。
1. 中没有错误 `system.log`.

<u>实际结果</u>：

1. 该页面仍会显示如下消息：
   *任务“更新N个选定产品的属性”：已计划更新1个项目。*
1. 产品的属性值会更新。
1. 新记录创建于 `message_bulk` 表，但中没有关联记录 `magento_operation` 表格。
1. 新记录创建于 `queue_message` 和 `queue_message_status` 表格。
1. `queue_message_status` 表记录有错误状态（状态值“6”）。
1. `system.log` 包含与以下内容类似的错误：
   *main.CRITICAL：消息已被拒绝： SQLSTATE[23000]：完整性约束违规： 1048列“operation_key”不能为null，查询为： INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}})值(？，？，？，？，？，？，？，？，？，？) [][]*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
