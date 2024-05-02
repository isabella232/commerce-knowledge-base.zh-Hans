---
title: '''ACSD-47027：慢查询B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新'
description: 应用ACSD-47027修补程序以修复查询B2B速度缓慢的Adobe Commerce问题 [!UICONTROL CompanyRole] [!DNL GraphQL] 更新。
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027：查询B2B缓慢 [!UICONTROL CompanyRole] [!DNL GraphQL] 更新

ACSD-47027修补程序解决了查询B2B速度缓慢的问题 [!UICONTROL CompanyRole] [!DNL GraphQL] 更新无法按预期工作。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.23。 修补程序ID为ACSD-47027。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

慢查询B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新无法按预期工作。

<u>先决条件</u>：

安装B2B模块。

<u>重现问题的步骤</u>：

1. 在Adobe Commerce Admin中，转到 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]** 并设置 **[!UICONTROL Enable Company]** 到 _是_.
1. 前往前端，创建公司。
1. 以公司用户身份登录后，转到 **[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]** 并添加新角色。
1. 启用 [!UICONTROL dev] 查询日志，使用 `bin/magento dev:que:enab`.
1. 现在发送以下内容 [!DNL GraphQL] 请求(id是 [!UICONTROL base64] 编码角色id)：

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. 检查查询日志。
1. 您可以看到上述查询已执行。 此查询的执行位置 `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`.

<u>预期结果</u>：

此 `app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources` 需要优化，以避免加载 **[!UICONTROL company_permissions]** 数据库表。

<u>实际结果</u>：

Adobe Commerce执行查询而不使用任何筛选器。 当记录数量很大时，Adobe Commerce需要大量时间来准备数据收集。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。 

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
