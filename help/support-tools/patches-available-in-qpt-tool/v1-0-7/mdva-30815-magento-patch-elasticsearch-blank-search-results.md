---
title: 'MDVA-30815：Elasticsearch的空白搜索结果'
description: MDVA-30815修补程序修复了在更改搜索结果的限制符选项时Elasticsearch显示空白页的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 请注意，Adobe Commerce 2.3.5中已修复此问题。
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815：Elasticsearch的空白搜索结果

MDVA-30815修补程序修复了在更改搜索结果的限制符选项时Elasticsearch显示空白页的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.7。 请注意，Adobe Commerce 2.3.5中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用Elasticsearch时，如果更改搜索结果的限制符选项，Adobe Commerce将显示一个空白页。

<u>先决条件</u>：

Elasticsearch为 **已启用**. 转到 **商店** > **设置** > **配置** > **目录** > **目录搜索**.

<u>重现问题的步骤</u>：

1. 转到您的网站。
1. 在主搜索字段中搜索产品。
1. 显示搜索结果页后，单击搜索结果页中的最后一页。
1. 选择 **每页显示xx个** 从限制符选项中。 请确保这是不同于当前配置的搜索结果数限制。

<u>预期结果</u>：

该页显示配置数量的产品结果。

<u>实际结果</u>：

显示空白页。 此错误也可在 `var/report` ： *\`"0"：&quot;SQLSTATE\[42000\]：语法错误或访问冲突： 1064您的SQL语法有错误；请检查与MySQL服务器版本对应的手册，了解``附近使用的正确语法*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
