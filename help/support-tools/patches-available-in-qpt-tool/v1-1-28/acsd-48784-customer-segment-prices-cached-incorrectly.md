---
title: 'ACSD-48784：在客户组之间错误地缓存了客户区段价格'
description: 应用ACSD-48784补丁以修复在客户组之间错误地缓存客户区段价格的Adobe Commerce问题。
exl-id: 6be11fd0-5c93-4ac7-8664-7e2a289c9e38
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-48784：客户组之间缓存的客户区段价格不正确

ACSD-48784修补程序修复了在客户组之间错误地缓存客户区段价格的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.28。 修补程序ID为ACSD-48784。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户组之间的客户区段价格缓存不正确。

<u>先决条件</u>：

配置 [!DNL Varnish] 或 [!DNL Fastly].

<u>重现问题的步骤</u>：

1. 在存储中启用全页缓存。
1. 以具有特殊客户组定价的用户身份登录站点。
1. 转到具有特殊客户组定价的产品页面。 观察 *特价*.
1. 在单独的浏览器中，以访客用户身份打开相同的产品页面，而无需登录。 遵守正常价格。
1. 访问Adobe Commerce管理界面并清除Adobe Commerce和 [!DNL Fastly] 此商店的缓存。
1. 在已登录的浏览器中，删除 `X-Magento-Vary` Cookie。
1. 在已登录的浏览器中，重新加载同一产品页面多次，直到缓存完全刷新为止。
1. 在非登录浏览器中，重新加载产品页面，以便现在查看客户组定价。

<u>预期结果</u>：

产品页显示特定客户组的正确价格。

<u>实际结果</u>：

* 访客用户可看到特殊的登录用户价格。
* 将产品添加到迷你购物车后，它会显示正确的价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
