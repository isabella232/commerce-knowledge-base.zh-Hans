---
title: “ACSD-57337：具有访问限制的管理员用户可查看*公司*网格中的所有公司”
description: 应用ACSD-57337修补程序以修复Adobe Commerce问题，该问题导致对特定网站具有访问限制的管理员用户可以在*公司*网格中查看所有网站中的公司。
feature: Companies, B2B, Configuration
role: Admin, Developer
source-git-commit: a02c80006f1c8a434fe17322f0c6cee25f086396
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337：具有访问限制的管理员用户可以在 *公司* 网格

ACSD-57337修补程序修复了以下问题：具有特定网站访问限制的管理员用户可以在 *公司* 网格。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.48。 修补程序ID为ACSD-57337。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对特定网站具有访问限制的管理员用户可以在以下位置查看所有网站上的公司： *公司* 网格。

<u>重现问题的步骤</u>：

1. 创建其他网站、商店和商店评论。
1. 创建一些分配给不同网站的公司。
1. 创建管理员用户角色，并将角色范围设置为已创建的网站。
1. 创建管理员，并将其分配给已创建的角色。
1. 使用新管理员登录。
1. 打开 **[!UICONTROL Customers]** > **[!UICONTROL Companies]** 观察公司名单。

<u>预期结果</u>：

已分配到其他网站的公司将显示在 *公司* 网格。

<u>实际结果</u>：

所有公司都显示在 *公司* 网格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。