---
title: 'ACSD-49286：当存在多个产品小组件时，将产品添加到购物车两次'
description: 应用ACSD-49286修补程序以修复Adobe Commerce问题：当页面上存在多个产品小组件时，产品会向购物车中添加两次。
exl-id: b1764943-945d-4ef9-9bbe-3f3c8383b5b1
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49286：当存在多个产品构件时，将产品添加到购物车两次

ACSD-49286修补程序修复了当页面上存在多个产品小组件时，将产品两次添加到购物车的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.28。 修补程序ID为ACSD-49286。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当页面上存在多个产品小组件时，会将产品添加到购物车两次。

<u>重现问题的步骤</u>：

1. 登录到管理员并转到 **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. 在内容部分中，单击 **[!UICONTROL Edit]** 使用 [!DNL Page Builder].
1. 将两个行元素添加到 **[!UICONTROL Content]**.
1. 将产品添加到这两个行元素中。
1. 在第一行中，将产品外观设置为 [!UICONTROL Product Grid] 并选择要显示的任意类别。
1. 在第二行中，将产品外观设置为 [!UICONTROL Product Carousel] 并选择要显示的任何其他类别。
1. 去店面 **[!UICONTROL Home Page]**，并从Product Grid添加一个产品。
1. 从添加其他产品 [!UICONTROL Product Carousel].

<u>预期结果</u>：

将产品从添加到购物车后，产品数量不应增加一倍 [!UICONTROL Product Grid].

<u>实际结果</u>：

将产品从添加到购物车后，产品数量会翻倍 [!UICONTROL Product Grid].

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。 

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
