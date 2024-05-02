---
title: 'ACSD-49706：未选择任何值时为可视样本属性保存的默认值'
description: 应用ACSD-49706修补程序以修复在未选择任何值时为可视样本属性保存默认值的Adobe Commerce问题。
exl-id: fe6071df-f2a4-443a-acfa-67f3d253c5e4
feature: Admin Workspace, Attributes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-49706：未选择任何值时为可视样本属性保存的默认值

ACSD-49706修补程序修复了在未选择任何值时为可视样本属性保存默认值的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.29。 修补程序ID为ACSD-49706。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果未选择任何值，则会为可视样本属性保存默认值。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. 单击 **[!UICONTROL Add New Attribute]**.
1. 填写字段。

   * 例如，选择输入类型 *[!UICONTROL Visual Swatch]*，并添加多个选项(例如 *红色*， *绿色*)。 请确保选择其中一个选项作为默认选项。
   * 单击 **[!UICONTROL Save Attribute]**.

1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. 编辑 *[!UICONTROL Default]* 属性集。
1. 移动 *[!UICONTROL New Attribute]* 从列 *[!UICONTROL Unassigned Attributes]* 到 *[!UICONTROL Product Details]* 中间的列中的文件夹。

   * 单击 **[!UICONTROL Save]**.

1. 使用创建新产品 *[!UICONTROL Default]* 属性集。

   * 离开 *[!UICONTROL New Attribute]* 清空并保存。

1. 保存后，值将显示在 *[!UICONTROL New Attribute]*.

<u>预期结果</u>：

未将值分配给 *[!UICONTROL New Attribute]* 默认情况下。

<u>实际结果</u>：

在保存产品时，默认值将应用于属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
