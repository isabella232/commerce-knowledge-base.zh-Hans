---
title: '''ACSD-47137：提高图像库加载速度''pub/media''文件夹大'''
description: 当“pub/media”文件夹非常大时，应用ACSD-47137修补程序以提高图像库的加载速度。
exl-id: 43268909-6845-4d1d-b6b8-4ae0ce40fd5e
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-47137：提高图像库加载速度，如果 `pub/media` 文件夹大

在以下情况下，ACSD-47137补丁可加快图像库的加载速度： `pub/media` 文件夹非常大。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.24。 修补程序ID为ACSD-47137。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

图像库的加载速度在以下情况下较慢： `pub/media` 文件夹非常大。

<u>重现问题的步骤</u>：

1. 转到Adobe Commerce管理员> **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** 到 _否_.
1. 清除配置缓存。
1. 注销并以管理员用户身份再次登录。
1. 在管理员侧边栏上，转到 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** 并选择根类别。
1. 展开 **[!UICONTROL Content]** 部分并单击 **[!UICONTROL Select from Gallery]**.

加载页面时，Adobe Commerce发送 `media_gallery/directories/gettree` 请求加载媒体文件夹树。

<u>预期结果</u>：

此 `media_gallery/directories/gettree` 请求应仅从必要的目录加载内容，而不是从循环整个路径列表 `pub/media/` 文件夹。

<u>实际结果</u>：

此 `media_gallery/directories/gettree` 请求需要很长时间才能加载，当 `pub/media/` 文件夹包含许多内容。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
