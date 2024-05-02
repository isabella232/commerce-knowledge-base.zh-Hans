---
title: 'ACSD-55352：创建带奖励积分的贷项通知单'
description: 应用ACSD-55352补丁以修复Adobe Commerce问题，其中在使用客户奖励点创建部分贷项通知单后，订单状态更改为*closed*，贷项通知单选项从管理订单页中消失。
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352：创建具有奖励积分的贷项通知单

ACSD-55352修补程序修复了以下问题：在使用客户奖励积分创建部分贷项通知单后，订单状态将更改为 *已关闭* 和贷项通知单选项从管理员订单页面中消失。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.44。 修补程序ID为ACSD-55352。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在创建包含客户奖励分数的部分贷项通知单后，订单状态将更改为 *已关闭* 和贷项通知单选项从管理员订单页面中消失。

<u>重现问题的步骤</u>：

1. 登录到Adobe Commerce管理员。
2. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. 添加两个费率：
   * *[!UICONTROL First]*：
      * *[!UICONTROL Direction]* = *指向货币*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*：
      * *[!UICONTROL Direction]* = *货币到点*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. 创建一个简单的产品，其价格为 *100美元* 和 *数量* ： *100*.
5. 从店面创建客户。
6. 再次转到后端： **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** >添加 *100* 拯救客户。
7. 转到店面，并以客户之前创建的身份登录。
8. 使用以下方式将产品添加到购物车 *数量* ： *10*.
9. 转到 **[!UICONTROL Checkout]** 并使用可用的 *100* 提示下订单时获得奖励积分。
10. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** 并发送订单。
11. 转到 [!UICONTROL Credit Memo] 并更新 *要退款的数量* 到 *8*.
12. 勾选 **[!UICONTROL Refund Reward Points]** 复选框，然后单击 **[!UICONTROL Refund offline]**.
13. 尝试使用退还订单中剩余的两个产品 [!UICONTROL Credit Memo].

<u>预期结果</u>：

* 管理员创建 [!UICONTROL Credit Memo] 以返回其余两个产品。
* 订单状态为 *已完成*.

<u>实际结果</u>：

* 无法创建更多内容 [!UICONTROL Credit Memo].
* 订单状态为 *已关闭*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
