---
title: 'MDVA-40488：带缺货子产品的可配置产品未显示在正确的价格范围内'
description: MDVA-40488修补程序解决了具有缺货子产品的可配置产品无法在其正确的价格范围内显示的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-40488。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 0c4b9f5e-ae41-409e-b244-1d7cf948ed6f
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# MDVA-40488：带缺货子产品的可配置产品未显示在正确的价格范围内

MDVA-40488修补程序解决了具有缺货子产品的可配置产品无法在其正确的价格范围内显示的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.9。 修补程序ID为MDVA-40488。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

包含缺货子产品的可配置产品未显示在它们的正确价格范围内。

<u>先决条件</u>：

转到Commerce管理员> **存储** > **配置** > **目录** > **库存** > **股票期权** 并设置 **显示缺货产品** 配置到 *是*.

<u>重现问题的步骤</u>：

1. 创建具有两个关联产品的可配置产品。 例如：简单产品Red和Brown。
1. 将简单产品的库存设置为红色，并将库存状态设置为 *有货*，然后将启用产品状态设置为 *否*.
1. 设置简单产品Brown的库存，然后将“启用产品”状态设置为 *是*.
1. 确保可配置产品的库存状态为 *有货*.
1. 将简单产品Brown的库存更改为0，并将Stock状态设置为 *缺货*.
1. 此时，可配置产品的库存状态仍为 *有货*.
1. 执行重新索引。
1. 查看 `min_price` 和 `max_price` 对于中的可配置产品 `catalog_product_index_price` DB表 — 两个值均设置为0。
1. 但是，如果我们将可配置产品的库存状态设置为 *缺货* 然后进行重新索引，我们就可以看到非零值 `min_price` 和 `max_price` 可配置产品的值。

<u>预期结果</u>：

如果所有子产品为 *缺货* 而且可配置产品本身也 *缺货*，则使用所有子产品计算价格。

<u>实际结果</u>：

此 `min_price` 和 `max_price` 中可配置产品的值 `catalog_product_index_price` 当可配置的库状态为时，数据库表设置为0 *有货*，但如果是 *缺货* 它们会变成非零值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
