---
title: '''ACSD-51890： [!UICONTROL Submit review] 按钮单击多次'
description: 应用ACSD-51890修补程序以修复Adobe Commerce问题，其中 [!UICONTROL Submit Review] 多次单击按钮，不需要 [!DNL Google reCAPTCHA v3] 验证。
feature: Products
role: Admin
exl-id: f6369a24-24bd-4e5e-a870-a13f507ada94
source-git-commit: 7dbf9a796fe2026b0657b719d10e5bb21b964fb6
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51890： **[!UICONTROL Submit Review]** 多次单击按钮，不需要 **[!DNL Google reCAPTCHA v3]** 验证

>[!NOTE]
>
>此修补程序已替换为 [ACSD-55112](/help/support-tools/patches-available-in-qpt-tool/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md).

ACSD-51890修补程序修复了 **[!UICONTROL Submit Review]** 多次单击按钮，不需要 **[!DNL Google reCAPTCHA v3]** 验证。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.35。 修补程序ID为ACSD-51890。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此 **[!UICONTROL Submit Review]** 单击按钮多次，但无需 **[!DNL Google reCAPTCHA v3]** 验证。

<u>重现问题的步骤</u>：

1. 启用 **[!DNL Google reCAPTCHA v3]** 用于产品审查。
1. 打开产品页面并导航到 **[!UICONTROL Review]** 部分并确保 [!DNL reCAPTCHA] 可见。
1. 填写审阅表单，然后单击 **[!UICONTROL Submit Review]** 按钮执行多次。
1. 打开 **[!UICONTROL Review]** 部分。

<u>预期结果</u>

不会创建重复的审核。

<u>实际结果</u>

创建重复的审核。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
