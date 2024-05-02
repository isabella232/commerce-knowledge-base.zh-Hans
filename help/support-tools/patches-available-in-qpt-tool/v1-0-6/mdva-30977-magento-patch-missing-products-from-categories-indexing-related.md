---
title: 'MDVA-30977：类别中缺少产品，索引相关'
description: MDVA-30977修补程序修复了在对大量产品进行重新索引或批量操作期间，在店面类别页面上显示的产品存在的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6后，即可使用此修补程序。 计划在Adobe Commerce 2.4.2中修复这些问题。
exl-id: 66ec4f53-c01d-4f87-a175-84f44a26f5d3
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# MDVA-30977：类别中缺少产品，索引相关

MDVA-30977修补程序修复了在对大量产品进行重新索引或批量操作期间，在店面类别页面上显示的产品存在的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装v.1.0.6。 计划在Adobe Commerce 2.4.2中修复这些问题。

## 受影响的产品和版本

该修补程序是为Adobe Commerce on cloud infrastructure 2.3.4创建的。它还与Adobe Commerce内部部署2.3.4兼容。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

### 问题1

在成批产品更新期间重新加载每个页面后，在店面的类别页面上显示的产品数会有所不同。

<u>重现问题的步骤：</u>

1. 创建两个类别中的至少30000个产品 — 每个类别中至少15000个产品。
1. 转到 **目录** > **产品** 在Commerce管理员中。
1. 从网格中选择所有产品，然后执行批量属性更新。 例如，设置 **新建** = *是* 属性。
1. 使用运行Magentocron作业 `bin/magento cron:run` 命令两次。
1. 在Adobe Commerce执行产品更新时，刷新Storefront30000类别页面。

<u>预期结果：</u>

每次类别页面刷新时，类别中的产品数量始终为15000。

<u>实际结果：</u>

每次类别页面刷新时，类别中的产品数量各不相同。

### 问题2

执行清单的完整重新索引时，类别页变为空，并且 *找不到与所选内容匹配的产品* 将显示消息。

<u>重现问题的步骤：</u>

1. 使用Elasticsearch配置Adobe Commerce。
1. 添加新网站。
1. 使用“管理库存”创建新来源并将其分配给新网站。
1. 创建30000配置产品。
1. 将所有产品分配到新网站，并将清单添加到新清单源。
1. 执行完全重新索引。
1. 通过运行执行清单重新索引 `bin/magento indexer:reindex inventory`
1. 浏览具有大量产品的类别。

<u>预期结果：</u>

类别页在重新索引期间照常显示产品。

<u>实际结果：</u>

在重新索引期间，类别页变为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
