---
title: 'ACSD-52143：导入产品后删除自定义选项'
description: 应用ACSD-52143修补程序以修复在产品导入后删除自定义选项的Adobe Commerce问题。
feature: Data Import/Export
role: Admin, Developer
exl-id: 7dde1efe-37a3-443f-9ce1-82cf1b3d9da7
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52143：导入产品后删除自定义选项

ACSD-52143修补程序修复了在产品导入后删除自定义选项的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.37。 修补程序ID为ACSD-52143。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

导入产品后，将删除自定义选项。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Store]** > **[!UICONTROL All Stores]**，并设置一个多商店实例（一个网站具有两个商店视图）。
1. 转到 **[!UICONTROL Catalog]** > **[!UICONTROL Products]** 并创建两个产品，用于 [!UICONTROL Customizable Options].
1. 在每个产品中，添加 [!UICONTROL Customizable Option].
1. 切换到第二个商店视图，并修改每个产品的产品名称。
1. 转到 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** 并导出您创建的两个产品。
1. 下载CSV文件。
1. 转到 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** 并重新导入文件。
1. 检查两个产品。

<u>预期结果</u>：

导入产品后未删除自定义选项。

<u>实际结果</u>：

在产品导入后，将删除海关选项。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
