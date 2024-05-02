---
title: 'ACSD-47657：为AWS凭据添加了缓存机制'
description: 应用ACSD-47657修补程序，通过为Adobe Commerce凭据添加缓存机制，修复在对AWS S3的高负载请求期间发生的AWS问题。
feature: Cache
role: Admin, Developer
exl-id: d5822082-c656-45bf-b192-9cc8007b82a2
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47657：为AWS凭据添加了缓存机制

ACSD-47657修补程序通过为AWS凭据添加缓存机制，修复了在高负载到AWS S3的请求期间发生的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.39。 修补程序ID为ACSD-47657。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

为从AWS检索到的AWS凭据添加缓存机制以进行EC2配置。

<u>重现问题的步骤</u>：

1. 为Adobe Commerce启用AWS S3存储段存储：

   ```
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="magentopubmedia-prod" --remote-storage-region="aws-west" --no-interaction
   bin/magento config:set 
   system/media_storage_configuration/media_database 0 
   bin/magento cache:flush
   ```

1. 运行同步：

   ```
   bin/magento remote-storage:sync
   ```

<u>预期结果</u>：

同步成功完成。

<u>实际结果</u>：

大约一小时后，出现以下错误：

```
    report.CRITICAL: Aws\Exception\CredentialsException: Error retrieving credentials from the instance profile metadata service. (cURL error 28: Connection timed out after 1001 milliseconds) (see https://curl.haxx.se/libcurl/c/libcurl-errors.html) 
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
