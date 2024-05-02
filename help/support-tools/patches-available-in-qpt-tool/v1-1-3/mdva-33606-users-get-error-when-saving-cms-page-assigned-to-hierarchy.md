---
title: 'MDVA-33606：保存分配给层次结构的CMS页面时，用户收到错误'
description: MDVA-33606修补程序解决了用户在保存分配给层次结构树的CMS页面时收到*发现唯一约束冲突*错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3后，即可使用此修补程序。 修补程序ID为MDVA-33606。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606：用户在保存分配给层次结构的CMS页面时遇到错误

MDVA-33606修补程序解决了用户收到 *发现唯一约束冲突* 保存分配给层次结构树的CMS页面时出错。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.3。 修补程序ID为MDVA-33606。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1-2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在尝试保存分配给层次结构树的CMS页时，用户会收到以下错误消息： *发现唯一约束冲突*.

<u>重现问题的步骤</u>：

1. 创建新的CMS页面。 将范围设置为“所有存储视图”。 这是您的CMS第1页。
1. 创建新的商店视图。 这是您的商店视图2。
1. 转到 **内容** > **层级** >将CMS第1页添加到层次结构树。
1. 将范围更改为“存储视图2”。
   * 取消选中“使用父节点层次结构”。
   * 将CMS第1页添加到此范围并保存。
1. 现在将范围更改为默认存储视图。
   * 取消选中“使用父节点层次结构”。
   * 将CMS第1页添加到此范围并保存。
1. 转到 **内容** > **页面** > **添加新页面**.
   * 将页面标题命名为“Page 2”。
   * 在网站中的页面部分中，分配给“所有商店视图”和两个商店视图（“默认商店视图”和“商店视图2”），然后单击 **保存页面**.
1. 在CMS编辑页中，打开层次结构选项卡。
   * 将页面2分配给“存储视图2”节点、“默认”节点和“所有网站”节点。

<u>预期结果</u>：

您可以将CMS页面分配到所有三个节点，而不会出现任何错误。

<u>实际结果</u>：

您会收到以下错误： *发现唯一约束冲突*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
