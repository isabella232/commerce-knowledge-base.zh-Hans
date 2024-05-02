---
title: 'ACSD-54324： GraphQL requisition_lists请求不考虑分页设置'
description: 应用ACSD-54324修补程序以修复Adobe Commerce问题，该问题导致GraphQL“requisition_lists”请求不考虑分页设置并返回所有结果。
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 85297eae-bedf-4624-9758-0b68452d131b
source-git-commit: b5894687704594a4e751c230246bdf167b1b6402
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-54324：GraphQL `requisition_lists` 请求不考虑分页设置

ACSD-54324修补程序修复了GraphQL的问题 `requisition_lists` 请求不考虑分页设置并返回所有结果。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.41。 修补程序ID为ACSD-54324。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL `requisition_lists` 请求不考虑分页设置并返回所有结果。

<u>重现问题的步骤</u>：

1. 登录到管理员，然后导航到 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * 设置 *[!UICONTROL Enable Requisition List]* 到 *是*.

1. 登录到前端，然后转到 **[!UICONTROL My Requisition Lists]** 从顶部菜单或从 **[!UICONTROL My Account]**，并创建多个申请（例如：7）。
1. 生成客户令牌后，运行以下GraphQL `requisition_lists` 查询客户。

   * 确保页面大小小于您创建的申请列表总数（例如：4）

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. 请注意， `total_count` 字段显示7，何时应显示4。

   当项目数应与 *页面大小*.

<u>预期结果</u>：

* 编号列为 *页面大小* 返回于 `total_count` 而不是记录的总数。
* 项目数与 *页面大小*.

<u>实际结果</u>：

返回的记录总数 `total_count`，即使 *页面大小* 中提及。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
