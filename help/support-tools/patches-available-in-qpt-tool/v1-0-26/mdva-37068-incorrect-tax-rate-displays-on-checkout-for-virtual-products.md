---
title: 'MDVA-37068：为虚拟产品签出时显示的税不正确'
description: MDVA-37068修补程序修复了签出页面显示虚拟产品税率不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26后，即可使用此修补程序。 修补程序ID为MDVA-37068。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: ef75b41e-e79d-4947-8b74-87966642f808
feature: Cache, Checkout, Orders, Products, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-37068：为虚拟产品签出时显示的税不正确

MDVA-37068修补程序修复了签出页面显示虚拟产品税率不正确的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.26。 修补程序ID为MDVA-37068。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**
Adobe Commerce（所有部署方法） 2.3.1-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当购物车只有虚拟产品时，“结帐”页面上显示的税率不正确。

<u>先决条件</u>：

1. 为两个不同的国家（例如，10%和1%）创建两个单独的税率和税则。
1. 创建虚拟产品。
1. 运行重新索引和清理缓存。

<u>重现问题的步骤</u>：

1. 创建客户。
1. 添加不同的帐单地址和送货地址。
1. 将虚拟产品添加到购物车。
1. 检查购物车和结帐页面。

<u>预期结果</u>：

“购物车”和“结账”页面上显示的税是相同的。

<u>实际结果</u>：

“购物车”和“结账”页面上显示的税种“不同”。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
