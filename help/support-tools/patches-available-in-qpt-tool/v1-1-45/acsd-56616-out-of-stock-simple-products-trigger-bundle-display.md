---
title: 'ACSD-56616：在简单库存短缺期间捆绑产品的店面展示'
description: 应用ACSD-56616补丁以修复以下问题：当所有关联的简单产品缺货时，Adobe Commerce店面会意外显示捆绑产品。
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616：在简单库存短缺期间捆绑产品的店面展示。

ACSD-56616修补程序修复了以下问题：当所有关联的简单产品都缺货时，店面中会意外出现捆绑产品。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.45。 修补程序ID为ACSD-56616。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

简单库存短缺期间捆绑产品的店面显示不正确。

<u>重现问题的步骤</u>：

1. 创建新网站/商店/店面。
1. 创建新源。
1. 创建新库存，并将其分配给新创建的网站。
1. 配置索引器以按计划更新。
1. 生成两个简单产品S1 （数量= 1）和S2 （数量= 1），并将它们分配给新库存和新网站。
1. 创建 *捆绑1* 并将其与新网站关联，然后将其放入类别 *CAT*.
1. 定义两个必需的下拉列表选项并链接简单产品 *S1* to option1和 *S2* 到选项2。
1. 保存产品。
1. 导航到 **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** 并启用 *将商店代码添加到URL* = *是*.
1. 打开店面并购买捆绑产品。
1. 运行两次压缩。
1. 返回到 *CAT* 类别。

<u>预期结果</u>：

此 *bundle1* 产品缺货。

<u>实际结果</u>：

此 *bundle1* 产品可见，价格= *$0*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
