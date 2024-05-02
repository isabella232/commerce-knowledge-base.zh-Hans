---
title: “MDVA-32714修补程序：客户组价格不通过GraphQL起作用”
description: MDVA-32714修补程序修复了在GraphQL产品查询响应中未添加с客户组价格的问题。 安装Quality Patches Tool (QPT) 1.0.13后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: a4fc92ad-68dc-437d-8577-303007ef8a92
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# MDVA-32714修补程序：客户组价格不适用于GraphQL

>[!WARNING]
>
>名为MDVA-33975的新修补程序修复了GraphQL的价格计算问题。 MDVA-32714已弃用，建议您应用修补程序MDVA-33975。 要访问此修补程序，请参阅 [MDVA-33975修补程序：GraphQL价格计算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html) 在我们的支持知识库中。

MDVA-32714修补程序修复了在GraphQL产品查询响应中未添加с客户组价格的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.13。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.4 - 2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL产品查询响应中未添加一般客户的客户组价格。

<u>重现问题的步骤</u>：

1. 为任何客户组的任何产品启用并设置特殊价格。
1. 在GraphQL中使用产品查询来提取此产品的价格，如中所述： [产品查询>示例查询](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html#sample-queries) 在我们的开发人员文档中。

<u>预期结果</u>：

```api
price_range
```

根据管理面板中定义的内容，显示一般客户的折扣价格。

<u>实际结果</u>：

```api
price_range
```

不显示一般客户之折扣价。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
