---
title: 'ACSD-45675：产品导出使用默认商店视图范围内的类别名称'
description: ACSD-45675修补程序修复了产品导出使用默认商店视图范围内的类别名称的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20后，即可使用此修补程序。 修补程序ID为ACSD-45675。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: 9edd718e-4c0c-44dd-b802-07c9ec7c182a
feature: Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-45675：产品导出使用默认商店视图范围内的类别名称

ACSD-45675修补程序修复了产品导出使用默认商店视图范围内的类别名称的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.20。 修补程序ID为ACSD-45675。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品导出使用默认商店视图范围内的类别名称。

<u>重现问题的步骤</u>：

1. 创建自定义商店视图 **[!UICONTROL Thai]** 在主商店内。
1. 制作 **[!UICONTROL Thai]** 主网站的默认商店视图。
1. 在下创建以下类别结构 **[!UICONTROL Default Category]**：

   *[!UICONTROL Default category/Tea/Black]*

1. 选择类别 **[!UICONTROL Tea]** 并更改 **[!UICONTROL Scope]** 到 **[!UICONTROL Thai]**.
1. 设置 **[!UICONTROL Category Name]** 作为 **[!UICONTROL ชาดำ]**.
1. 创建简单产品 **[!UICONTROL SP001]** 并分配类别 **[!UICONTROL Black]**.
1. 确保cron不运行。
1. 执行产品导出。 按SKU筛选并选择 **[!UICONTROL SP001]**.
1. 查看 **[!UICONTROL categories]** 列中的“禁止页面加载闪烁”字段。

<u>预期结果</u>：

由于在导出期间未选择任何存储，因此您应获得如下类别路径： *[!UICONTROL Default Category/Tea/Black]*.

<u>实际结果</u>：

类别路径包含混合语言： *[!UICONTROL Default Category/ชาดำ/Black]*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tools] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在“Quality Patches Tool（质量修补程序工具）”指南中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) 在我们的支持知识库中。

有关中可用的其他修补程序的信息 [!DNL QPT]，请参阅 [中提供的修补程序 [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在“Quality Patches Tool（质量修补程序工具）”指南中。
