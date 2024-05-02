---
title: '''ACSD-51408：订单项目状态错误地设置为 [!UICONTROL backordered]’'
description: 应用ACSD-51408修补程序以修复订单项状态错误设置为的Adobe Commerce问题 [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
exl-id: 0355beca-4612-438f-8f91-be42d8d637e9
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# ACSD-51408：订单项目状态错误地设置为 *[!UICONTROL backordered]*

ACSD-51408修补程序修复了订单项状态错误设置为的问题 [!UICONTROL backordered]. 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.33。 修补程序ID为ACSD-51408。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订单项目状态错误地设置为 *[!UICONTROL backordered]*.

<u>先决条件</u>：

已安装Adobe Commerce B2B和Inventory management (MSI)模块。

<u>重现问题的步骤</u>：

1. 创建新网站、商店和商店视图。
1. 创建新源。
1. 创建链接到在步骤1中创建的新网站的新库存，并分配在步骤2中创建的源。
1. 创建公司并将其分配给在第1步中创建的新网站。
1. 创建新客户并将其分配给在步骤4中创建的公司。
1. 创建一个产品，将其分配给新网站，然后设置 **[!UICONTROL default stock]** = *0*，和 **[!UICONTROL new stock]** 大于 *0*.
1. 启用 **[!UICONTROL backorders]**.
1. 启用 **[!UICONTROL Check/Money Order]** 新网站范围的支付方式。
1. 启用 **[!UICONTROL Flat Rate shipping method]** 用于新网站范围。
1. 从创建新订单 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. 选择在步骤5中创建的新客户。
1. 选择在步骤1中创建的新存储。
1. 选择在步骤6中创建的产品。
1. 填写订单信息，包括付款和运送方式。
1. 提交订单。
1. 查看 *项目状态*.

<u>预期结果</u>

可从库存中发运物料。 项目状态为 *[!UICONTROL ordered]*.

<u>实际结果</u>

项目状态为 *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[订单项目状态错误地设置为 *[!UICONTROL Ordered]* 当产品库存为0时。](/help/support-tools/patches-available-in-qpt-tool/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
