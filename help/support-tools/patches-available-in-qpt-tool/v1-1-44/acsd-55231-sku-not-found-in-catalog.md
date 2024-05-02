---
title: 'ACSD-55231：使用快速订购功能时出现“SKU未找到”错误'
description: Adobe Commerce应用ACSD-55231修补程序以修复以下问题：当尝试使用快速订购功能将产品添加到购物车时，出现*“在目录中未找到SKU”*错误。
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231：使用快速订购功能时出现“未找到SKU”错误

ACSD-55231修补程序修复了您获取的 *&#39;在目录中找不到SKU&#39;* 尝试使用快速订购功能将产品添加到购物车时出错。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.44。 修补程序ID为ACSD-55231。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

正在获取 *&#39;在目录中找不到SKU&#39;* 使用快速订购功能搜索要添加到购物车的产品时出错。

<u>重现问题的步骤</u>：

1. 安装Adobe Commerce和B2B模块。
1. 导航到 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** 并设置：
   * **[!UICONTROL Enable company]**： *是*
   * **[!UICONTROL Enable Shared Catalog]**： *是*
   * **[!UICONTROL Enable Quick Order]**： *是*
1. 保存上述配置。
1. 转到 **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** 并创建新的共享目录。
1. 导航到 **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** 并创建新客户：
   * 在组字段中，选择最近创建的共享目录并设置 *[!UICONTROL Allow remote shopping assistance]* 到 *是*.
1. 使用SKU生成简单产品 *p12*，将其与类别关联 *c1*，然后在中选择新创建的共享目录 [!UICONTROL Product in Shared Catalog] 部分。
1. 运行：

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. 刷新管理页面。
1. 导航到 **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** 并编辑之前创建的客户。
1. 单击 **[!UICONTROL Login as customer]**.
1. 转到 **[!UICONTROL Quick order]**.
1. 搜索 *p12* SKU并单击 **[!UICONTROL Product Suggestion]**.
1. 将此产品添加到购物车并下订单。
1. 返回到 **[!UICONTROL Quick Order]**，搜索SKU *p12* 再次，然后单击 **[!UICONTROL Product Suggestion]**.

<u>预期结果</u>：

您可以使用快速订购功能将产品添加到购物车。

<u>实际结果</u>：

您无法使用快速订购功能将产品添加到购物车并获取 *&#39;在目录中找不到SKU&#39;* 搜索产品SKU时出错。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
