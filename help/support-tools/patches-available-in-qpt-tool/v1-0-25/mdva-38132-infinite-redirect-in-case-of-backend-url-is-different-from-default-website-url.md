---
title: 'MDVA-38132：后端URL与默认网站URL不同时的无限重定向'
description: MDVA-38132修补程序修复了后端URL与默认网站URL不同时的无限重定向问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25后，即可使用此修补程序。 修补程序ID为MDVA-38132。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132：后端URL与默认网站URL不同时的无限重定向

MDVA-38132修补程序修复了后端URL与默认网站URL不同时的无限重定向问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.25。 修补程序ID为MDVA-38132。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
云基础架构上的Adobe Commerce 2.3.4-p2

**与Adobe Commerce版本兼容：**
Adobe Commerce（所有部署方法） 2.3.3-2.4.2-p1
>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当后端URL不同于默认网站URL时，Commerce管理面板具有无限重定向。

<u>先决条件</u>：

* 基本URL同时用于后端和店面。 未使用基本安全URL。
* Web服务器的配置方式是，可通过两个不同的URL访问Adobe Commerce。 URL1用于安装Adobe Commerce。

<u>重现问题的步骤</u>：

1. 转到管理面板> **商店** > **配置** > **Web**.
1. 保留全局配置中的原始基本URL。 这是你的URL1。
1. 切换到主网站范围。
1. 将基本URL更改为其他URL（请参阅正确设置Web服务器的先决条件）。 这是您的URL2。
1. 清除缓存（如果必要和可能）。
1. 打开管理面板。

<u>预期结果</u>：

管理面板已成功打开并可导航。 已成功打开主网站的商店，并且可以导航。

<u>实际结果</u>：

发生无限重定向。 Adobe Commerce会从URL1重定向到URL2，并且会来回继续。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
