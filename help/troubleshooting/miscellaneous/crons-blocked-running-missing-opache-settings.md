---
title: Cron由于配置错误或丢失而停止 [!DNL OpCache] 设置
description: 本文为配置错误或丢失导致cron停止工作提供了解决方案 [!DNL OpCache] 设置。
exl-id: 30643ea9-969f-41c8-8e62-b24e56d690cf
feature: Cache
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Cron因配置错误或丢失而停止 [!DNL OpCache] 设置

本文提供了一个解决方案，用于解决由于缺少或配置错误而导致cron停止工作的问题 [!DNL OpCache] 设置。

## 受影响的产品和版本

云基础架构上的Adobe Commerce， [所有受支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 问题

cron已停止工作。

## 原因

此 [!DNL OpCache] 模块已更新到较新版本，其中引入了 [!DNL GraphQL] 重写以下内容的插件 `env.php` 在运行时并且可能会覆盖cron设置，这可能导致问题。 此 [!DNL OpCache] 需要更新配置，以避免出现任何问题 `env.php file`这问题解决了 [版本2002.1.13](/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package.html?lang=en#v2002.1.13) 的 [!DNL ECE Tools] 包。

## 解决方案

选项1：在命令行工具中运行以下命令：

```bash
bin/magento cron:run
```

可能会显示一条消息，显示cron已禁用。

选项2：打开 `app/etc/env.php` 文件 — 如果您看到以下内容，则表示已手动禁用cron，由于部署失败未重新启用，或者此问题与 [!DNL OpCache] 设置。

```php
  'cron' =>
  array (
    'enabled' => 0,
  ),
```

1. 如果cron已禁用，请运行此命令以重新启用cron： `vendor/bin/ece-tools cron:enable`
1. 确保您使用的是最新版本的 [!DNL ECE Tools]. 如果不是，请升级（或跳至项目3）。 要检查现有版本，请运行此命令：
   `composer show magento/ece-tools`
1. 如果您已在最新版本的 [!DNL ECE Tools]，检查是否存在 `op-exclude.txt` 文件。 为此，请运行此命令：
   `ls op-exclude.txt`.
如果此文件不存在，请将https://github.com/magento/magento-cloud/blob/master/op-exclude.txt添加到存储库，然后提交更改并重新部署。
1. 无需升级 [!DNL ECE Tools]，则您只需在存储库中添加/修改https://github.com/magento/magento-cloud/blob/master/op-exclude.txt ，然后提交更改并重新部署。

## 相关阅读

* [Cron就绪检查问题](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues.html)
* [Crons属性](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)
* [Cron作业卡在“正在运行”状态](/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
