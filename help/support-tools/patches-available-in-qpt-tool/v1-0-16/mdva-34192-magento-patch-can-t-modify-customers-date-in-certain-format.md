---
title: “MDVA-34192修补程序：无法以特定格式修改客户日期”
description: MDVA-34192修补程序修复了无法使用dd/mm/yyyy格式修改/指定客户出生日期的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-34192修补程序：无法以特定格式修改客户日期

MDVA-34192修补程序修复了无法使用dd/mm/yyyy格式修改/指定客户出生日期的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.16。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.5-p1

**与Adobe Commerce版本兼容：** 2.3.4 - 2.3.6

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

该补丁解决了若干问题。 以下是其中一个的描述和重现步骤。

当我们使用自定义日期属性进行筛选并且管理员用户区域设置为en\_GB时，产品网格筛选器无法正常工作。

<u>重现问题的步骤：</u>：

1. 创建管理员用户，其 **界面区域设置** 设置为 *英语（英国）*.
1. 使用以下配置创建日期属性：
   * **商店所有者的目录输入类型**： *日期*
   * **在筛选器选项中使用**： *是*
   * **添加到列选项**： *是*
1. 将属性分配给属性集。
1. 转到产品编辑页面，使用日期选取器为新属性选择日期并保存。
1. 尝试使用新的日期属性筛选产品网格。

<u>预期结果：</u>：

当管理员用户区域设置为en\_GB时，产品过滤器可正确用于自定义日期属性。

<u>实际结果：</u>：

当管理员用户区域设置为en\_GB时，产品过滤器无法正确用于自定义日期属性。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
