---
title: 'ACSD-51528：不同行为对snake_case格式的影响'
description: 应用ACSD-51528修补程序以修复Adobe Commerce问题，该问题导致在snake_case格式方面有不同的行为。
exl-id: dd878321-8032-41f3-8dcd-acb0cc023b44
feature: Variables
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-51528：关于snake_case格式的不同行为

ACSD-51528修补程序修复了snake_case格式的不同行为。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.32。 修补程序ID为ACSD-51528。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对snake_case格式的不同行为。

<u>重现问题的步骤</u>：

1. 测试 `\Magento\Framework\Api\DataObjectHelper::populateWithArray` 函数中，函数包含各种不同的属性名称。
1. 名称如下所示的属性 *新名称* 应该转换为 *new_p_name*&#x200B;相反，它们将转换为 *new_name*.
1. 此外，在使用 *getNewPName* 函数中， *null* 将返回，因为 *抽象模型* 将正确地将调用转换为 *new_p_name* 使这两个功能相互不兼容。

<u>预期结果</u>

此 **[!UICONTROL populateWithArray]** 函数应正确地将对象属性转换为snake_case，使其与 **[!DNL AbstractModel's]** `Getters` 和 `Setters`.

<u>实际结果</u>

使用时 **[!UICONTROL populateWithArray]** 函数中，任何对象属性的名称中一行包含两个或多个大写字母，都将导致最终数据数组中的snake_case转换不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
