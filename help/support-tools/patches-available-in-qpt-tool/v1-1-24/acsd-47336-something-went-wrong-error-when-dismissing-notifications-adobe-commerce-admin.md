---
title: '''ACSD-47336： [!UICONTROL Something went wrong] 在Adobe Commerce Admin`中取消通知时出错'
description: 应用ACSD-47336修补程序以修复用户看到的Adobe Commerce问题 [!UICONTROL Something went wrong] 在中取消通知时出错 [!DNL Commerce] 管理员。
exl-id: 7561f055-ce04-4a49-8c58-271c24420a60
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336： _[!UICONTROL Something went wrong]_在Adobe Commerce管理中取消通知时出错

ACSD-47336修补程序修复了用户看到 _[!UICONTROL Something went wrong]_在中取消通知时出错 [!DNL Commerce] 管理员。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.24。 修补程序ID为ACSD-47336。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法）： 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）： 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户看到 _[!UICONTROL Something went wrong]_在中取消通知时出错 [!DNL Commerce] 管理员。

<u>重现问题的步骤</u>：

1. 执行批量操作（例如，从产品网格批量更新产品属性）。
1. 完成操作(例如，运行 `bin/magento queue:consumer:start product_action_attribute.update`)。
1. 刷新 [!DNL Commerce] 管理页面，展开管理通知部分，然后单击 **[!UICONTROL Dismiss All Completed Tasks]** 链接。

<u>预期结果</u>：

此 _[!UICONTROL Something went wrong]_清除已完成的任务时不应显示错误。

<u>实际结果</u>：

此 _[!UICONTROL Something went wrong]_将显示错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
