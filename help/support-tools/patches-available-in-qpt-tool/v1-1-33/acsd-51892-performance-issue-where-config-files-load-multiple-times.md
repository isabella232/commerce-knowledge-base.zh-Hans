---
title: 'ACSD-51892：配置文件加载多次出现的性能问题'
description: 应用ACSD-51892修补程序以修复在部署期间多次加载配置文件的Adobe Commerce性能问题。
feature: Observability
role: Admin
exl-id: 397343df-360f-43c4-bcef-be5f0da5aeef
source-git-commit: 97734799a39f41d0d6441379e21608fa5fcd1d4c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-51892：配置文件加载多次出现的性能问题

ACSD-51892修补程序修复了加载 `app/etc/env.php` 和 `app/etc/config.php` 每次在单个请求中访问部署配置值时发送的文件。 文件读取过多给系统带来压力，导致整体性能下降。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.33。 修补程序ID为ACSD-51892。 请注意，Adobe Commerce 2.4.6-p2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

存在配置文件加载多次的性能问题。

<u>重现问题的步骤</u>：

1. 执行部署或升级到Adobe Commerce 2.4.6或更高版本。
1. 检查文件系统日志以访问 `app/etc/env.php` 和 `app/etc/config.php` 文件数。

<u>预期结果</u>：

在常规时间范围内部署成功。

<u>实际结果</u>：

* 服务器正在努力响应您输入的任何命令。 这将导致 *错误503第一字节超时* 访问网站时。
* 日志文件中有多个条目可以访问到 `app/etc/env.php` 和 `app/etc/config.php` 文件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
