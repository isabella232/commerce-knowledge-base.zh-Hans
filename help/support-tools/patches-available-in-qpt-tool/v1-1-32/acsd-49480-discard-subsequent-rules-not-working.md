---
title: 'ACSD-49480：放弃后续规则不起作用'
description: 应用ACSD-49480修补程序以修复Adobe Commerce问题，其中 [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 未按预期工作。
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480： [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 未按预期工作

ACSD-49480修补程序修复了 [!UICONTROL Cart Price Rule - Discard Subsequent Rules] 未按预期工作。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.32。 修补程序ID为ACSD-49480。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] 未按预期工作。

<u>重现问题的步骤</u>：

1. 创建 **[!UICONTROL Cart Price Rule]** 带有优惠券代码(将其命名为 *测试*)可给您十美元的折扣， *产品ID 1* 在 **[!UICONTROL Actions]** 制表符 [!UICONTROL Discard Subsequent Rules] 设置为 *[!UICONTROL Yes]* 和 [!UICONTROL Priority] 设置为 *1*.
1. 创建另一个 **[!UICONTROL Cart Price Rule]** 没有优惠券代码，给予$5的折扣 *产品ID 2* 在 **[!UICONTROL Actions]** 制表符 [!UICONTROL Priority] 设置为 *2*. 在此，我们假设，这是一次全球性的销售， *产品ID 2*.
1. 转到前端网站并添加 *产品ID 1* 和 *产品ID 2* 放入购物车。
1. 应用 *测试* 优惠券代码。

<u>预期结果</u>

* *折扣1* 应用于 *产品ID 1*.
* *折扣2* 应用于 *产品ID 2*.

<u>实际结果</u>

* 仅 *折扣1* 应用于 *产品ID 1*.
* *折扣2* 未应用于 *产品ID 2*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
