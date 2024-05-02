---
title: 'ACSD-51102：应用于大量产品的目录规则未正确索引'
description: 应用ACSD-51102修补程序以修复Adobe Commerce问题：当计划更新启用了应用于大量产品的目录规则时，该规则无法正确编制索引。
feature: Catalog Management, Products
role: Admin
exl-id: 5c1c5f9c-9cce-4b11-8058-0e12a4bf93fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-51102：应用于大量产品的目录规则未正确编制索引

ACSD-51102修补程序修复了以下问题：当计划更新启用了应用于大量产品的目录规则时，该规则无法正确编制索引。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.33。 修补程序ID为ACSD-51102。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

计划更新启用了应用于大量产品的目录规则时，该规则无法正确编制索引。

先决条件：

* Cron作业已设置并每分钟运行一次。

<u>重现问题的步骤</u>：

1. 创建一个包含数千种产品的大型目录，以实现 *目录规则* 启用目录规则时超过120秒的索引器。
2. 使用以下方式创建两个目录规则 *活动* 状态设置为 *否*.  例如， *测试1* 和 *测试2*. 每个规则都应影响目录中的所有产品，并导致索引器运行超过120秒。
3. 确保索引器的状态为 *就绪*.
4. 创建计划更新以启用这两个规则。 *测试2* 计划应于以下时间后不久开始 *测试1*. 例如，差异为1分钟。
5. 检查店面的产品价格。

<u>预期结果</u>

将应用这两个规则的折扣。

<u>实际结果</u>

仅应用第一个规则折扣。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) 在 [!DNL Quality Patches Tool] 指南。
