---
title: 'ACSD-56886：子产品禁用时，可配置产品缺货'
description: 应用ACSD-56886补丁以修复在禁用产品时可配置产品缺货子项的Adobe Commerce问题。
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886：禁用子产品后，可配置产品将缺货

ACSD-56886修补程序修复了在禁用子产品时，可配置产品缺货的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.45。 修补程序ID为ACSD-56886。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

禁用子产品后，可配置产品将缺货。

<u>重现问题的步骤</u>：

1. 以管理员身份登录。
1. 设置中的所有索引器 **[!UICONTROL Update By Schedule]** 模式。
1. 创建以下可配置产品：

   * 名称= *测试可配置1*
   * 属性= *颜色*
   * 值= *红色* 和 *black*
   * 的价格 **红色**  子产品= *100美元*；
   * “黑色”子产品的价格= *200美元*.

1. 为可配置产品创建以下计划更新：

   * 开始日期= *3* 几分钟后。
   * 结束日期= *5* 开始日期后的分钟数。
   * 产品名称= *已编辑测试可配置1*.
   * 禁用 **红色** 子产品位于 **可配置** 部分。

1. 等待开始日期。
1. 在Storefront上打开可配置产品的详细信息。

<u>预期结果</u>：

可配置产品显示为 **有货** 使用 **低至200** 标签。

<u>实际结果</u>：

可配置产品显示为 **缺货**.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
