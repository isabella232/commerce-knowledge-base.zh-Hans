---
title: '''ACSD-56635：将帐户共享设置为时，会复制导入的客户 [!DNL Global]’'
description: 应用ACSD-56635补丁程序，以修复在帐户共享设置为的情况下使用导入时，导入的客户使用同一电子邮件地址复制的Adobe Commerce问题 [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: 86d752c9c2791ef19960876afafe24fefe5d29ed
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635：将帐户共享设置为时，导入的客户将使用相同的电子邮件地址进行复制 [!DNL Global]

ACSD-56635修补程序修复了在将导入用于帐户共享设置为 [!DNL Global]. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.48。 修补程序ID为ACSD-56635。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将帐户共享设置为时，导入的客户将使用相同的电子邮件地址进行复制 [!DNL Global].

<u>重现问题的步骤</u>：

1. 在Adobe Commerce（2.4 — 开发b2b）下 **[!UICONTROL Admin]**，访问 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. 设置 *[!UICONTROL Share Customer Accounts]* 将设置为 *[!DNL Global]*.
1. 创建多个网站和商店：

   * ws1 > s11， s12 > sw111， sw122
   * ws2 > s21， s22 > sw211， sw212

1. 在下创建新客户 *主网站* 发件人管理员，其电子邮件地址用作 <adb@yormail.com>.
1. 下 **[!UICONTROL Admin]**，导航到 **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. 选择 **[!UICONTROL Customer Entity Type]** 作为 *[!UICONTROL Customers Main File]*.
1. 使用与相同的电子邮件地址 <adb@yormail.com> 在其他网站上，例如ws1。 请参阅下面给出的示例CSV文件customer.csv 。
1. 完成导入以查看在 *ws1* 具有相同电子邮件地址的网站。

customer.csv内容：

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>预期结果</u>：

会更新具有相同电子邮件地址的导入客户，而不是进行重复。

<u>实际结果</u>：

使用客户导入时，会使用相同的电子邮件地址创建重复客户。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
