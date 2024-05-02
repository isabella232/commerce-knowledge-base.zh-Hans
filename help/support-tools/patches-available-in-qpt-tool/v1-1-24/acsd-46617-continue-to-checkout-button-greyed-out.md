---
title: '''ACSD-46617： **[!UICONTROL Continue to Checkout]当小计大于配置的最小订单量时，**按钮灰显'
description: 应用ACSD-46617修补程序以解决Adobe Commerce问题，该问题导**[!UICONTROL Continue to Checkout]即使小计大于配置的最小订单量，**按钮也会呈灰显状态。
exl-id: 42fe02bd-f48b-4c6d-8643-ea2c1aa98c94
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-46617： &quot;[!UICONTROL Continue to Checkout]当小计大于“”时，“按钮”灰显[!UICONTROL Minimum Order Amount]&quot;

此ACSD-46617修补程序解决了 **[!UICONTROL Continue to Checkout]** 即使小计大于配置的最小订单量，按钮也会灰显。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.24。 修补程序ID为ACSD-46617。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此 **[!UICONTROL Continue to Checkout]** 即使小计大于配置的最小订单量，按钮也会灰显。

<u>重现问题的步骤</u>：

1. 转到Adobe Commerce管理员> **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** 并设置以下各项：
   * [!UICONTROL Enable]： *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. 创建 [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]： *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]： *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]：
      * [!UICONTROL Apply]： *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]： *[!UICONTROL Yes]*
1. 创建价格为$25的产品。
1. 将产品添加到购物车。
1. 转到购物车，选择$5 **[!UICONTROL Flat Rate shipping]** 方法和应用优惠券代码。
1. 转到结帐，完成装运，然后导航至 **[!UICONTROL Paytment]** 部分。
1. 返回购物车。

<u>预期结果</u>：

最小订单金额没有错误，因为总计$2.4大于所需金额$2。

<u>实际结果</u>：

* 即使总计$2.4大于最小订单金额$2，最小订单金额仍然存在错误。
* 此 **[!UICONTROL Continue to Checkout]** 按钮呈灰显状态。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
