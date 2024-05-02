---
title: “MDVA-28202修补程序：缺货产品未正确过滤”
description: MDVA-28202修补程序解决了在Adobe Commerce商店前端使用**Price**过滤器未正确过滤缺货产品的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6后，即可使用此修补程序。
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-28202修补程序：缺货产品未正确过滤

MDVA-28202修补程序解决了无法使用正确过滤缺货产品的问题。 **价格** 在Adobe Commerce商店前端上筛选。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装v.1.0.6。

## 受影响的产品和版本

* 该补丁是为Cloud Infrastructure 2.3.5-p1上的Adobe Commerce设计的。
* 该补丁还兼容本地Adobe Commerce和Cloud Infrastructure 2.3.4 - 2.4.1上的Adobe Commerce。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

缺货产品未使用正确过滤 **价格** 在Commerce管理中筛选。

<u>先决条件：</u>

* 设置 **显示缺货产品** = &quot;*是*“，在 **存储>配置>目录>库存>库存选项**.

<u>重现问题的步骤：</u>

1. 创建具有两个简单产品的可配置产品(例如：set **价格** = *1500美元*)。
1. 创建可配置产品时，两个简单产品都应“缺货”。
1. 将此可配置产品分配给类别。
1. 重新索引并检查 `catalog_product_index_price` 表来标识上述可配置产品的实体。
1. 保存所有产品价格= *$0*.
1. 加载类别并确认产品的可用性。
1. 打开 **价格** 过滤分层导航。
1. 请注意 **价格** 筛选器的选项为“ *0.00美元 — 9.99美元* “。
1. 单击上面的这个 **价格** 筛选选项并设置 **价格** = *1500美元*，您将获得我们上面创建的可配置产品。

<u>预期结果：</u>

产品会按预期筛选在正确价格范围下的产品。

<u>实际结果：</u>

产品属于错误的价格范围过滤器。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [使用Quality Patches工具应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。

要了解有关可配置产品的更多信息，请参阅我们的开发人员文档中的此文章： [创建可配置的产品教程](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html) 在我们的开发人员文档中。
