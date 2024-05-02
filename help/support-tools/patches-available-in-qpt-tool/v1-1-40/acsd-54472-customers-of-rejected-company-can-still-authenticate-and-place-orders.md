---
title: 'ACSD-54472：被拒绝公司的客户仍然可以进行身份验证'
description: 应用ACSD-54472修补程序以修复Adobe Commerce问题，该问题导致被拒绝公司的客户仍然可以执行身份验证，被阻止和被拒绝公司的客户仍然可以下订单。
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472：被拒绝公司的客户仍然可以进行身份验证

ACSD-54472修补程序修复了以下问题：被拒绝公司的客户仍然可以进行身份验证，被阻止和被拒绝公司的客户仍然可以下订单。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.40。 修补程序ID为ACSD-54472。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

被拒绝公司的客户仍然可以进行身份验证，被阻止和被拒绝公司的客户仍然可以下订单。

<u>重现问题的步骤</u>：

1. 创建公司。
1. 通过以下方式将产品添加到购物车 [!DNL GraphQL].
1. 将公司状态更改为 *已阻止*.
1. 发送 [!DNL GraphQL] 提交订单和创建可转让报价的请求。
1. 将公司状态更改为 *被拒绝*.
1. 发送 [!DNL GraphQL] 请求获取公司的用户授权令牌。
1. 将客户状态设置为 *不活动*.
1. 发送 [!DNL GraphQL] 请求获取公司的用户授权令牌。

<u>预期结果</u>：

* 订单和可转让报价不是由 *已阻止* 公司。
* 未为的用户获取授权令牌 *被拒绝* 公司。
* 未获取 *不活动* 客户。

<u>实际结果</u>：

* 订单和可转让报价由 *已阻止* 公司。
* 为的用户获取授权令牌 *被拒绝* 公司。
* 已为获取授权令牌 *不活动* 客户。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
