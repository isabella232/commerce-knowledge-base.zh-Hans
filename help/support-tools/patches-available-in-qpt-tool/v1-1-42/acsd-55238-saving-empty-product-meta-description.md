---
title: 'ACSD-55238：保存空的产品元描述'
description: 应用ACSD-55238修补程序以修复Adobe Commerce问题，该问题导致产品描述中包含由生成的HTML代码 [!DNL Page Builder] 或者元描述中始终显示另一个HTML编辑器，并且无法将其设置为空。
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238：保存空的产品元描述

ACSD-55238修补程序修复了元描述中始终显示包含HTML编辑器生成的HTML代码的产品描述的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.42。 修补程序ID为ACSD-55238。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

包含由生成的HTML代码的产品说明 [!DNL Page Builder] 或者元描述中始终显示另一个HTML编辑器，并且无法将其设置为空。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** 并创建包含任何内容的新块。
1. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** 并创建一个新产品。 将元描述设置为空。
1. 添加上面创建的块，使用 *[!DNL Page Builder]* 在 *[!UICONTROL Content]* 制表符并保存产品。
1. 在店面打开产品并检查其文档元素 `meta name = "description"`.

<u>预期结果</u>：

元描述为空。

<u>实际结果</u>：

当产品的描述中有块时，它用于产品元描述。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
