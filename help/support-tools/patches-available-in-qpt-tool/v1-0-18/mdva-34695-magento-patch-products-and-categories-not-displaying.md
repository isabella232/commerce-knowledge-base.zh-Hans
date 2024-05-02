---
title: 'MDVA-34695：未显示产品和类别'
description: MDVA-34695修补程序解决了在“管理员”的类别网格中无法显示产品和类别的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18后，即可使用此修补程序。 修补程序ID为MDVA-34695。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 0c2e50c1-648b-480a-a768-72af721950d8
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-34695：未显示产品和类别

MDVA-34695修补程序解决了在“管理员”的类别网格中无法显示产品和类别的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.18。 修补程序ID为MDVA-34695。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.4

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.0-2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

以下项的负值 `children_count` 在删除类别之后显示在数据库中。

<u>重现问题的步骤</u>：

1. 登录到管理员后端。
1. 导航到 **“目录”>“类别”**.
1. 单击 **添加子类别**.
1. 设置 **类别名称** = *父级1*，然后保存。
1. 单击 **添加子类别**.
1. 设置 **类别名称** = *子项1*，然后保存。
1. 单击 **添加子类别**.
1. 设置 **类别名称** = *子项2*，然后保存。
1. 单击 **添加子类别**.
1. 设置 **类别名称** = *子项3*，然后保存。 此时，此类别应具有级别= *5*.
1. 单击 **子项1** 类别。
1. 删除类别。

<u>预期结果</u>：

类别网格会按预期显示产品和类别。

<u>实际结果</u>：

类别网格为空。 查看 `catalog_category_entity` 表中的数据。 请注意 `children_count` 变为负值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
