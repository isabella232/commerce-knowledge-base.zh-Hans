---
title: “ACSD-49042：无法从店面订购具有无限延交订单的产品”
description: 应用ACSD-49042补丁以修复无法从店面订购无限延交产品的Adobe Commerce问题。
exl-id: b9227296-f300-447c-a241-30ccc0691c9a
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-49042：无法从店面订购具有无限延交订单的产品

ACSD-49042修补程序修复了无法从店面订购具有无限延交订单的产品的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.27。 修补程序ID为ACSD-49042。 请注意，Adobe Commerce 2.4.5中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当无法从店面订购具有无限延交订单的产品时，会发生此错误。

<u>重现问题的步骤</u>：

1. 设置以下配置设置：
   * **[!UICONTROL Display Out of Stock Products]** 设置为 *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** 设置为 *[!UICONTROL Allow Qty Below 0]*.
1. 添加新 **[!DNL custom stock]** 和 **[!DNL custom source]**.
1. 将产品分配给 **[!DNL custom source]** 并确保为其设置了库存编号(例如： *10*)。
1. 在产品编辑页面上，打开 **[!UICONTROL Advanced Inventory]**. 设置 **[!UICONTROL minimum quantity]** 在购物车中(例如： *160*)。 数量必须高于库存。
1. 前往店面购买产品以创建预订。
1. 更改 **[!UICONTROL product quantity]** 到 *0*. 关键是从 **[!DNL Admin panel]** 有预订时。
1. 打开 **[!UICONTROL product page]** 并尝试将产品添加到购物车。

<u>预期结果</u>：

可以将产品添加到购物车，因为延期交货的数量低于此值 *0* 是允许的。

<u>实际结果</u>：

产品显示为缺货。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
