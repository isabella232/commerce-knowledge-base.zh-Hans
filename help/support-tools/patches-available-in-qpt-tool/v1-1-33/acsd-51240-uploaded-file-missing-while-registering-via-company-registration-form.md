---
title: 'ACSD-51240：通过公司注册表单注册时上传的文件丢失'
description: 应用ACSD-51240修补程序以修复在通过公司注册表单注册时上传的文件缺失的Adobe Commerce问题。
exl-id: e5822c54-4e77-46b0-84b6-5e25c3845974
source-git-commit: e1fe8936c56f422ae591c6424d8a72621093db81
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240：通过公司注册表单注册时上传的文件丢失

>[!NOTE]
>
>此修补程序已替换为 [ACSD-55628](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

ACSD-51240修补程序修复了在通过公司注册表单注册时上传的文件缺失的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.33。 修补程序ID为ACSD-51240。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 问题

通过公司注册表单注册时上传的文件丢失。

<u>重现问题的步骤</u>：

1. 设置 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *是*.
1. 创建新的客户属性 **[!UICONTROL File]** 类型，设置 **[!UICONTROL Show in StoreFront]** = *是*，并选择 **[!UICONTROL all forms]**.
1. 在店面中创建新公司并上传新属性的图像。
在店面中打开公司和管理员用户。

<u>预期结果</u>：

将显示上传的文件。

<u>实际结果</u>：

上传的文件不会显示在的公司页面上，也不会显示在中的管理员客户页面上。 [!UICONTROL Commerce Admin].

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
