---
title: 'MDVA-30945：添加和更新购物车操作期间发生致命错误'
description: MDVA-30945修补程序修复了在更新购物车时，在module-configurable-product CartItemProcessor.php*中的null上收到致命错误*调用成员函数getValue()的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 已在Adobe Commerce 2.4.2中修复此问题。
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945：添加和更新购物车操作期间发生严重错误

MDVA-30945修补程序修复了您收到致命错误的问题 *在模块可配置的产品CartItemProcessor.php中调用null上的成员函数getValue()* 更新购物车时。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.7。 已在Adobe Commerce 2.4.2中修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在管理员中更新购物车中的产品后出现致命的PHP错误。

<u>重现问题的步骤</u>：

1. 在Commerce管理员中，创建不带选项的可配置产品。
1. 将其添加到店面的购物车中。
1. 返回到管理员，向产品添加可配置选项并保存更改。
1. 刷新店面上的购物车页面。

<u>预期结果</u>：

在购物车页面上，会显示以下验证消息： *下面的某些产品没有所有必需的选项*.

<u>实际结果</u>：

购物车页面为空白。 在PHP中 `error.log`，将记录以下错误： *vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php：76中的消息“Call to a member function getValue() on null”未捕获到“Error”异常*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
