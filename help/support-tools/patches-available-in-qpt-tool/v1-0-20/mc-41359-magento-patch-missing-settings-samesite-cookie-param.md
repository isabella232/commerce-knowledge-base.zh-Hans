---
title: 'MC-41359商务修补程序：缺少设置SameSite Cookie参数'
description: MC-41359商务修补程序修复了缺少SameSite Cookie参数设置的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20后，即可使用此修补程序。 修补程序ID为MC-41359。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# MC-41359商务修补程序：缺少设置SameSite Cookie参数

MC-41359商务修补程序修复了缺少SameSite Cookie参数设置的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.20。 修补程序ID为MC-41359。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.4.2

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.6-p1、2.4.2、2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

缺少SameSite Cookie参数的设置。

<u>重现问题的步骤：</u>

先决条件：

* 打开Chrome，然后转到chrome://flags/
* 启用 **默认为Cookie设置SameSite** 和 **不具有SameSite的Cookie必须是安全的**.
* 打开Chrome检查器。

<u>场景1：</u>

1. 启用Paypal。
1. 去店前面。
1. 将产品添加到购物车。
1. 去结帐。

<u>场景2：</u>

如果您有New Relic [已启用](https://docs.magento.com/user-guide/reports/new-relic-reporting.html) 警告会显示在任何前端页面上。

<u>实际结果：</u>

浏览器控制台中的警告消息： *与跨站点资源关联的Cookie在设置时没有SameSite属性。*

<u>预期结果：</u>

不应将“lax”添加到Cookie域；samesite属性应使用默认值显示。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
