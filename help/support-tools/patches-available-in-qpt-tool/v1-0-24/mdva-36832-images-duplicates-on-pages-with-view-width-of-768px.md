---
title: 'MDVA-36832：具有768像素视图宽度的页面上复制的图像'
description: MDVA-36832修补程序修复了在视图宽度为768px的页面上复制图像的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24后，即可使用此修补程序。 修补程序ID为MDVA-36832。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 3eb0c11b-d93a-4676-afd1-8f6592c6cd6d
feature: Configuration, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-36832：在视图宽度为768像素的页面上复制的图像

MDVA-36832修补程序修复了在视图宽度为768px的页面上复制图像的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.24。 修补程序ID为MDVA-36832。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在视图宽度为768像素的页面上复制的图像。

<u>重现问题的步骤：</u>

1. 转到后端>内容>页面并编辑任何页面。
1. 将任意图像添加到页面。
1. 转到前端并打开已编辑的页面。
1. 在Chrome中打开开发人员工具。
1. 启用“设备视图”并选择“iPad视图”或将页面宽度设置为768像素。

<u>实际结果：</u>

图像重复。

<u>预期结果：</u>

页面上只应显示一个已添加图像。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
