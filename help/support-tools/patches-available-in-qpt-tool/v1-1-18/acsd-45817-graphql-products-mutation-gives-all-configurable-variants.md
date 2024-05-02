---
title: 'ACSD-45817：GraphQL产品突变给出了所有可配置变体'
description: ACSD-45817修补程序修复了以下问题：特定存储的GraphQL“products”突变会返回所有可配置变体，包括那些未分配给所请求存储的变体。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18后，即可使用此修补程序。 修补程序ID为ACSD-45817。 请注意，Adobe Commerce 2.4.4中已修复此问题。
exl-id: 3d61d1aa-36b5-471d-929b-7df8ce65c791
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-45817：GraphQL产品突变会提供所有可配置变体

ACSD-45817修补程序修复了GraphQL的问题 `products` 对特定存储进行变异会返回所有可配置的变体，包括那些未分配给所请求存储的变体。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.18。 修补程序ID为ACSD-45817。 请注意，Adobe Commerce 2.4.4中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL `products` 对特定存储进行变异会返回所有可配置的变体，包括那些未分配给所请求存储的变体。

<u>先决条件</u>：

创建第2个网站、第2个商店和第2个商店视图。

<u>重现问题的步骤</u>：

1. 创建包含两个子产品的可配置产品：“configurable-a”和“configurable-b”。
1. 将可配置产品分配给两个网站。
1. 仅向第二个网站分配一个“可配置 — a”变体。
1. 转到 **店面**，切换到第二个网站，然后打开可配置的产品。
1. 确保只看到一个子选项：&quot;configurable-a&quot;。
1. 使用以下方式运行GraphQL查询 `POST: /graphql` 端点，和 `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>预期结果</u>：

“configurable-b”变体未分配给第2个网站，因此不应显示在响应中。

<u>实际结果</u>：

响应中显示“configurable-b”变量。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
