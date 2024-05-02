---
title: 'ACSD-52714：日期过滤器设置为y-m-d时在管理网格中不起作用'
description: 应用ACSD-52714修补程序以修复将日期格式设置为y-m-d时，日期过滤器在管理网格中不起作用的Adobe Commerce问题。
feature: Attributes
role: Admin, Developer
exl-id: b292ab2c-e12d-40df-a9ad-19f25fbde5a0
source-git-commit: 513cb47c054dbb907810bbdc3d20d2aca9d5e42b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-52714：将日期过滤器设置为y-m-d时，该过滤器在管理网格中不起作用

ACSD-52714修补程序修复了将日期格式设置为y-m-d时，日期过滤器在管理网格中不起作用的问题。此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.43。 修补程序ID为ACSD-52714。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将日期格式设置为y-m-d时，日期过滤器在管理网格中不起作用。

<u>重现问题的步骤</u>：

1. 安装干净的Adobe Commerce。
1. 编辑
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
文件并添加
   `<dateFormat>Y-MM-dd</dateFormat>`
到
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
在标记下
   `<dataType>date</dataType>`

1. 刷新缓存 `bin/magento c:f`.
1. 登录到管理员并从创建新客户 **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * 起始日期：当前日期减1天
   * 截止日期：当前日期

1. 单击 **[!UICONTROL Apply Filters]**.

<u>预期结果</u>：

网格的日期过滤器工作正常，与区域设置无关。

<u>实际结果</u>：

将显示以下消息： *找不到任何记录*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
