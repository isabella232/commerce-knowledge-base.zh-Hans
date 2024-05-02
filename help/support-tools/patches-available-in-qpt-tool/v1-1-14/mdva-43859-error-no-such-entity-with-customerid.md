---
title: '''MDVA-43859：错误“删除的客户登录时，未记录具有customerId =的此类实体”'
description: MDVA-43859修补程序修复了以下问题：当删除的客户尝试登录时，不会记录具有customerId=*的此类实体。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-43859。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 62c4b6ee-88a0-40b8-9eb2-37b6cefa0b83
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-43859：删除的客户登录时，出现“没有记录具有customerId =”的此类实体”错误

MDVA-43859修补程序修复了错误的问题 *没有具有customerId =的此类实体* 当已删除的客户尝试登录时记录。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.14。 修补程序ID为MDVA-43859。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误 *没有具有customerId =的此类实体* 当已删除的客户尝试登录时记录。

<u>重现问题的步骤</u>：

1. 从前端创建客户帐户。
1. 注销并登录到在步骤1中创建的客户帐户。
1. 在其他浏览器中加载后端，然后转到客户网格。
1. 删除在第一步中创建的客户。
1. 切换回第一个浏览器并尝试注销。

<u>预期结果</u>：

客户将被重定向到登录页面，并且不会出现任何错误。

<u>实际结果</u>：

客户收到以下错误： *没有具有customerId =的此类实体*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
