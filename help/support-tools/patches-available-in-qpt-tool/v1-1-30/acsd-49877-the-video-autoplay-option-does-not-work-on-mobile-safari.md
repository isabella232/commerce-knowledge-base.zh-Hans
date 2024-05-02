---
title: '''ACSD-49877：视频自动播放在移动设备中不起作用 [!DNL Safari]’'
description: 应用ACSD-49877补丁以修复视频自动播放选项在移动设备上不起作用的Adobe Commerce问题 [!DNL Safari] 当视频直接链接到远程视频文件时。
exl-id: 454f7cec-29b9-485b-93be-2a4f2eb77da7
feature: CMS
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877：视频自动播放在移动设备中不起作用 [!DNL Safari]

ACSD-49877修复了移动设备上的自动播放选项的问题 [!DNL Safari] 当视频直接链接到远程视频文件时，无法正常工作。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.30。 修补程序ID为ACSD-49877。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 [！magento/quality-patches] 包到最新版本，并检查[[!DNL Quality Patches Tool]：搜索修补程序]。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

视频自动播放在移动设备上不起作用 [!DNL Safari] 当视频直接链接到远程视频文件而不是流服务时。

<u>先决条件</u>：
[!DNL Page Builder] 模块已安装。

<u>重现问题的步骤</u>：

1. 创建新的CMS页面，并编辑 **[!UICONTROL Content Value]** 替换为 [!DNL Page Builder].
1. 添加 *选项卡* 元素到内容中，并添加 *视频元素* 内部 *选项卡*.
1. 现在，单击齿轮按钮以编辑 *视频元素*.
1. 将指向mp4视频文件的链接添加到 [!UICONTROL Video URL] 字段。
1. 标记 **[!UICONTROL Autoplay]** 字段为 *是*.
1. 单击 **[!UICONTROL Save]**.
1. 打开最近创建的页面 [!DNL Safari] 使用iPhone。

<u>预期结果</u>

自动播放选项适用于 [!DNL Safari] 使用iPhone。

<u>实际结果</u>

自动播放选项不起作用 [!DNL Safari] 使用iPhone。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
