---
title: 'ACSD-56760：管理员用户仅限访问特定网站，无法排序或添加新产品'
description: 应用ACSD-56760修补程序以修复Adobe Commerce问题：该问题导致管理员用户仅限于访问特定网站，如果网络商店拥有自己的根类别，则该用户无法对类别进行排序或添加新产品。
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760：管理员用户仅限访问特定网站，无法排序或添加新产品

ACSD-56760修补程序修复了以下问题：管理员用户被限制在特定网站，如果网络商店拥有自己的根类别，则无法在类别中排序或添加新产品。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.47。 修补程序ID为ACSD-56760。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

仅限特定网站的管理员用户，如果网络商店拥有自己的根类别，该用户无法在类别中排序或添加新产品。

<u>重现问题的步骤</u>：

1. 创建 *2* 网站。
1. 创建 **[!UICONTROL restricted admin user]** 只能访问 *1* 网站。
1. 登录身份 **[!UICONTROL restricted admin user]** 并尝试更改某个类别中的产品位置。

*用例1*：

* *2* 商店。
* *2* 根类别，每个网站都分配给自己的类别根。

*用例2*：

* *2* 商店。
* 仅 *1* 根类别同时分配给两个网站。

<u>预期结果</u>：

* *用例1*：受限管理员应该能够对可用类别中的产品进行排序。
* *用例2*：受限管理员无法对可用类别中的产品进行排序，因为这样也会影响受限商店。

<u>实际结果</u>：

* *用例1*：受限管理员无法对可用类别中的产品进行排序。
* *用例2*：受限管理员可以对可用类别中的产品进行排序，从而影响受限商店。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
