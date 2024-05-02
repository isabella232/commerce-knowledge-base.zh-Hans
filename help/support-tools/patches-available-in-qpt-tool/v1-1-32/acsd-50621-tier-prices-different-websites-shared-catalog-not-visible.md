---
title: 'ACSD-50621：共享目录中不同网站的分层价格不可见'
description: 应用ACSD-50621修补程序以修复Adobe Commerce问题，该问题导致在多个网站环境中编辑共享目录中的不同网站时，无法看到这些网站的层价格。
exl-id: 6d6635bc-4f76-4e2f-9bc7-0276cced8ca9
feature: Catalog Management, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-50621：共享目录中不同网站的分层价格不可见

ACSD-50621修补程序修复了在多网站环境中编辑共享目录中不同网站的层价格时不可见的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.32。 修补程序ID为ACSD-50621。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在多网站环境中编辑共享目录中的不同网站时，不会显示这些网站的分层价格。

<u>重现问题的步骤</u>：

1. 设置 **[!UICONTROL Catalog Price Scope]** 到 **[!UICONTROL Website]**.
1. 创建其他网站、商店和商店评论。
1. 创建一个简单的产品并将其分配给所有网站。
1. 创建自定义共享目录。
1. 转到 **[!UICONTROL Set Pricing and Structure]** （对于您创建的自定义共享目录）。
1. 在第1步中：为目录选择产品。 添加您创建的简单产品。
1. 在第2步中：设置自定义价格并单击 **[!UICONTROL Configure]**.
1. 为不同的网站设置不同的层级价格。
1. 选择 **[!UICONTROL Done]** 并单击 **[!UICONTROL Generate Catalog]** 然后单击 **[!UICONTROL Save]**.
1. 运行cron。
1. 导航到 **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** 并验证层价格。

<u>预期结果</u>：

以前为不同网站配置的所有层价格均存在。

<u>实际结果</u>：

先前配置的层价格不存在。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
