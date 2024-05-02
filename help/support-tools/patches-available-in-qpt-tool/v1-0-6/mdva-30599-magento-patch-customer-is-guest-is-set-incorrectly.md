---
title: 'MDVA-30599：customer_is_guest设置不正确'
description: MDVA-30599修补程序修复了以下问题：使用API创建的访客报价错误地标记为已登录客户的报价。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。 已在Adobe Commerce 2.4.2中修复此问题。
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599：customer_is_guest设置不正确

MDVA-30599修补程序修复了以下问题：使用API创建的访客报价错误地标记为已登录客户的报价。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.6。 已在Adobe Commerce 2.4.2中修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.4 - 2.4.0

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用API创建的访客报价错误地标记为已登录客户的报价。

<u>重现问题的步骤</u>：

1. 在Adobe Commerce店面，以访客用户身份将产品添加到购物车。
1. 在Adobe Commerce DB中，查找与 `quote_id_mask`.
1. 发送API请求到 `quoteGuestCartRepositoryV1` 来宾购物车的购物车存储库界面。 可以通过Swagger或cURL请求来完成。

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>预期结果</u>：

响应时，您收到 `"customer_is_guest": true`

<u>实际结果</u>：

响应时，您收到 `"customer_is_guest": false`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 安装修补程序后所需的其他步骤

该补丁对所有新来宾购物车都有效。 如果需要修复现有客用车，请设置 `quote.customer_is_guest = 1` 对于这些记录， `quote.customer_id` 为空。 您可以运行类似于以下内容的查询：

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>我们强烈建议先在暂存/集成环境中测试查询，然后再在生产环境中运行它。 我们还建议在使用DB进行任何操作之前先备份最近的数据。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
