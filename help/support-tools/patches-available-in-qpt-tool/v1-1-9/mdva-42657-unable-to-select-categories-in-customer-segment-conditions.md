---
title: 'MDVA-42657：无法在客户区段条件中选择类别'
description: MDVA-42657修补程序解决了管理员用户无法在客户区段条件中选择类别的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-42657。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 9c810dcd-b39b-4456-a362-5452ada4dc53
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-42657：无法在客户区段条件中选择类别

MDVA-42657修补程序解决了管理员用户无法在客户区段条件中选择类别的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.9。 修补程序ID为MDVA-42657。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员用户无法在客户区段条件中选择类别。

<u>重现问题的步骤</u>：

1. 转到 **客户** > **区段**.
1. 创建新区段。
1. 转到新创建的区段并单击 **条件** 左侧导航栏中。
1. 单击绿色加号。
1. 选择“产品”下的“产品历史记录”。
1. 将“已查看”更改为“已订购”。
1. 将“ALL”更改为“ANY”。
1. 单击嵌套的绿色加号，然后选择“类别”。
1. 单击 **...** 签名，然后单击选择器图标（复选标记的左侧）。
1. 打开浏览器开发控制台。
1. 选中任意/多个类别对应的复选框，并记下控制台中抛出的javascript错误。
1. 单击 **保存** 按钮。
1. 导航回条件，并检查是否保存了选定的类别。

<u>预期结果</u>：

在查看/编辑区段条件时，将保存和选择选定的类别。

<u>实际结果</u>：

缺少选定的类别，无法正确保存。 您在控制台中收到以下错误：

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
