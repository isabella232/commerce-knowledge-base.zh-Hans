---
title: ’[!DNL ACSD-47280]：禁用共享目录会给出错误的产品搜索结果'
description: 应用 [!DNL ACSD-47280] 修复了在禁用共享目录功能时显示正确搜索结果的修补程序。
exl-id: 98bbae42-fd68-4b54-823d-189d742cc35f
source-git-commit: 975f5b5c95ad488128a5dbb3488b8d54f7b73b59
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]：禁用共享目录会给出错误的产品搜索结果

此 [!DNL ACSD-47280] 在以下情况下，修补程序可修复正确搜索结果的显示： [!DNL shared catalog] 功能已禁用。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.22。 此 [!DNL patch ID] 是 [!DNL ACSD-47280]. 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用 [!DNL patch ID] 作为搜索关键字来查找修补程序。

## 问题

正在禁用 [!DNL shared catalog] 提供的产品搜索结果有误。

<u>先决条件</u>：

* [!DNL B2B] 安装的模块

<u>重现问题的步骤</u>：

1. 创建第二个网站。
1. 将产品分配给第二个网站。
1. 检查上的产品 **第二个网站** 使用 [!DNL GraphQL]：

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. 启用 **[!UICONTROL Shared Catalog]** 默认 [!DNL scope].
1. 此 [!DNL GraphQL] 请求不再显示第二个网站的任何产品，这是正确结果。
1. 转到 [!DNL scope] 第二个网站并禁用 **[!UICONTROL Company]**.

<u>预期结果</u>：

此 [!DNL GraphQL] 请求仍应显示第二个网站的产品。

<u>实际结果</u>：

此 [!DNL GraphQL] 请求未显示第二个网站的任何产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
