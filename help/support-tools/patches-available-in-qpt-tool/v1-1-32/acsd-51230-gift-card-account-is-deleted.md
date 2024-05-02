---
title: 'ACSD-51230：已删除礼品卡帐户'
description: 应用ACSD-51230修补程序以修复以下问题：当订单中的简单产品部分退款被处理时，Adobe Commerce帐户会被删除。
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230：已删除礼品卡帐户

ACSD-51230修补程序修复了在订单中处理简单产品的部分退款时删除礼品卡帐户的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.32。 修补程序ID为ACSD-51230。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当从订单中处理简单产品的部分退款时，删除礼品卡帐户。

<u>重现问题的步骤</u>：

1. 使用以下方式创建订单 *礼品卡* 和 *简单产品* (例如， *添加：SKU：GI000XX000XXX，SKU：PC046CP042076*) — （任何付款和运送方式均有效）。
1. 为订单开票。
1. 转到 **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. 为礼品卡创建帐户。
1. 现在转到 **[!UICONTROL Order]**，并创建 **[!UICONTROL Credit Memo]**.
1. 更改的数量 *礼品卡* 更改为0并更新它。 这将导致部分退款 *简单产品*.
1. 单击 **[!UICONTROL Refund]**.
1. 现在刷新 **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. 新创建的帐户将被删除。

<u>预期结果</u>

礼品卡帐户可供使用，因为未为礼品卡创建退款。

<u>实际结果</u>

删除礼品卡帐户，且礼品卡不退款。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
