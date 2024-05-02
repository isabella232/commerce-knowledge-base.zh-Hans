---
title: '''ACSD-55305：在中编辑公司用户时弹出窗口冻结 [!UICONTROL My Account]’'
description: 应用ACSD-55305修补程序以修复Adobe Commerce问题，其中 [!UICONTROL Edit Company User] 上的弹出窗口 [!UICONTROL My Account] &gt； [!UICONTROL Company Structure] 屏幕上有加载器时会冻结页面。
feature: Companies, B2B
role: Admin, Developer
exl-id: be2bfe08-d05e-485d-84c3-2ff14e1a8654
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-55305：在中编辑公司用户时弹出窗口冻结 [!UICONTROL My Account]

ACSD-55305修补程序修复了以下问题  [!UICONTROL Edit Company User] 上的弹出窗口 [!UICONTROL My Account]> [!UICONTROL Company Structure] 屏幕上有加载器时会冻结页面。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.43。 修补程序ID为ACSD-55305。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

尝试使用 *[!UICONTROL Edit Company User]* 上的弹出窗口 *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* 页面时，它会随着屏幕上显示的加载器而冻结。

<u>重现问题的步骤</u>：

1. 创建一个B2B公司。
1. 为客户创建多选属性。
1. 为新创建的公司管理员属性分配一个值。
1. 以公司管理员身份登录。
1. 转到 [!UICONTROL account dashboard] 并导航至 **[!UICONTROL Company Structure]**.
1. 选择用户。
1. 单击 **[!UICONTROL Edit Selected]**.

<u>预期结果</u>：

表单弹出窗口会准确显示，并提供编辑公司信息的选项。

<u>实际结果</u>：

此时会出现表单弹出窗口，且无法进行任何编辑。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。