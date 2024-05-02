---
title: 'MDVA-33453：页面生成器预览分段产品价格因站点而异'
description: MDVA-33453修补程序解决了当匹配产品的每个网站的价格不同时，页面生成器预览会中断的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 78a7f7d4-8691-4b5d-a900-1c9a6ec73486
feature: CMS, Orders, Page Builder, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-33453：页面生成器预览分段产品价格因站点而异

MDVA-33453修补程序解决了当匹配产品的每个网站的价格不同时，页面生成器预览会中断的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.16。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：** 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.6 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当不同网站上存在不同价格的产品时，Page Builder产品预览会中断。

<u>重现问题的步骤</u>：

1. 登录到Commerce管理面板。
1. 创建两个网站。
1. 创建一个简单的产品。
1. 在每个网站上为产品设置不同的价格。
1. 运行cron并重新索引。
1. 创建或编辑CMS页面，然后使用产品块添加产品。

<u>实际结果</u>：<br>

出现以下错误：

*筛选模板时出错：已存在具有相同ID“2”的项目(Magento\\Catalog\\Model\\Product\\Interceptor)。*

<u>预期结果</u>：<br>

不显示错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
