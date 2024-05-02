---
title: 'ACSD-57854： *GraphQL*响应包含不应在类别聚合中列出的禁用类别'
description: 应用ACSD-57854修补程序以修复Adobe Commerce问题，该问题导致*GraphQL*响应包含不应在类别聚合中列出的禁用类别。
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854： *GraphQL* 响应包含不应在类别聚合中列出的禁用类别

ACSD-57854修补程序修复了 *GraphQL* 响应中包含不应在类别聚合中列出的禁用类别。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.48。 修补程序ID为ACSD-57854。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

*GraphQL* 响应中包含不应在类别聚合中列出的禁用类别。

<u>重现问题的步骤</u>：

1. 创建两个类别。
1. 创建产品(测试Adobe产品)并将产品分配给这两个类别。
1. 禁用已创建的类别之一。
1. 使用产品 *GraphQL* 以搜索产品。
1. 检查 *GraphQL* 响应。

<u>预期结果</u>：

禁用的类别未列在 *GraphQL* 响应。

<u>实际结果</u>：

已禁用的类别将列在类别聚合中 *GraphQL* 响应。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
