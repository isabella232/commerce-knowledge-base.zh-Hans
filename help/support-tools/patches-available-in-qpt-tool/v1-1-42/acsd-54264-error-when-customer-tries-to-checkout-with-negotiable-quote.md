---
title: 'ACSD-54264：客户尝试使用可转让报价结帐时出错'
description: 应用ACSD-54264修补程序以修复Adobe Commerce问题，该问题导致出现错误消息“您无法更新所请求的属性。 当客户尝试从其他商店视图中用可转让报价结帐时，将显示行ID：store_id。
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264：客户尝试使用可转让报价结帐时出现错误

ACSD-54264修补程序修复了错误消息的问题 *无法更新请求的属性。 行ID：store_id* 当客户尝试使用另一商店视图中的可转让报价结帐时显示。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.42。 修补程序ID为ACSD-54264。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误消息 *无法更新请求的属性。 行ID：store_id* 当客户尝试使用另一商店视图中的可转让报价结帐时显示。

<u>先决条件</u>：

Adobe Commerce B2B模块已安装和启用。

<u>重现问题的步骤</u>：

1. 为默认网站创建其他商店视图。
1. 启用 *[!UICONTROL B2B Quote]* 在配置中。
1. 以公司客户身份登录其中一个商店视图。
1. 将产品添加到 *[!UICONTROL Shopping Cart]*.
1. 提交报价以供审查。
1. 作为管理员用户，请访问 **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** 并提交已批准的报价。
1. 作为公司客户，将商店视图更改为其他商店视图。
1. 试试看吧。

<u>预期结果</u>：

客户使用此报价单下订单。

<u>实际结果</u>：

* 保存配送信息时出现错误：

  `You cannot update the request attribute. Row ID: store_id =#`

* 将记录以下错误：

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
