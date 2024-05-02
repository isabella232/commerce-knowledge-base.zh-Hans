---
title: 'MDVA-36424：附加到页面生成器的图像在保存时消失'
description: MDVA-36424修补程序解决了在多个网站第二次保存类别时，附加到页面生成器元素的图像消失的问题，默认网站的基本URL与管理员URL不同。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21后，即可使用此修补程序。 修补程序ID为MDVA-36424。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424：附加到页面生成器的图像在保存时消失

MDVA-36424修补程序解决了在多个网站第二次保存类别时，附加到页面生成器元素的图像消失的问题，默认网站的基本URL与管理员URL不同。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.21。 修补程序ID为MDVA-36424。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.6

**与Magento版本兼容：**

Adobe Commerce（所有部署方法） 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果后端基本URL与店面基本URL不同，则不会保存附加到页面生成器元素的媒体图像。

<u>重现问题的步骤</u>：

1. 创建第二个网站 — website2。
1. 为website2设置不同的基本URL（admin中使用的基本URL应不同于第二个网站）。
1. 将第二个网站设置为默认网站(**商店** > *设置* > **所有商店** >选择第二个网站>设置为 *默认*)。
1. 导航到后端中的类别页面，然后转到类别编辑视图。
1. 导航到 **内容** > *描述*.
1. 向内容添加列，并使用媒体集设置背景图像。
1. 保存类别。
1. 转到 **内容** > *描述* 再次重申；您将正确看到保存的图像。
1. 再次保存类别。
1. 转到 **内容** > *描述*.

<u>预期结果</u>：

保存类别时未删除图像。

<u>实际结果</u>：

再次保存类别后，将删除该图像。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
