---
title: 'MDVA-34847：customer_grid_flat表慢查询'
description: MDVA-34847修补程序解决了“customer_grid_flat”表上查询缓慢的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: e91cb86d-83cd-4267-a132-64465a57da7f
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-34847：customer_grid_flat表查询缓慢

MDVA-34847修补程序解决了在 `customer_grid_flat` 表格。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.16。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.3

**与Adobe版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

查询速度较慢 `customer_grid_flat` 表格。

<u>重现问题的步骤</u>：

1. 创建具有自定义范围的管理员用户(示例：已设置 **GWS** = *0，* 并选择现有的默认网站 **ID** = *1*)。
1. 创建任何产品和类别项目。
1. 从前端下订单。
1. 以新用户身份登录到管理员。
1. 转到Sales网格(**销售>订单**)。
1. 检查SQL查询是否已发送到DB（数据库）。

<u>预期结果</u>：

Admin GWS扩展应使用

```sql
int
```

值

```sql
website_id
```

在SQL条件中，如预期：

```sql
main_table.website_id IN (1)
```

<u>实际结果</u>：

管理员GWS扩展添加了一个条件

```sql
website_id
```

值是

```sql
string
```

，例如：

```sql
main_table.website_id IN ('1')
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
