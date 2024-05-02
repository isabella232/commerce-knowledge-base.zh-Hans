---
title: '''ACSD-48313： [!UICONTROL configurable_variations] 如果属性值包含逗号''，则未分析列'
description: 应用ACSD-48313修补程序以修复Adobe Commerce问题，其中 [!UICONTROL configurable_variations] 如果属性值包含逗号，则不会分析列。
exl-id: 0ac3f8da-4da3-4308-bea4-98a5b6926b0d
feature: Attributes, Configuration
role: Admin
source-git-commit: 4cb43c4f16238253fc7fc75d9af9b921dfa74158
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-48313： **[!UICONTROL configurable_variations]** 如果属性值包含逗号，则不解析列

ACSD-48313修补程序解决了以下问题： **[!UICONTROL configurable_variations]** 如果属性值包含逗号，则不会分析列。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.25。 修补程序ID为ACSD-48313。 将修复此问题的版本尚不可用。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

导出可配置产品后，由于出现格式问题，无法再次导入生成的文件 **[!UICONTROL configurable_variations]** 属性。 当属性选项中包含逗号时，会发生这种情况。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** 并创建新属性 _大小_：
1. 商店所有者的目录输入类型： **[!UICONTROL Dropdown]**.
1. 创建包含逗号的选项，例如：
   * 10,2厘米
   * 15,5厘米
1. **[!UICONTROL Advanced Attribute Properties]**  — 范围： _全局_.
1. 使用创建配置功能创建新的可配置产品。
1. 选择上述属性 _大小_ 以及包含逗号的两个选项。
1. 转到 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** 并创建一个新的“产品”导出（执行cron以触发CSV文件的生成）。
1. 转到 **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** 并尝试重新导入上面创建的相同CSV文件。

<u>预期结果</u>：

用户应该能够导入文件。

<u>实际结果</u>：

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。


## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
