---
title: 禁用Adobe Commerce横幅输出以提高网站性能
description: 本文修复了站点性能较低的问题。 启用但未使用“Magento_横幅”模块可能会导致网站性能降低。 禁用模块输出可以提高站点性能。 查看文章以了解解决步骤。
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 禁用Adobe Commerce横幅输出以提高网站性能

本文修复了站点性能较低的问题。 站点性能低的原因可能是 `Magento_Banner` 模块已启用，但未使用。 禁用模块输出可以提高站点性能。 查看文章以了解解决步骤。

>[!NOTE]
>
>如果您使用Adobe Commerce Banner功能，请参阅 [高吞吐量AJAX请求导致性能不佳](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md) 本文提供了支持知识库，其中提供了有关如何避免因过多Ajax请求而导致的性能问题的建议。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce v.2.x.x
* Adobe Commerce内部部署v.2.2.x和2.3.x

## 问题

此 `Magento_Banner` 模块已启用，但未使用。

要检查是否出现这种情况，请执行以下操作：

对于Adobe Commerce on cloud infrastructure 2.2.x：

1. 登录到Commerce管理员。
1. 导航到 **内容** > *元素* > **横幅**.
1. 如果此页面上显示的网格为空，则表示您没有任何横幅。

如果您没有看到 **横幅** 下的选项 **内容** > *元素*&#x200B;中指定的货币相同，则不会出现这种情况，并且无法应用本文中的建议。

对于Adobe Commerce on cloud infrastructure 2.3.x(功能是 [在v 2.3.x中重命名](https://devdocs.magento.com/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block))：

1. 登录到Commerce管理员。
1. 导航到 **内容** > *元素>*  **动态块**.
1. 如果此页面上显示的网格为空，则表示您没有任何动态块（横幅）。

如果您没有看到 **动态块** 下的选项 **内容** > *元素*&#x200B;中指定的货币相同，则不会出现这种情况，并且无法应用本文中的建议。

## 原因

当 `Magento_Banner` 模块已启用，Adobe Commerce会将Ajax请求从店面发送到服务器以获取横幅信息。 这些Ajax请求会对性能产生影响，尤其是在高负载（高容量和高流量）情况下。 如果未使用该功能，建议您禁用模块输出。 由于存在依赖性问题，因此不建议禁用该模块。

## 解决方案

>[!WARNING]
>
>我们强烈建议在以下位置测试更改： [暂存/集成环境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) 首先，将其应用于生产之前。 我们还建议在进行任何操作之前进行最近备份。

1. 禁用 `Magento_Banner` 模块输出，如中所述 [禁用模块输出](https://devdocs.magento.com/guides/v2.3/config-guide/config/disable-module-output.html) 在我们的开发人员文档中。 您需要使用的模块名称为 `Magento_Banner`.
1. 部署代码。 对于云基础架构上的Adobe Commerce，请按照 [部署您的商店](https://devdocs.magento.com/guides/v2.3/cloud/live/stage-prod-live.html) 本文档。
