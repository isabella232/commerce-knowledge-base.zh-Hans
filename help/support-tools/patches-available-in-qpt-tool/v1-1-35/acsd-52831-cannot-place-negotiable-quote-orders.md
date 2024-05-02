---
title: 'ACSD-52831：在以下情况下不能下达可转让的报价单： [!DNL Google reCAPTCHA v3 Invisible] 已启用'
description: Adobe Commerce应用ACSD-52831补丁以修复以下问题：当出现以下情况时，您无法下达可转让的报价单 [!DNL Google reCAPTCHA v3 Invisible] 已启用。
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831：在以下情况下不能下达可转让的报价单 [!DNL Google reCAPTCHA v3 Invisible] 已启用

ACSD-52831修补程序修复了以下问题： [!DNL Google reCAPTCHA v3 Invisible] 已启用。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.35。 修补程序ID为ACSD-52831。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在以下情况下无法下达可转让的报价单： [!DNL Google reCAPTCHA v3 Invisible] 已启用。

<u>重现问题的步骤</u>：

1. 启用B2B报价功能。
1. 启用 [!DNL Google reCAPTCHA v3 Invisible] 启用结帐/下单功能。
1. 提出报价，然后使用该报价进行结账。
1. 由于CAPTCHA错误，您将无法下订单。

<u>预期结果</u>：

报价将进行结账。

<u>实际结果</u>：

您收到错误信息 *reCAPTCHA验证失败，请重试*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
