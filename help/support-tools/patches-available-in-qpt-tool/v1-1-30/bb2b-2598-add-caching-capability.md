---
title: 'BB2B-2598：增加了对storeConfig、货币、国家/地区、availableStores GraphQl查询的缓存功能'
description: 应用BB2B-2598修补程序以向storeConfig、货币、国家/地区、国家/地区和availableStores GraphQl查询添加缓存功能。
exl-id: 37551954-d721-4f3a-b237-cd795f715a5f
feature: B2B, GraphQL, Cache
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# BB2B-2598：为添加缓存功能 `storeConfig`， `currency`， `country`， `countries`、和 `availableStores` GraphQl查询

BB2B-2598修补程序将缓存功能添加到 `storeConfig`， `currency`， `country`， `countries`、和 `availableStores` graphql查询。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.30。 修补程序ID为BB2B-2598。 请注意，该问题计划在Adobe Commerce 2.4.7-beta1中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`availableStores`， `countries`， `country`， `currency`， `storeConfig`、和 `customAttributeMetadata` GraphQL查询不可缓存。

<u>先决条件</u>：

* 服务器指向 [!DNL Varnish] 代理到Adobe Commerce后端。
* 配置设置 `system/full_page_cache/caching_application` 设置为 *2* ([!DNL Varnish])，或转到Adobe Commerce管理员> **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** >并将其设置为 [!DNL Varnish].

应用修补程序后，请运行以下步骤以确保缓存功能现在可用：

1. 发送 `GET` 使用任意字段向上面列出的任何GraphQL查询发出请求。
1. 重新发送请求，且不做任何更改；您会发现它速度更快。 请注意，请求不会发送到后端，但它完全由处理 [!DNL Varnish] 作为缓存命中。
1. 如果需要进一步验证，请注释掉未设置的 `X-Magento-Debug` 标头出现在我们的中 [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227)，然后重新启动 [!DNL Varnish] 并再次运行上述步骤。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
