---
title: “MDVA-40120：GraphQL产品DESC/ASC排序不起作用”
description: MDVA-40120修补程序解决了按DESC/ASC排序的GraphQL不适用于具有相同相关性或价格的产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-40120。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: f04373d6-d3e8-47ba-9261-87fad8dff327
feature: GraphQL, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-40120：GraphQL产品DESC/ASC排序不起作用

MDVA-40120修补程序解决了按DESC/ASC排序的GraphQL不适用于具有相同相关性或价格的产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.6。 修补程序ID为MDVA-40120。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

创建几个价格相同的不同产品。

<u>重现问题的步骤</u>：

1. 运行以下GraphQL查询：
   <pre>
    <code class="language-graphql">
    {
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) {
        total_count
        items {
          name
          sku
        }
      }
    }
    </code>
    </pre>
1. 检查响应。
1. 更改排序顺序 **升序** 到 **DESC** 在GraphQL查询中：
   <pre>
    <code class="language-graphql">
    {
      products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) {
        total_count
        items {
          name
          sku
        }
      }
    }
    </code>
    </pre>
1. 检查响应。

<u>预期结果</u>：

GraphQL响应中的产品列表应根据排序顺序进行更改。

<u>实际结果</u>：

排序顺序保持不变。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
