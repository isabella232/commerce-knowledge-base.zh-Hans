---
title: 'ACSD-54626：无法通过GraphQL创建具有NUMBER_OF_SKUS的新采购订单规则'
description: 应用ACSD-54626修补程序以修复Adobe Commerce问题，该问题导致客户无法通过GraphQL创建具有“NUMBER_OF_SKUS”属性的新采购订单规则(“createPurchaseOrderApprovalRule”)。
feature: Attributes, B2B, GraphQL, Purchase Orders
role: Admin, Developer
exl-id: 807f06e3-6708-4860-bf46-df4404124f27
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-54626：无法通过GraphQL创建具有NUMBER_OF_SKUS的新采购订单规则

ACSD-54626修补程序修复了客户无法创建新采购订单规则(`createPurchaseOrderApprovalRule`) `NUMBER_OF_SKUS` 属性访问GraphQL。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.42。 修补程序ID为ACSD-54626。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户无法创建新采购订单规则(`createPurchaseOrderApprovalRule`) `NUMBER_OF_SKUS` 属性访问GraphQL。

<u>先决条件</u>：

安装和启用Adobe Commerce B2B模块。

<u>重现问题的步骤</u>：

1. 启用B2B公司和购买规则。
1. 创建一个已启用购买规则的公司。
1. 运行以下GraphQL查询：

   ```
   mutation CreatePurchaseRule {
       createPurchaseOrderApprovalRule(
           input: {
               name: "Test Rule"
               description: "description"
               applies_to: "MQ=="
               status: ENABLED
               approvers: "MQ=="
               condition: {
                   attribute: NUMBER_OF_SKUS
                   operator: MORE_THAN
                   quantity: 10
               }
           }
       ) {
           uid
           name
           __typename
       }
   }
   ```

<u>预期结果</u>：

创建购买规则。

<u>实际结果</u>：

引发以下错误：

```
{
    "errors": [
        {
            "message": "Required data is missing from a rule condition.",
            "locations": [
                {
                    "line": 2,
                    "column": 3
                }
            ],
            "path": [
                "createPurchaseOrderApprovalRule"
            ],
            "extensions": {
                "category": "graphql-input"
            }
        }
    ],
    "data": {
        "createPurchaseOrderApprovalRule": null
    }
}
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
