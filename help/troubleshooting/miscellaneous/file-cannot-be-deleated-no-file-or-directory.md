---
title: “无法删除文件。 警告！ unlink：没有此类文件或目录错误 [!DNL Admin]"
description: 本文提供了解决出现错误*无法删除文件问题的方案。 警告！取消链接没有此类文件或目录错误* [!DNL Admin] 当您执行 [!DNL Javascript/CSS] 刷新。
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *无法删除该文件。 警告！unlink：没有此类文件或目录错误* 从 [!DNL Admin]

本文提供了解决出现错误问题的方案 *无法删除该文件。 警告！unlink：没有此类文件或目录错误* 从 [!DNL Commerce Admin] 当您执行 [!DNL JavaScript/CSS] 刷新。

## 受影响的产品和版本

* Adobe Commerce 2.4.0 - 2.4.6，所有部署方法

## 问题

当您执行 [!DNL JS/CSS] 刷新：

*无法删除“/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b”文件。 警告！unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b)：没有这样的文件或目录*

或：您会在以下位置看到上述错误： [!DNL Admin]中的和/或类似错误 [!DNL New Relic] 或在部署日志中。

或者：您无法访问高级报告，并且analytics_collect_data cron作业失败，出现以下错误：

*无法删除“/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0”文件。 警告！unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0)：没有此类文件或目录*

<u>重现问题的步骤：</u>

方法1：

1. 登录到 [!DNL Admin].
1. 转到 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 单击 **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

方法2：

1. 登录到 [!DNL Admin].
1. 转到 **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. 更改 [!UICONTROL Base URL] 或 [!UICONTROL Base URL (Secure)].
1. 单击 **[!UICONTROL Save Config]**.

## 解决方案

如果您在使用Adobe Commerce on Cloud基础架构并且拥有 [!DNL magento/magento-cloud-patches] 已安装的1.0.22包括修补程序，您无需单独安装ACSD-50165。

云基础架构上的Adobe Commerce：将适用于Commerce的云修补程序升级到1.0.22 (**或更新**)，其中包含此修补程序： [Commerce云修补程序](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

50165 Adobe Commerce内部部署：使用 [Quality Patches Tools > Usage](/docs/commerce-operations/tools/quality-patches-tool/usage.html). ACSD-50165修补程序附带 [!DNL QPT] [v1.1.30。](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## 相关阅读

* [[!DNL Quality Patches Tool] >发行说明](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) Commerce Tools指南中的。
* [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) Commerce Tools指南中的。
