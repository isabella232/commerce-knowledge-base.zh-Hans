---
title: 'ACSD-56546：可配置和捆绑产品在店面显示为缺货'
description: 应用ACSD-56546修补程序以修复Adobe Commerce问题，该问题导致当出现以下情况时，可配置和捆绑产品在店面显示为缺货*[!UICONTROL Display Out of Stock Products]*配置选项已禁用。
feature: Storefront, Products
role: Admin, Developer
exl-id: 488e2c69-442f-45e1-aa8f-71d9c0a93950
source-git-commit: 031d5cad6727bac61c88f21fa7c84e0d2a6df331
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546：可配置和捆绑产品在店面显示为缺货

ACSD-56546修补程序修复了可配置和捆绑产品在店面显示为缺货的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.48。 修补程序ID为ACSD-56546。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当出现以下情况时，可配置和捆绑产品会在店面显示为缺货 *[!UICONTROL Display Out of Stock Products]* 选项已禁用。

<u>重现问题的步骤</u>：

1. 设置 **[!UICONTROL Display Out of Stock Products]** 选项至 *否*.
1. 创建网站、商店和商店评论。
1. 创建源和库存，然后将其分配给第二个网站。
1. 创建 *可配置产品* 两个子产品。 将子产品同时分配给源和两个网站。
1. 将第一个子产品更新为 *数量=0* 两个来源中。
1. 更新第二个子产品并在第二个网站上禁用它。
1. 执行完整的重新索引。
1. 选中第二个网站上包含可配置产品的类别。

<u>预期结果</u>：

缺货的可配置产品在店面不可见。

<u>实际结果</u>：

店面中可以看到缺货的可配置产品，即使在 *[!UICONTROL Display Out of Stock Products]* 选项已禁用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
