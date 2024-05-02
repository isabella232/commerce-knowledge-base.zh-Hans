---
title: 'ACSD-52929：重新索引默认源项的冗余请求'
description: 应用ACSD-52929补丁程序，以修复在异步模式下配置清单索引器时存在重新索引默认源项目的冗余请求的Adobe Commerce问题。
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 978fe0d0-3917-4ba2-94bb-01c607a825cc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-52929：重新索引默认源项的冗余请求

ACSD-52929修补程序修复了在异步模式下配置清单索引器时，重新索引默认源项目的请求存在冗余的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.38。 修补程序ID为ACSD-52929。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在异步模式下配置库存索引器时，重新索引默认源项目的请求存在冗余。

<u>重现问题的步骤</u>：

1. 配置 [!DNL RabbitMQ].
1. 通过转到以下位置启用异步重新索引策略 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** 并设置 **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. 创建自定义库存来源。
1. 登录 [!DNL RabbitMQ] 仪表板并转到“队列”选项卡。
1. Check `inventory.indexer.sourceItem` 队列，并确保它没有消息。
1. 从后端打开简单产品并添加 *[!UICONTROL stock only]* 到自定义源并保存产品。
1. 加载 `inventory.indexer.sourceItem` 中的队列 [!DNL RabbitMQ] 功能板，然后检查消息。

<u>预期结果</u>：

自定义源的队列中只有一条消息。

<u>实际结果</u>：

队列中显示两条消息：一条用于默认源，另一条用于自定义源。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
