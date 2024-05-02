---
title: 'ACSD-47232：在以下情况下不应用优惠券： [!UICONTROL Same as Billing Address] 已选中'
description: 应用ACSD-47232修补程序以修复以下情况下未应用优惠券的Adobe Commerce问题 [!UICONTROL Same as Billing Address] 已选中。
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232：在以下情况下不应用优惠券： [!UICONTROL Same as Billing Address] 已选中

ACSD-47232修补程序修复了以下情况下未应用优惠券的问题： **[!UICONTROL Same as Billing Address]** 已选中。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.23。 修补程序ID为ACSD-47232。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在以下情况下不应用优惠券： **[!UICONTROL Same as Billing Address]** 已选中。

<u>重现问题的步骤</u>：

1. 安装Adobe Commerce。
1. 创建一个简单的产品，其权重为= *8*.
1. 使用默认帐单和送货地址创建新客户。
1. 创建包含优惠券的购物车价格规则。
   * 在 **[!UICONTROL Conditions]** 部分，添加 *总重量等于或大于5*
1. 尝试在中创建新订单 [!UICONTROL Commerce] 管理员。
   * 使用刚刚创建的客户
   * 添加产品
   * 尝试应用优惠券

<u>预期结果</u>：

已应用优惠券。

<u>实际结果</u>：

您收到类似于以下内容的错误： *123优惠券代码无效。 请验证代码并重试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
