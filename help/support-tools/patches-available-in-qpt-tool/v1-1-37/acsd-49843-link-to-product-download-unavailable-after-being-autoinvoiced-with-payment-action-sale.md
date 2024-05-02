---
title: '''ACSD 49843：使用自动开票后，产品下载链接不可用 [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]’'
description: Adobe Commerce应用ACSD-49843修补程序以修复以下问题：在下列情况下，通过在线付款方式自动对订购项目开票后，产品下载链接不可用 [!UICONTROL Payment Action] 设置为 [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: 4bfa3827-a2b1-4168-a39c-99c617ee4795
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# ACSD-49843：使用自动开票后，产品下载链接不可用 [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

ACSD-49843修补程序修复了在以下情况下对订购项目自动开票后产品下载链接不可用的问题： [!UICONTROL Payment Action] 设置为 [!UICONTROL Intent Sale]. 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.37。 修补程序ID为ACSD-49843。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在以下情况下，通过在线付款方法自动对订购项目开票后，产品下载链接不可用： [!UICONTROL Payment Action] 设置为 [!UICONTROL Intent Sale].

<u>重现问题的步骤</u>：

1. 登录到Adobe Commerce管理员并导航到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * 在 [!UICONTROL Payment Action] 下拉列表，选择 **[!UICONTROL Intent Sale]**，并设置 *[!UICONTROL Enable Card Payments]* 到 *是*.

1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**，并确保将其设置为 *“已开发票”*.
1. 在店面，以客户身份登录。

   * 将任何可下载的产品和简单产品添加到购物车。
   * 使用 [!DNL Braintree Pay] 使用卡选项下订单。

1. 转到 **[!UICONTROL My Orders]** 并且查看系统会自动为订单创建发票，并且物料状态均为 *“已开发票”*.
1. 转到 **[!UICONTROL My Downloadable Products]** 并观察下载链接是否不可用。
1. 在“管理员”中，转至该订单并为其创建装运。
1. 在店面，去 **[!UICONTROL My Downloadable Products]** 并观察下载链接现在是否可用。

<u>预期结果</u>：

当可下载的产品状态为“ ”时，下载链接可用 *“已开发票”*.

<u>实际结果</u>：

即使可下载的产品状态显示为“Download Link（下载链接）”，该链接也不可用 *“已开发票”*. 只有在为实物产品创建装运后，它才可用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
