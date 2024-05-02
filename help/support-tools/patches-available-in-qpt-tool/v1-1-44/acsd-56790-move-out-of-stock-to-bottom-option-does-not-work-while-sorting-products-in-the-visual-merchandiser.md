---
title: '''ACSD-56790： **[!UICONTROL move out of stock to bottom]在中对产品进行排序时，**选项不起作用  [!DNL Visual Merchandiser]’'
description: 应用ACSD-56790补丁程序，以修复在可视化促销器中对产品进行分类时，无法正常使用“从缺货到底部”选项的Adobe Commerce问题。
feature: Products, Categories
role: Admin, Developer
exl-id: a0c61696-a12d-4c1a-a061-e2f17f38e1f4
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# ACSD-56790： **[!UICONTROL move out of stock to bottom]** 在中对产品进行排序时，选项不起作用 [!DNL Visual Merchandiser]

ACSD-56790修补程序修复了在对中的产品进行分类时，“从库存移至底部”选项不起作用的问题。 [!DNL Visual Merchandiser]. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.44。 修补程序ID为ACSD-56790。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此 **[!UICONTROL move out of stock to bottom]** 在中对产品进行排序时，选项不起作用 [!DNL Visual Merchandiser]

<u>重现问题的步骤</u>：

1. 安装Adobe Commerce。
1. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 和创建以下属性。
1. 创建新网站： **非主要**.
1. 创建 **非主存储** 在这个新网站上。
1. 创建两个存储：

   * 中的第一个 **主网站商店**.
   * 中的第二个 **非主存储**.

1. 创建两个源：
   * 书信。
   * 数字。

1. 创建两个库存：
   * 第一个主要 — 销售渠道：主要网站 — 分配的来源：信件。
   * 第二个非主要 — 销售渠道：非主要 — 分配的来源：数字。

1. 在两个网站上创建三个简单的产品（全部在“默认”类别中，全部分配给两个源）：

   * 产品A — 数量 *10* 在字母中，数量 *0* 在数字中。
   * 产品1 — 数量 *0* 在字母中，数量 *10* 在数字中。
   * ProductA1 — 数量 *10* 在字母中，数量 *10* 在数字中。

1. 转到 **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** 并选择  **[!UICONTROL Default category]**.
1. 将范围更改为 **第一**.
1. 展开“类别”部分中的产品。
1. 选择排序顺序为： **[!UICONTROL move out of stock to bottom]**

<u>预期结果</u>：

产品列表，具有 **缺货** 将产品移到底部。

<u>实际结果</u>：

产品加载失败。 页面重定向到管理员功能板，并显示错误消息： `Invalid security or form key. Please refresh the page`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
