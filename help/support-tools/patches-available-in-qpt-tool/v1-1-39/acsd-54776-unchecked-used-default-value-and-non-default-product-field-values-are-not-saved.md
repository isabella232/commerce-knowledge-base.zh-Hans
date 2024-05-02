---
title: 'ACSD-54776：未选中 [!UICONTROL Use Default Value] 对于第二个网站、商店和商店视图，不会保存非默认产品字段值'
description: 应用ACSD-54776修补程序以修复未选中的Adobe Commerce问题 [!UICONTROL Use Default Value] 对于第二个网站、商店和商店视图，和非默认产品字段值不会保存。
feature: Products
role: Admin, Developer
exl-id: 5bdad804-8d7b-48b4-ba3b-c2d5387ef55e
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-54776：未选中 *[!UICONTROL Use Default Value]* 和非默认产品字段值未保存

>[!NOTE]
>
>此修补程序将取代 [ACSD-51984](/help/support-tools/patches-available-in-qpt-tool/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) QPT 1.1.35中发布的修补程序。

ACSD-54776修补程序修复了未选中该复选框的问题 **[!UICONTROL Use Default Value]** 对于第二个网站、商店和商店视图，和非默认产品字段值不会保存。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.39。 修补程序ID为ACSD-54776。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p4、2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

未选中 *[!UICONTROL Use Default Value]* 对于第二个网站、商店和商店视图，和非默认产品字段值不会保存。

<u>重现问题的步骤</u>：

1. 转到后端并导航到 **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** 并创建新网站、商店和商店视图。
1. 转到 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**，创建一个简单产品并进行保存，然后从将产品分配给两个网站 **[!UICONTROL Product in Websites]**.
1. 从步骤2将范围更改为新创建的存储视图。
1. 转到 **[!UICONTROL Search Engine Optimization]** 并取消选中 **[!UICONTROL Use Default Value]** 复选框 [!UICONTROL Meta Title]， [!UICONTROL Meta Keywords]、和 [!UICONTROL Meta Description].
1. 清除字段中的文本： *[!UICONTROL Meta Title]*， *[!UICONTROL Meta Keywords]* 和 *[!UICONTROL Meta Description]*，然后单击 **[!UICONTROL Save]**.
1. 转到 **[!UICONTROL Search Engine Optimization]** 再来一次。

<u>预期结果</u>

将保存字段和复选框的值。

<u>实际结果</u>

未保存字段和复选框的值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
