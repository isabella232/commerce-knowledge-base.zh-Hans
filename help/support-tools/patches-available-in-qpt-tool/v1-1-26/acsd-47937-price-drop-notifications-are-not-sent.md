---
title: 'ACSD-47937：由于应用程序级别的缓存，未发送价格下降通知'
description: 应用ACSD-47937修补程序以修复由于应用程序级别的缓存而无法始终发送降价通知的Adobe Commerce问题。
exl-id: f39c9ef6-4689-427f-bd61-3a52dec88be2
feature: Admin Workspace, Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-47937：由于应用程序级别的缓存，未发送价格下降通知

ACSD-47937修补程序修复了由于应用程序级别的缓存而无法始终发送降价通知的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.26。 修补程序ID为ACSD-47937。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4和2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4、2.4.5和2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户不会收到后续产品价格更改的产品价格下降电子邮件。

<u>重现问题的步骤</u>：

1. 启用 **[!UICONTROL Product Alert]** 两者 *[!UICONTROL Price Changes]* 和 *[!UICONTROL Back in Stock]* 在 **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. 启用 **[!UICONTROL Display Out of Stock Products]**.
1. 创建数量= 0的简单产品(ABC)。
1. 从店面创建客户并订阅上述产品，获取产品降价提醒。
1. 启动客户产品警报。

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. 降低ABC产品的价格。
1. 触发产品警报cron。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 再次降低ABC产品的价格。
1. 触发产品警报cron。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>如果您不熟悉 [!DNL n98] 工具，然后您可以 `bin/magento cron:run command` 照常进行，监控 `cron_schedule` 表格以确保 `catalog_product_alert` 作业将获得成功状态。

<u>预期结果</u>：

发送第二个降价电子邮件。

<u>实际结果</u>：

第二个降价电子邮件未发送。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
