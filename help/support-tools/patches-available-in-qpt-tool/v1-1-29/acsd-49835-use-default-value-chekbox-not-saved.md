---
title: 'ACSD-49835： [!UICONTROL Use Default Value] 复选框未保存'
description: 应用ACSD-49835修补程序以修复Adobe Commerce问题，其中 [!UICONTROL Use Default Value] 复选框未在多选属性的存储级别上正确保存。
exl-id: 84270551-c8a9-4b08-a055-ffdcc538c33d
feature: Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-49835： [!UICONTROL Use Default Value] 复选框未保存

ACSD-49835修补程序修复了 [!UICONTROL Use Default Value] 复选框未在多选属性的存储级别上正确保存。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.29。 修补程序ID为ACSD-49835。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此 [!UICONTROL Use Default Value] 复选框未在多选属性的存储级别上正确保存。

<u>重现问题的步骤</u>：

1. 创建 **[!UICONTROL Multiple-select Attribute]** 在 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 并将其添加到属性集。
1. 转到 **[!UICONTROL Product]** 并保存 **[!UICONTROL Values]** 在 **[!UICONTROL All Store Views (Default Scope)]**.
1. 转到特定 **[!UICONTROL Store View Scope]** 并保存产品。
1. 转到 **[!UICONTROL Store View Scope]** 并查看 **[!UICONTROL Use Default Value]** 复选框。

<u>预期结果</u>：

复选属性值在选中时正确保存 [!UICONTROL Use Default Value] 中的复选框 [!UICONTROL Store View Scope].

<u>实际结果</u>：

复选属性值在检查时未正确保存 [!UICONTROL Use Default Value] 中的复选框 [!UICONTROL Store View Scope].

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
