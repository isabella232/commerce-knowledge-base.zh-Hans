---
title: 'ACSD-45168：没有为已覆盖url_key属性的产品生成SEO友好的URL'
description: 应用ACSD-45168修补程序以修复Adobe Commerce问题：对于在商店视图级别覆盖url_key属性的产品，不会生成对SEO友好的URL。
exl-id: cdba42ac-3c96-439b-befa-f0a13587b5d9
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-45168：没有为已覆盖url_key属性的产品生成SEO友好的URL

ACSD-45168修补程序修复了以下问题：对于在存储视图级别覆盖了url_key属性的产品，不会生成SEO友好的URL。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.24。 修补程序ID为ACSD-45168。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于在存储视图级别上覆盖了url_key属性的产品，不会生成SEO友好的URL。

<u>重现问题的步骤</u>：

1. 按照以下方式设置配置，方法是转到 **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**：
   * [!UICONTROL Use Categories Path for Product URLs] = *是*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *是*
1. 清除配置缓存。
1. 创建两个类别： [!UICONTROL Category 1] 和 [!UICONTROL Category 2].
1. 创建两个产品： [!UICONTROL Product 1] 在 [!UICONTROL Category 1]， [!UICONTROL Product 2] 在 [!UICONTROL Category 1].
1. 将范围更改为 [!UICONTROL Default Store View] 对象 [!UICONTROL Product 1].
1. 取消选中可选URL [!UICONTROL Key] 在 [!UICONTROL Search Engine Optimization].
1. 保存产品。
1. 切换回 [!UICONTROL All Store Views].
1. 添加 [!UICONTROL Product 1] 到 [!UICONTROL Category 2]，并添加 [!UICONTROL Product 2] 到 [!UICONTROL Category 2].
1. 查看 [!UICONTROL url_rewrite] 表或 [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>预期结果</u>：

的SEO友好URL [!UICONTROL Category 2] 创建对象 [!UICONTROL Product 1].

<u>实际结果</u>：

的SEO友好URL [!UICONTROL Category 2] 缺少 [!UICONTROL Product 1] 因为它覆盖了存储视图范围的URL键属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
