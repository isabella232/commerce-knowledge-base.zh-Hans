---
title: 'MDVA-36833：搜索结果页面上的分页损坏'
description: MDVA-36833修补程序修复了在启用共享目录并从共享目录中排除某些产品时分页中断的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22后，即可使用此修补程序。 修补程序ID为MDVA-36833。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 7105c4ed-48d9-4d4c-bf12-5914bbad62da
feature: Catalog Management, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-36833：搜索结果页面上的分页损坏

MDVA-36833修补程序修复了在启用共享目录并从共享目录中排除某些产品时分页中断的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.22。 修补程序ID为MDVA-36833。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** Adobe Commerce（所有部署方法） 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从共享目录排除某些产品会导致搜索结果的分页损坏。

<u>重现问题的步骤：</u>

1. 启用共享目录。
1. 转到 **目录** > **共享目录** 并通过为其分配所有产品来设置默认共享目录。
1. 加载店面并搜索“jacket”。
1. 请注意第一页上列出的产品。 应该有12种产品。
1. 从第一页开始记下11个SKU。 转到后端并加载默认共享目录。
1. 从默认共享目录中取消分配以前记录的SKU。
1. 去店面搜寻“夹克”。
1. 检查搜索结果的第一页。

<u>实际结果：</u>

第一页具有一个产品，而其余产品可在第二页上使用。

<u>预期结果：</u>

第一页应该有12种产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。


## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
