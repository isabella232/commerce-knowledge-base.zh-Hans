---
title: 'ACSD-47520：创建贷项通知单时，客户会失去奖励积分'
description: 应用ACSD-47520补丁以修复客户在创建贷项通知单时失去奖励点的Adobe Commerce问题。
exl-id: 748b4e05-981d-49f6-a4f5-b121d57085f4
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47520：创建贷项通知单时，客户会失去奖励积分

ACSD-47520修补程序修复了在创建贷项通知单时客户丢失奖励点的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.25。 修补程序ID为ACSD-47520。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

创建贷项通知单时，客户会失去奖励积分。

<u>重现问题的步骤</u>：

1. 转到Adobe Commerce管理员> **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. 更改设置：
   * **[!UICONTROL Enable Reward Points Functionality]** = _是_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _是_
   * **[!UICONTROL Customers May See Reward Points History]** = _是_
   * **[!UICONTROL Refund Reward Points Automatically]** = _否_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _是_
1. 转到管理员> **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** 并单击 **[!UICONTROL Add New Rate]**.
1. 添加新速率(1:1)并刷新缓存。
1. 创建客户并向此帐户添加10个奖励点。
1. 转到管理员> **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** >选择在上一步中创建的客户。
1. 选择价格大于奖励分数的任意产品。
1. 通过任何支付方式和奖励点数下单。
1. 为订单创建发票。
1. 创建贷项通知单，但不退回奖励积分。

<u>预期结果</u>：

* 管理员可以退还奖励积分。

* 订单状态将会关闭。

<u>实际结果</u>：

* 没有办法退还奖励积分。

* 订单状态为 **[!UICONTROL Completed]**.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
