---
title: ’[!UICONTROL Recommendations] [!DNL JS] 升级到Adobe Commerce版本2.4.5时出错
description: 本文修复了在升级到Adobe Commerce后（所有部署方法）， [!DNL JS] 控制台中与产品相关的错误 [!UICONTROL Recommendations] 模块。
feature: Install, Upgrade
role: Developer
exl-id: 51d899eb-48f7-48c5-8bda-bd72a4d28945
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# [!UICONTROL Recommendations] [!DNL JS] 升级到Adobe Commerce版本2.4.5时出错

本文修复了在升级到Adobe Commerce后（所有部署方法）， [!DNL JS] 控制台中与产品相关的错误 [!UICONTROL Recommendations] 模块/设备。

目前暂无计划在未来的版本中解决此问题。

## 受影响的版本和产品

* 升级到版本2.4.5时的Adobe Commerce（所有部署方法）

## 问题

问题是由店面网页仍引用某些已删除产品引起的 [!UICONTROL Recommendations] 模块/单元（块和/或小组件） [!DNL CMS].

<u>重现问题的步骤</u>：

1. 升级到Adobe Commerce 2.4.5。
1. 访问店面网页。
1. 右键单击鼠标，然后选择 **Inspect** 以在Web浏览器中打开Web检查器。
1. 单击 **[!UICONTROL Console]** 选项卡。
1. 查看 [!DNL JS] 错误。

<u>预期结果</u>：

升级成功，但无 [!DNL JS] 错误。

<u>实际结果</u>：

几种不同类型的 [!DNL JS] Web浏览器控制台中显示错误。

## 解决方法

作为解决方法，您可以查看所有 [!UICONTROL Recommendations] 在页面上使用的设备，并删除所有已删除的设备。
