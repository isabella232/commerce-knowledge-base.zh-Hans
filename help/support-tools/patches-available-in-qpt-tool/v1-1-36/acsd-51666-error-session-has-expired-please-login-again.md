---
title: 'ACSD-51666：错误“会话已过期，请重新登录。” 登录后'
description: 应用ACSD-51666修补程序以修复错误*会话已过期的Adobe Commerce问题，请重新登录。*在您尝试登录后发生。
feature: Customers
role: Admin, Developer
exl-id: c3913f1c-f401-440b-b6b3-10702f13fff5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-51666：错误 *会话已过期，请重新登录。* 登录之后

ACSD-51666修补程序修复了错误的问题 *会话已过期，请重新登录。* 在您尝试登录后发生。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.36。 修补程序ID为ACSD-51666。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

您收到错误信息 *会话已过期，请重新登录。* 在重置另一台设备上的密码后，尝试使用新密码从一台设备登录时。 仅当自定义模块添加的页面上有其他Ajax请求时，才会发生这种情况。

<u>重现问题的步骤</u>：

1. 安装自定义模块，在店面的每个页面上添加一个Ajax请求。
1. 创建新帐户。
1. 注销并返回登录页面。
1. 打开 *忘记密码* 链接并发送 *重置密码* 电子邮件。
1. 在第一个浏览器中打开重置密码电子邮件并设置新密码。
1. 尝试在第二个浏览器中登录。

<u>预期结果</u>：

第一次尝试时您能够成功登录。

<u>实际结果</u>：

* 您会看到 *会话已过期，请重新登录。* 错误。
* 您未登录并重定向到主页。
* 第二次登录尝试成功。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
