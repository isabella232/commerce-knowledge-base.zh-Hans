---
title: 'ACSD-52786：目录规则*[!UICONTROL SKU is]*适用于以SKU开头的所有产品'
description: 应用ACSD-52786修补程序以修复目录规则条件存在的Adobe Commerce问题*[!UICONTROL SKU is]*适用于从给定SKU开始的所有产品。
feature: Price Rules
role: Admin
exl-id: af373b6c-5944-412b-a544-cc6fc3f209d3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52786：目录规则»*[!UICONTROL SKU is]*”适用于以SKU开始的所有产品

ACSD-52786修补程序修复了目录规则条件的问题 *[!UICONTROL SKU is]* 适用于从给定SKU开始的所有产品。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.35。 修补程序ID为ACSD-52786。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

目录规则条件 *[!UICONTROL SKU is]* 适用于从给定SKU开始的所有产品。

<u>重现问题的步骤</u>：

1. 创建两个产品，一个带有SKU“24”，另一个带有SKU“24-MB01”。
1. 导航到 **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. 应用以下条件：
   * *[!UICONTROL If **&#x200B;所有&#x200B;**这些条件中有** TRUE **]*： *[!UICONTROL SKU is 24]*
1. 在操作中设置任何折扣金额。
1. 单击 **[!UICONTROL Save and Apply]**.
1. 刷新缓存。
1. 去店面看看24-MB01的价格。

<u>预期结果</u>：

目录规则仅应用于SKU等于24的单个产品。

<u>实际结果</u>：

目录规则条件 *[!UICONTROL SKU is]* 适用于从给定SKU开始的所有产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
