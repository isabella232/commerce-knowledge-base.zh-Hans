---
title: “ACSD-48404： *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]*导致按浏览器的后退按钮时出错”
description: 应用ACSD-48404修补程序以修复以下位置的Adobe Commerce问题：*[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]*导致按浏览器的后退按钮时出错。
exl-id: b4b96198-dee6-4b3c-b60a-0983ef8ef7b2
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-48404： *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 导致按浏览器的后退按钮时出错

ACSD-48404修补程序修复了以下问题 *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 导致按浏览器的后退按钮时出错。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.27。 修补程序ID为ACSD-48404。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* 导致按浏览器的后退按钮时出错。


<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**，并设置 *[!UICONTROL Remember Category Pagination]* 到 *是*.
1. 在店面打开一个类别。
1. 选择一个非缺省值的值 *[!UICONTROL Show Per Page]* 下拉菜单。 选择某个选项后，页面将重新加载。
1. 重新加载页面后，单击目录页面上的任何产品。
1. 在打开的产品详细信息页面上，单击 **[!UICONTROL Back]** 按钮进行更改。

<u>预期结果</u>：

目录页面再次打开。

<u>实际结果</u>：

类别页面返回错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
