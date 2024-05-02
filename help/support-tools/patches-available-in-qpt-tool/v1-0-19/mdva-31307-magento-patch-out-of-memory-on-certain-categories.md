---
title: 'MDVA-31307：某些类别的内存不足'
description: MDVA-31307修补程序修复了“Magento\_Csp/模型/块缓存”占用大量内存并生成大量缓存字符串的问题，如果某些页面具有大量动态列入白名单的脚本和样式，则会导致出现问题。 提供的修补程序将优化此过程。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-31307。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307：某些类别的内存不足

MDVA-31307修补程序修复了以下问题 `Magento\_Csp/Model/BlockCache` 占用大量内存并生成大量缓存字符串，这会导致存在大量动态列入白名单脚本和样式的特定页面出现问题。 提供的修补程序将优化此过程。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.19。 修补程序ID为MDVA-31307。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了存在以下问题的情况 *内存不足* 由于缓存块的动态CSP白名单出现问题，导致某些类别上出现错误。

<u>重现问题的步骤：</u>

1. 生成小型配置文件夹具(`bin/magento setup:performance:generate-fixtures`)。
1. 在不同选项卡中打开所有类别页面。

<u>实际结果：</u>

*[日期和时间] PHP致命错误：未知行0中允许的内存大小已用尽1073741824字节(尝试分配90112字节)
[日期和时间] PHP致命错误： /app/中允许的内存大小已用尽1073741824字节(尝试分配33554440字节)`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php第31行*

<u>预期结果：</u>

所有页面均已正确打开。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
