---
title: 修订的Google修补程序所有Adobe Commerce版本上的访问丢失
description: “本文为最近不兼容的Adobe Commerce商家提供了修补程序 [!DNL Google Maps] 版本3.54+.'
feature: Install, Upgrade
role: Developer
source-git-commit: 49bc0b643c10c6597d6a905935c36251e92b18f9
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# 修订的修补程序 [!DNL Google Maps] 所有Adobe Commerce版本上的访问丢失

本文为最近不兼容的Adobe Commerce商家提供了修补程序 [!DNL Google Maps] 版本3.54+。 此修复程序旨在解决Adobe Commerce商家无权访问的问题。 [!DNL Google Maps] (在任何Adobe Commerce版本中)。

## 受影响的版本和产品

* Adobe Commerce和/或其他所用技术的版本。
* Adobe Commerce *2.4.4* - *2.4.7* 在云和内部部署版本上。

## 问题

开启 *2024年6月14日* [!DNL Google Maps] 版本 *3.53* 到了生命尽头，却被关闭了 [!DNL Google].

有关详细信息，请参见[[!DNL Google Maps] 平台：映射JavaScript API] (https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions)。

Adobe Commerce与任何最近使用的 [!DNL  Google Maps] 版本3.54+。

不兼容是由旧版导致的 `prototype.js script`，通过加载 `lib/web/legacy-build.min.js` 覆盖本机Array.from函数，这会导致与 [!DNL  Google Maps] API。

请参阅[[!DNL Google Maps: JS Best Practices]] (https://developers.google.com/maps/documentation/javascript/best-practices)。

<u>重现问题的步骤</u> ：

1. 转到 **[!UICONTROL Content]** > **[!UICONTROL Pages]** >并单击 **[!UICONTROL New Page]**.
1. 展开内容块并单击编辑 **[!DNL PageBuilder]** 按钮。
1. 将地图内容块从 **[!DNL PageBuilder]** 菜单切换为页面。

<u>预期结果：</u>

[!DNL Google Maps] 应该按预期工作。

<u> 实际结果：</u>

从删除映射内容块时 **[!DNL PageBuilder]** 菜单转到页面，出现错误消息，例如 *“对不起！ 出现错误”* 将显示。

## 解决方案

* 任何2.4.4、2.4.5、2.4.6或2.2.7修补程序版本上的所有商户都应将这些相应的修补程序应用于其版本。

## Patch

根据Adobe Commerce版本，使用以下附加的修补程序：

**对于版本2.4.4：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**对于版本2.4.5：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**对于版本2.4.6：**
[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)

**对于版本2.4.7：**
[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)

**请注意**

此问题将在8月版仅限安全的修补程序版本中永久修复： 2.4.7-p2、2.4.6-p7、2.4.5-p9、2.4.4-p10

## 相关阅读

[如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)