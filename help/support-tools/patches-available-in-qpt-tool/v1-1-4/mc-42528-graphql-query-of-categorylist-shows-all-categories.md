---
title: 'MC-42528：categoryList的GraphQL查询显示所有类别'
description: MC-42528修补程序解决了以下问题：当特定类别的浏览类别设置为“拒绝”时，“categoryList”的GraphQL查询会返回已分配和未分配的类别。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4后，即可使用此修补程序。 修补程序ID为MC-42528。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528：categoryList的GraphQL查询显示所有类别

MC-42528修补程序解决了以下问题的GraphQL查询： `categoryList` 将特定类别的浏览类别设置为“拒绝”时，会返回已分配和未分配的类别。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.4。 修补程序ID为MC-42528。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL查询 `categoryList` 返回已分配和未分配的类别。

<u>重现问题的步骤</u>：

1. 创建两个类别：CAT1和CAT2，并为每个类别分配少量产品。
1. 创建专用共享目录。
1. 创建公司用户并将其分配给创建的共享目录。
1. 将CAT1分配给自定义目录，并将专用目录的客户组的类别权限设置为“允许”浏览类别。
1. 将CAT2的类别权限设置为“拒绝”浏览类别，以访问私有目录的客户组。
1. 运行 `categoryList` 或 `categories` GraphQL查询作为公司用户。

<u>预期结果</u>：

响应中只显示CAT1。

<u>实际结果</u>：

所有类别都会显示在响应中，无论类别的浏览权限如何。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
