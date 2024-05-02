---
title: 'MDVA-35847：公司用户表单不起作用'
description: MDVA-35847修补程序解决了公司用户表单不起作用并在前端返回500错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-35847。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 1a3f4a61-0c21-460a-ae48-e792d03ed805
feature: B2B, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-35847：公司用户表单不起作用

MDVA-35847修补程序解决了公司用户表单不起作用并在前端返回500错误的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.19。 修补程序ID为MDVA-35847。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.1 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

已安装Adobe Commerce B2B。

<u>重现问题的步骤</u>：

1. 转到 **商店** > **属性** > **客户**，并创建新的自定义客户属性：

   * 输入类型= *日期*
   * 在店面显示= *是*
   * 排序顺序= *0*
   * 要在中使用的Forms = *所有表单*

1. 创建新公司。
1. 以公司管理员身份登录前端。
1. 转到公司用户部分。

<u>预期结果</u>：

公司用户表单会正常加载。

<u>实际结果</u>：

公司用户表单未加载并返回500错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
