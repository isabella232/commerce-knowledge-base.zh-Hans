---
title: 'ACSD-52921：从GraphQL请求有关缺货的可配置产品的购物车详细信息时出错'
description: 应用ACSD-52921修补程序以修复Adobe Commerce问题，该问题导致从GraphQL请求缺货可配置产品的购物车详细信息时出现内部错误。
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 687460c4-f0d5-45d2-82b1-dda2947fe1e7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-52921：从GraphQL请求有关缺货的可配置产品的购物车详细信息时出错

ACSD-52921修补程序修复了从GraphQL请求缺货可配置产品的购物车详细信息时发生内部错误的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.35。 修补程序ID为ACSD-52921。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从GraphQL请求有关缺货的可配置产品的购物车详细信息时出现内部错误。

<u>重现问题的步骤</u>：

1. 使用几个选项创建可配置产品。
1. 从前端（访客结帐）将以上可配置产品的选项添加到购物车。
1. 获取 `[ masked_id ]` 从 `[ quote_id_mask ]` 上述已创建报价的db表。
1. 执行以下GraphQL查询以获取上述访客购物车详细信息。

   添加 `[ masked_id ]` 从查询中的步骤3收到。

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. 这将返回报价详细信息，不会出现任何问题。
1. 转到后端并更新可配置产品的 *[!UICONTROL Stock Status]* 到 *[!UICONTROL Out of Stock]*.
1. 执行与步骤4中相同的GraphQL查询。

<u>预期结果</u>：

在响应中正确发送/处理错误消息。

<u>实际结果</u>：

*500内部服务器* 在响应GraphQL查询时引发错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
