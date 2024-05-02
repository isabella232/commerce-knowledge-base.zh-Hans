---
title: 'ACSD-53643：下达采购订单时，订单总计不正确'
description: 应用ACSD-53643修补程序以修复以下问题：订购禁用或缺货的产品时，Adobe Commerce订单总额不正确。
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643：下达采购订单时，订单总计不正确

ACSD-53643修补程序修复了在订购禁用或缺货产品的采购订单时，订单总额不正确的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.41。 修补程序ID为ACSD-53643。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订购禁用或缺货的产品时，订单总计不正确。

<u>重现问题的步骤</u>：

1. 安装 *[!UICONTROL B2B]* 和 *[!UICONTROL Inventory]*.
1. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** 并设置 **[!UICONTROL Company]** = *是* 和 **[!UICONTROL Purchase Order]** = *是*.
1. 清除配置缓存。
1. 创建新公司、激活它并启用 *[!UICONTROL Purchase order]* 为公司服务。
1. 为公司创建新用户。
1. 创建 *批准规则* 要批准所有订单大于 *1美元* 由公司管理员执行。
1. 创建其他源。
1. 以新公司用户的身份登录。
1. 将两个产品添加到购物车并下达采购订单。
1. 禁用第二个产品。
1. 以公司管理员身份登录。
1. 打开采购订单，然后查看该采购订单是否同时包含产品，并且合计是两个产品的合计。
1. 审批采购订单。
1. 下订单。
1. 打开订单详细信息。

<u>预期结果</u>：

* 即使订单中的一个产品为，也无法下订单 *已禁用* 或 *缺货*.
* *[!UICONTROL Place Order]* 按钮处于隐藏状态。

<u>实际结果</u>：

所下的订单仅包含第一个有效产品，但会计算两个产品的订单合计。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
