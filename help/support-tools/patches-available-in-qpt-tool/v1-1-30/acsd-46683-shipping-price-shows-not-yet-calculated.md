---
title: 'ACSD-46683：配送价格显示*尚未计算*'
description: 应用ACSD-46683修补程序以修复发货价格显示*尚未计算*的Adobe Commerce问题。
exl-id: 77986612-87b7-4f50-afaf-1cfe9a4feb6f
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-46683：配送价格显示 *尚未计算*

ACSD-46683修补程序修复了发货价格显示的问题 *尚未计算*. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.30。 修补程序ID为ACSD-46683。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

运费显示 *尚未计算*.

<u>先决条件</u>：

Adobe Commerce Inventory management (MSI)模块已安装。

<u>重现问题的步骤</u>：

1. 创建简单产品并将其价格设置为 *34美元*.
1. 配置免费送货方式。
1. 配置至少一个以上的投放方法。
1. 转到 **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** 并创建新规则：
   * 名称= *75更多*
   * 优惠券=无
   * 优先级= 1
   * 条件：小计等于或大于 *75美元*
   * 操作：
      * 应用于发运金额=是
      * 放弃后续规则=否
      * 免费发运=对于具有匹配物料的发运
1. 创建另一个购物车价格规则：
   * 名称= *35关*
   * 优先级= 0
   * 优惠券=特定优惠券
   * 优惠券代码= 35折扣
   * 操作：
      * 应用=产品价格折扣的百分比
      * 折扣金额= 35
      * 应用于装运金额=否
      * 放弃后续规则=是
      * 免费送货=否
1. 打开店面，然后将三个产品添加到购物车，以使小计超过$75。
1. 以来宾身份继续结帐。
1. 在送货步骤中，选择 **$0 — 免运费** 并进入支付步骤。
1. 查看 [!UICONTROL Order Summary] 在付款步骤中。 它显示 *[!UICONTROL $0 - Free Shipping - Free]*.
1. 应用优惠券代码 *35关*，它会更新小计，使其小于$75。
1. Check [!UICONTROL Order Summary] 在付款步骤中。

<u>预期结果</u>：

将显示以下消息： *所选的配送方式不可用。 请选择此订单的其他配送方式。*

<u>实际结果</u>：

装运价格显示 *尚未计算*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
