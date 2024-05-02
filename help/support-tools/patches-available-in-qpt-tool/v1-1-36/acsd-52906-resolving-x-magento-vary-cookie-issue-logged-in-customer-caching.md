---
title: 'ACSD-52906：解决已登录客户缓存的XMagento差异Cookie问题'
description: 应用ACSD-52906修补程序以修复针对登录客户的X-Magento差异Cookie设置不正确的Adobe Commerce问题。
feature: Cache
role: Admin, Developer
exl-id: 863e0808-9208-467d-8d56-9dd7a7f4354d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-52906：解决已登录客户的XMagento差异Cookie问题

ACSD-52906修补程序修复了为已登录的客户错误设置X-MagentoVary Cookie的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.36。 修补程序ID为ACSD-52906。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于属于同一客户区段的已登录客户，XMagento差异Cookie设置不正确，导致某些页面的缓存不正确。

<u>先决条件</u>：

Adobe Commerce Inventory management (MSI)模块已安装和启用。

<u>重现问题的步骤</u>：

1. 配置 [!DNL Varnish] 或 [!DNL Fastly] 缓存。
1. 创建新客户区段并将其分配给 *已注册* 客户。
1. 创建两个客户，例如customer1和customer2。
1. 清除缓存。
1. 以customer1身份登录并转到主页。
1. 在浏览器中打开无痕页面。
1. 转到主页以外的任何页面。
1. 以customer2登录。
1. 转到主页。
1. 检查页面是否缓存在浏览器开发控制台中。

<u>预期结果</u>：

将从缓存中检索页面。

<u>实际结果</u>：

不缓存页面。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
