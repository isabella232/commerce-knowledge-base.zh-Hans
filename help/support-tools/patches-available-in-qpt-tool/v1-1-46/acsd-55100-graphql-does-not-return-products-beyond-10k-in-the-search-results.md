---
title: “ACSD-55100： [!DNL GraphQL] 不会返回搜索结果中超过10,000的产品”
description: 应用ACSD-55100修补程序以修复Adobe Commerce问题，该问题导致GraphQL在搜索结果中未返回超过*10k*的产品。
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100： [!DNL GraphQL] 不会返回搜索结果中超过10k的产品

ACSD-55100修补程序修复了以下问题 [!DNL GraphQL] 不会返回超出以下范围的产品 *1万* 在搜索结果中。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.46。 修补程序ID为ACSD-55100。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!DNL GraphQL] 不会返回超出以下范围的产品 *1万* 在搜索结果中。

<u>先决条件</u>：

如果是 **[!DNL OpenSearch]**，确保您使用的是最新可用版本。

为了解决报告的问题，引入了时间点功能，该功能在以下时段后可用 **[!DNL OpenSearch]** 2.5.0，需要版本2.2的 `opensearch-project/opensearch-php` 包。

但是，与 `magento/magento-cloud-metapackage`，指定依赖于 `opensearch-project/opensearch-php` 应小于版本2.0.1的包。


此依赖关系阻止更新 [opensearch-project/opensearch-php] 包到最新版本2.2。

因此，系统会遇到以下错误，对于超过以下值的产品会返回空结果 *10,000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

现有的依赖关系使得直接向添加版本变得非常困难 `composer.json` 文件并更新 `opensearch-project/opensearch-php` 包到版本2.2。

要解决此问题，请在主文件中包含以下行 `composer.json` 个文件（位于所需块下）。 之后，重新部署以将有问题的包更新到最新版本。

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>重现问题的步骤</u>：

1. 生成目录 *15k* 产品。
1. 发送 [!DNL GraphQL]：

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>预期结果</u>：

总计= *15k*
您应该能够显示所有产品。

<u>实际结果</u>：

总计= *1万*
之后无法再显示任何产品 *1万* 批处理。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
