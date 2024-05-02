---
title: 'ACSD-48362：使用默认送货地址而不是新送货地址。'
description: 应用ACSD-48362修补程序以修复以下问题：在使用可转让报价下订单时，使用Adobe Commerce的默认送货地址而不是新送货地址。
exl-id: 52f518b6-6f73-42cc-ac1b-c893cd5007fa
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-48362：使用默认送货地址而不是新送货地址

ACSD-48362修补程序修复了在使用可协商的报价下订单时使用默认送货地址而不是新添加的地址的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.27。 修补程序ID为ACSD-48362。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用可转让报价下订单时，将使用默认送货地址而不是新添加的送货地址。

<u>重现问题的步骤</u>：

1. 通过导航到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]**.
1. 以公司用户身份登录。
1. 将产品添加到购物车。
1. 转到购物车页面并请求报价。
1. 转到客户的 **[!UICONTROL My Quotes]** 页并选择刚创建的报价。
1. 转到 **[!UICONTROL Shipping Information]** 部分。
   * 单击 **[!UICONTROL Add New Address]**，填写表单并保存地址(请勿选择 **[!UICONTROL Use as my default billing address]** 或 **[!UICONTROL Use as my default shipping address]**)。
1. 单击 **[!UICONTROL Send for Review]** 在客户的报价页上。
1. 以管理员用户身份转到Adobe Commerce管理员，打开刚创建的报价，然后单击 **[!UICONTROL Send]**.
1. 现在，转到客户的报价页面，刷新该页面，然后单击 **[!UICONTROL Proceed to Checkout]**.
1. 在结账页面上，即使选择了新的送货地址，数据也会显示默认送货地址。
1. 单击 **[!UICONTROL Continue]** 下订单。

<u>预期结果</u>：

订单应使用新地址，而无需在结账页面上重新选择默认送货地址。

<u>实际结果</u>：

使用默认送货地址下订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。 

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
