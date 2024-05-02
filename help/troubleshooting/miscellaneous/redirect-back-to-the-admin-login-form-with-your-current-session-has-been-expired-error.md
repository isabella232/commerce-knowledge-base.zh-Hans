---
title: 重定向回Commerce管理员登录表单，其中显示“您的当前会话已过期”错误
description: '''本文提供了Commerce管理员登录问题的可能解决方案，您会在该问题中被重定向回登录表单，并出现以下错误消息：*“您的当前会话已过期”*。 解决方案包括检查服务器时间设置问题和更改会话存储设置。'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# 重定向回Commerce管理员登录表单，其中显示“您的当前会话已过期”错误

本文针对Commerce管理员登录问题提供了可能的解决方案，您会在该问题中被重定向回登录表单，并显示以下错误消息： *“您当前的会话已过期”*. 解决方案包括检查服务器时间设置问题和更改会话存储设置。

## 受影响的版本和版本：

所有Adobe Commerce版本和版本

## 问题

<u>重现问题的步骤</u>：

1. 转到Commerce管理页面。
1. 输入您的凭据，然后单击“登录”。

<u>预期结果</u>：

您将登录到Commerce管理员。

<u>实际结果</u>：

系统会将您重定向回登录表单，并显示以下错误消息： *“您当前的会话已过期”*.

## 原因

这个问题可能有两个原因：

* 服务器时间设置问题
* 会话存储问题

请查看以下部分以了解解决方案。

## 解决方案

### 检查服务器时间设置问题

检查在中创建的会话记录 `admin_user_session` 表格。 如果 `created_at` 和/或 `updated_at` 不正确，这可能是由于服务器时间设置问题导致的。 请要求您的服务器系统管理员检查这一点。 请注意，默认情况下，DB中的时间设置为UTC。

### 更改会话存储

尝试更改会话存储。 使用来自以下位置的信息 [如何查找会话文件](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html) 文章，以了解会话的存储位置，然后通过编辑 `app/etc/env.php` 文件。

例如，要在文件系统中开始存储会话，请更改 `'session'` 部分如下所示：

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

运行 `bin/magento app:config:import` 命令导入配置数据。


## 相关阅读

* [从配置文件导入数据](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html) 在我们的开发人员文档中
* [配置Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html) 在我们的开发人员文档中
* [重定向回Commerce管理员登录表单，其中显示“您的帐户暂时被禁用”错误](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md) 在我们的支持知识库中
* [尝试登录Commerce管理员时，重定向回登录表单，并且未出现错误](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md) 在我们的支持知识库中
