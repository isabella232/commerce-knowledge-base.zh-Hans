---
title: “ACSD-48204：根据*是/否*属性创建的目录价格规则不考虑选定的范围”
description: 应用ACSD-48204补丁程序，以修复基于*是/否*属性创建的目录价格规则不考虑所选范围的Adobe Commerce问题。
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204：目录价格规则创建于 *是/否* 属性不考虑选定的范围

ACSD-48204修补程序修复了以下问题：所创建的目录价格规则基于 *是/否* 属性不考虑选定的范围。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.28。 修补程序ID为ACSD-48204。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

目录价格规则创建于 *是/否* 属性不考虑选定的范围。

<u>重现问题的步骤</u>：

1. 创建两个网站（默认网站和W2网站）。
1. 创建产品属性 *是/否* 类型。
   * 设置 [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. 基于具有两个变体（V1和V2）的任意属性创建可配置产品。
   * 添加 *是/否* 可配置变体属性集的属性
   * 对于变体(V1)之一，将值设置为 *[!UICONTROL Yes]* 在非默认网站(W2)上
1. 创建目录规则：
   * 应用于两个网站
   * 条件： *是/否* 属性值是 *[!UICONTROL Yes]*
   * 折扣= 50%
1. 在非默认网站(W2)上打开可配置产品。
1. 检查V1变量是否应用了50%的折扣。
1. 在Adobe Commerce管理员中打开V1变体。
   * 切换到默认网站
   * 不做更改并保存产品
1. 刷新可配置产品的店面页面。

<u>预期结果</u>：

由于未进行任何更改，V1变量仍应用50%的折扣。

<u>实际结果</u>：

折扣将消失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
