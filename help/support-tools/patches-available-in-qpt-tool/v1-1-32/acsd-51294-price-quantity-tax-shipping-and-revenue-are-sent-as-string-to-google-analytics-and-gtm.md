---
title: '''ACSD-51294：价格、数量、税、运输、收入作为字符串发送至 [!DNL Google Analytics] 和GTM’'
description: 应用ACSD-51294补丁以修复价格、数量、税务、运费和收入作为字符串发送到Adobe Commerce的问题 [!DNL Google Analytics] 和GTM。
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294：价格、数量、税、运输、收入（按字符串发送到） [!DNL Google Analytics] 和GTM

ACSD-51294修补程序修复了将价格、数量、税、运费和收入作为字符串发送到的问题 [!DNL Google Analytics] 和GTM。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.32。 修补程序ID为ACSD-51294。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

价格、数量、税、运费和收入将作为字符串发送至 [!DNL Google Analytics] 和GTM。

<u>重现问题的步骤</u>：

1. 配置 [!DNL Google Tag Manager] 导航到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. 创建一个简单的产品。
3. 使用该产品完成结帐。
4. 查看 `dataLayer` 签出成功页面上的JavaScript变量。

<u>预期结果</u>

价格和数量值为数字。

<u>实际结果</u>

价格和数量值为字符串。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
