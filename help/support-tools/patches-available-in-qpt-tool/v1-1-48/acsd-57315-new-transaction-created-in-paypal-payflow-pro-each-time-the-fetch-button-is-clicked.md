---
title: '''ACSD-57315：新事务创建于 [!DNL PayPal Payflow Pro] 每次单击“获取”按钮时'
description: 应用ACSD-57315修补程序以修复在中创建新事务的Adobe Commerce问题。 [!DNL PayPal Payflow Pro] 每次在的“查看交易”屏幕上单击“提取”按钮时， [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315：新事务处理创建于 [!DNL PayPal Payflow Pro] 每次单击“获取”按钮时

ACSD-57315修补程序修复了在中创建新交易的问题 [!DNL PayPal Payflow Pro] 每次在的“查看交易”屏幕上单击“提取”按钮时， [!UICONTROL Admin]. 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.48。 修补程序ID为ACSD-57315。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

新事务创建于 [!DNL PayPal Payflow Pro] 每次在的“查看交易”屏幕上单击“提取”按钮时， [!UICONTROL Admin].

<u>重现问题的步骤</u>：

1. 配置 [!DNL PayPal Payflow Pro].
1. 将交易记录方法设置为 *[!UICONTROL Sale]*.
1. 下订单，使用 *信用卡*.
1. 从以下位置打开交易记录 [!UICONTROL Admin].
1. 单击 **[!UICONTROL Fetch]** 按钮。
1. Check [!DNL PayPal] 与下单相关的交易记录的帐户。

<u>预期结果</u>：

未创建新的付款交易记录。

<u>实际结果</u>：

为已支付的订单创建新的付款交易记录。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
