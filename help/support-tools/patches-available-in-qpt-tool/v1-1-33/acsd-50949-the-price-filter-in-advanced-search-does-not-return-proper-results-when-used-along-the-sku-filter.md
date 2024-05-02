---
title: 'ACSD-50949：高级搜索中的价格过滤器在与SKU过滤器一起使用时未返回正确结果'
description: 应用ACSD-50949补丁以修复Adobe Commerce问题，该问题导致高级搜索中的价格过滤器在与SKU过滤器一起使用时无法返回正确结果。
feature: Orders, Search
role: Admin
exl-id: 3e1f88dc-07f6-4e10-b4b7-163648076cbc
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# ACSD-50949：与SKU过滤器一起使用时，高级搜索中的价格过滤器未返回正确结果

ACSD-50949修补程序修复了高级搜索中的价格过滤器在与SKU过滤器一起使用时无法返回正确结果的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.33。 修补程序ID为ACSD-50949。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 问题

高级搜索中的价格过滤器在与SKU过滤器一起使用时未返回正确结果。

<u>重现问题的步骤</u>：

1. 创建多个产品，例如：

   | SKU | 名称 | 价格 | 数量 |
   |-----|-----------|-------|----------|
   | 麦芽1 | 产品1 | 10美元 | 10 |
   | MJ2 | 产品2 | 15美元 | 10 |
   | 马航3型 | 产品3 | 21美元 | 10 |
   | 麦角四号 | 产品4 | 32美元 | 10 |
   | 马绍尔群岛航空 | 产品5 | 33美元 | 10 |
   | 麦剑6 | 产品6 | 34美元 | 10 |
   | 麦剑7 | 产品7 | 44美元 | 10 |

1. 打开 **[!UICONTROL Advanced Search]** ，并由SKU搜索：“MJ”。
1. 单击 **[!UICONTROL Modify your search]** 链接。
1. 将价格范围添加到以下项的标准： *1* 到 *21*，然后单击 **[!UICONTROL Search]** 按钮。

<u>预期结果</u>：

只返回价格在定义范围内的产品。

<u>实际结果</u>：

产品价格高于 *21美元* 会返回。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
