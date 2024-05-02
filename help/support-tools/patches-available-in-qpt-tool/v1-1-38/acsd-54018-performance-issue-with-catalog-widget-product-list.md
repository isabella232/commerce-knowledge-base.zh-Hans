---
title: 'ACSD-54018：目录小组件产品列表出现性能问题'
description: 应用ACSD-54018修补程序以修复在添加具有条件和属性类型布尔值的目录小部件产品列表时页面加载缓慢的Adobe Commerce问题。
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018：目录小部件产品列表出现性能问题

ACSD-54018修补程序修复了在添加具有条件和属性类型布尔值的目录小部件产品列表时页面加载缓慢的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.38。 修补程序ID为ACSD-54018。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

添加具有条件和属性类型布尔值的目录小部件产品列表时，页面加载缓慢。

<u>重现问题的步骤</u>：

1. 生成10万个产品。
1. 创建范围设置为的布尔属性 [!UICONTROL Store View].
1. 将属性分配给所有属性集。
   * 分配属性值 *是* 所有产品。
1. 现在转到 **[!UICONTROL Catalog]** > **[!UICONTROL Products]**，并选择所有100,000个产品。
   * 选择 **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * 将bool属性设置为 *是* 并保存它。
   * 如果您已在此步骤中注销，请检查 *注释*.
1. 转到CLI并运行 `php bin/magento queue:con:start product_action_attribute.update`.
   * 确保所有产品的属性都已更新。
1. 现在转到 **[!UICONTROL Content]** > **[!UICONTROL Pages]** 并创建新页面。
1. 打开 **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. 选择 *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. 设置条件 *[!UICONTROL Created attribute]* 到 *[!UICONTROL Yes]* 并保存它。
1. 转到前端并打开创建的页面。
1. 禁用全页缓存并阻止html缓存。
1. 检查页面加载速度。
1. 重新加载页面几次，并计算平均加载时间。

<u>预期结果</u>：

页面加载速度快。

<u>实际结果</u>：

加载页面需要5 - 10秒。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
