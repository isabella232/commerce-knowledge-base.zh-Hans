---
title: ’[!DNL Admin] 登录不起作用 — 超出允许的会话最大大小'
description: 解决您尝试登录 [!DNL Admin] 面板和表单会刷新并且您无法登录。
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# [!DNL Admin] 登录不起作用 — 超出了允许的会话最大大小

本文修复了您尝试登录 [!DNL Admin] 面板，但表单刚刚刷新，您无法登录。 这是因为 [!DNL Admin] 已超过会话大小。

## 受影响的版本

* Adobe Commerce内部部署， [所有受支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 云基础架构上的Adobe Commerce， [所有受支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

无法登录到 [!DNL Admin]，因为表单会不断重新加载。

## 原因

超出了允许的会话最大大小。

## 解决方案

查看 `var/log/support_report.log` 文件查找错误，例如：

*[2023-07-13T04:26:09.792060+00:00] report.WARNING：260572的会话大小超过了允许的会话最大大小256000。 [] []
[2023-07-13T04:26:17.056714+00:00] report.WARNING：260570的会话大小超过了允许的会话最大大小256000。 [][]*

如果您看到这些错误，解决办法将是：

<u>Adobe Commerce内部部署</u>：
1. 增加 **[!UICONTROL Max Session Size in Admin]** 值。 为此，请转到 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. 将值设置为 *500000* 或更高。 根据错误中报告的现有最大大小 — 您还可以将该值设置为 *0* 将取消会话大小限制。

<u>云基础架构上的Adobe Commerce</u>：

(此设置只能在 [!DNL Admin] 当部署/操作模式为默认或开发人员时。 但是，在云环境中只允许使用生产部署模式。)

要增加此值，请在终端(SSH)中运行此命令：

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

您可以设置为大于 *500000* 根据错误中报告的现有最大大小，您还可以将该值设置为 *0* 以移除会话大小限制。

## 相关阅读

* [会话大小](/docs/commerce-admin/systems/security/security-session-management.html?lang=en#admin-sessions) 在“Admin Systems Guide（管理系统指南）”中。
* [操作模式](/docs/commerce-operations/configuration-guide/cli/set-mode.html) ，位于配置指南中。
* [安全连接](/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) 《Commerce on Cloud Infrastructure指南》中的。
