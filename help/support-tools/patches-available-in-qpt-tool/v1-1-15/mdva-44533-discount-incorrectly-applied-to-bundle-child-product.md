---
title: 'MDVA-44533：折扣错误地应用于捆绑的子产品'
description: MDVA-44533修补程序修复了将折扣错误地应用于捆绑子产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15后，即可使用此修补程序。 修补程序ID为MDVA-44533。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 84302ed4-d850-45e4-8b5b-44495f9df820
feature: Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-44533：折扣错误地应用于捆绑的子产品

MDVA-44533修补程序修复了将折扣错误地应用于捆绑子产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.15。 修补程序ID为MDVA-44533。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

折扣错误地应用于捆绑的子产品。

<u>重现问题的步骤</u>：

1. 创建一个价格为50美元的简单产品。
1. 创建捆绑产品，并将简单产品指定为捆绑产品的唯一选项。
1. 使用以下方式创建购物车价格规则：

   * 条件：如果总金额大于130$
   * 操作：应用10$的固定金额折扣

1. 转到店面并将捆绑包产品添加到购物车，数量为1。
1. 转到购物车并检查捆绑产品的总成本是否为50$，并且折扣不适用。
1. 将数量更改为2并更新购物车。 捆绑产品的总成本现在应为100$。

<u>预期结果</u>：

不应用折扣，因为小计为100\$，在规则条件中小于130\$。

<u>实际结果</u>：

将应用折扣。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
