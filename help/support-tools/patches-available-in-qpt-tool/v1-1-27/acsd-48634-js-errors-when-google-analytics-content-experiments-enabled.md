---
title: 'ACSD-48634： [!DNL JS] 发生以下情况时出错： [!DNL Google Analytics Content Experiments] 已启用'
description: 应用ACSD-48634修补程序进行修复 [!DNL JS] 上的错误 [!DNL staging] 更新页面时间 [!DNL Google Analytics Content Experiments] 已启用。
exl-id: 4a9f201d-eaf0-4e43-a1a1-0a9ffb0a2ead
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-48634： [!DNL JS] 发生以下情况时出错： [!DNL Google Analytics Content Experiments] 已启用

ACSD-48634修补程序修复 [!DNL JS] 上的错误 [!DNL staging] 更新页面时间 [!DNL Google Analytics Content Experiments] 已启用。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.27。 修补程序ID为ACSD-48634。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!DNL JS] 发生错误 [!DNL staging] 更新页面时间 [!DNL Google Analytics Content Experiments] 已启用。

<u>重现问题的步骤</u>：

1. 在 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**、创建其他网站、商店和 **[!UICONTROL Store View]**. 确保 **[!UICONTROL Store View]** 是 *[!UICONTROL Enabled]*.
1. 配置 **[!DNL Configure Google Analytics]** 通过转到 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**：
   * 对象 **[!DNL Main]** 和其他网站 [!DNL scope]：
      * **[!UICONTROL Enabled]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**： *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**： *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* 用于其他字段，但请勿更改它们。
   * 对象 **[!DNL Default Config]** [!DNL scope]：
      * **[!UICONTROL Enabled]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**： *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**： *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**： *[!UICONTROL Yes]*
1. 禁用 **[!DNL Configure Google Analytics]** 日期 **[!DNL Default Config]** [!DNL scope] 通过更改 **[!UICONTROL Enable]** 从 *[!UICONTROL Yes]* 到 *[!UICONTROL No]*. 确保不更改其他任何内容！
1. 转到 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. 创建和编辑任意 **[!UICONTROL category]** 并为其添加计划的更新：
   * 任何名称、将来的开始日期、将来的结束日期以及中的任何更改 **[!UICONTROL category]** ([!UICONTROL For Example]： *[!UICONTROL disable category]*)。
1. 保存更新并检查 [!DNL browser developer console] 错误。

<u>预期结果</u>：

否 [!DNL JS] 错误以及对 [!DNL staging] 更新保存成功。

<u>实际结果</u>：

[!DNL JS] 控制台中会显示错误，表单格式不正确，并且 [!DNL spinner] 保存后从不禁用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
