---
title: Adobe Commerce站点故障排查器
description: 单击每个问题以显示故障诊断程序每个步骤中的答案详细信息。
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Adobe Commerce站点故障排查器

单击每个问题以显示故障诊断程序每个步骤中的答案详细信息。

## 步骤1 {#step-1}

+++**是 <https://status.adobe.com> 是否显示任何问题？**

a.是 — 如果选中 [AdobeMagento状态](https://status.adobe.com/products/3350) 它显示出了一个问题，打开 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以便进一步调查。\
b.否 — 如果选中 [AdobeMagento状态](https://status.adobe.com/products/3350) 并且它没有显示问题，请继续 [步骤2](#step-2).

+++

## 步骤2 {#step-2}

+++**http://status.fastly.com是否显示任何问题？**

a.是 — 如果选中 [Fastly状态](https://status.fastly.com/) 它显示出了一个问题，打开 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以便进一步调查。\
b.否 — 如果选中 [Fastly状态](https://status.fastly.com/) 并且它没有显示问题，请继续 [步骤3](#step-3).

+++

## 步骤3 {#step-3}

+++**在Web浏览器中查看您的网站。 你有200（好的）代码吗？**

在中检查错误代码 **Firefox**：单击 **打开菜单** 图标> **Web开发人员** > **切换工具** > **网络** 选项卡> **全部** 过滤器> **状态** 列。 在中检查错误代码 **铬黄**：单击 **打开菜单** 图标> **更多工具** > **开发人员工具** > **网络** 选项卡> **全部** 过滤器> **状态** 列。

a.是 — 打开 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以便进一步调查。\
b.否 — 继续访问 [步骤4](#step-4).

+++

## 步骤4 {#step-4}

+++**您收到了哪个网站错误代码？**

a.错误代码500 — 检查日志 `/var/log/platform/`. 如果此数据不会向您显示问题，您可以打开 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 并包含您目前掌握的故障排除信息，以便进一步调查。

b.错误代码503 — 检查日志 `var/reports`. 如果此数据不会向您显示问题，您可以打开 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 并包含您目前掌握的故障排除信息，以便进一步调查。

c.错误代码404 — 运行以下查询： `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';` 如果查询返回表，其中 `update_exists` 值为“0”，请参阅 [由于内容暂存问题，所有页面（店面和管理员）上出现错误404](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md) 文章。 在所有其他情况下，请转至 [步骤5](#step-5).

d.其他错误代码 — 继续执行 [步骤5](#step-5).

+++

## 步骤5 {#step-5}

+++**您的网站运行是否缓慢，或者是MySQL或Redis中的服务器负载高、CPU负载高、请求处理速度慢还是发生中断？**

a.是 — 继续执行以下步骤 [检查来自CLI的DDOS攻击](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md).\
b.否 — 检查日志 `/var/log/exception.log` 和 `/var/log/deploy.log`，如果此数据不会向您显示问题，请转到 [步骤6](#step-6).

+++

## 步骤6 {#step-6}

+++**您是否有部署错误或部署失败？**

a.是 — 转到 [步骤13](#step-13).\
b.否 — 继续访问 [步骤7](#step-7).

+++

## 步骤7 {#step-7}

+++**是否存在Elasticsearch错误？**

a.是 — 继续执行以下步骤 [检查Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html).\
b.否 — 继续访问 [步骤8](#step-8).

+++

## 步骤8 {#step-8}

+++**您的MySQL数据库是否有较慢的查询或错误的查询？**

a.是 — 继续 [在MySQL中检查缓慢的查询和进程花费太长时间](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md) 并在中检查您的查询结构 [MySQL查询教程](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html).\
b.否 — 继续访问 [步骤9](#step-9).

+++

## 步骤9 {#step-9}

+++**您的静态内容是否不可用？**

a.是 — 继续查阅 [检查静态内容](https://support.magento.com/hc/en-us/articles/360031624091) 文章。\
b.否 — 继续访问 [步骤10](#step-10).

+++

## 步骤10 {#step-10}

+++**是否在日志中看到PHP致命错误？**

a.是 — 继续咨询 [常见PHP致命错误和解决方案](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md).\
b.否 — 继续访问 [步骤11](#step-11).

+++

## 步骤11 {#step-11}

+++**你看到Redis错误了吗？**

a.是 — 继续执行以下步骤 [验证Redis是否正在运行](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify) 和 [Redis疑难解答](https://redis.io/topics/problems).\
b.否 — 继续访问 [步骤12](#step-12).

+++

## 步骤12 {#step-12}

+++**是否看到索引器错误？**

a.是 — 如果索引被其他进程锁定，请查阅 [索引被另一个进程锁定](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md). 如果您有其他索引器错误，请打开 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以便进一步调查。\
b.否 — 打开 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以便进一步调查。

+++

## 步骤13 {#step-13}

+++**您的自定义模块是否有问题？**

a.是 — 继续查阅 [常规自定义模块故障诊断帮助](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md).\
b.否 — 继续访问 [步骤14](#step-14).

+++

## 步骤14 {#step-14}

+++**您是否遇到挂接后故障？**

a.是 — 继续在此检查您的MySQL错误 [MySQL服务器错误消息引用](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b.否 — 继续访问 [步骤15](#step-15).

+++

## 步骤15 {#step-15}

+++**您是否遇到编辑器修补程序问题？**

a.是 — 继续咨询 [应用修补程序将导致您的网站停机](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md).\
b.否 — 继续访问 [步骤16](#step-16).

+++

## 步骤16 {#step-16}

+++**是否存在SQL数据库错误？**

a.是 — 继续在此检查您的MySQL错误 [MySQL服务器错误消息引用](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html).\
b.否 — 继续访问 [步骤17](#step-17).

+++

## 步骤17 {#step-17}

+++**您是否有MySQL数据库死锁或无响应的MySQL数据库？**

a.是 — 继续检查此处的MySQL死锁 [MySQL中的死锁](/help/troubleshooting/database/deadlocks-in-mysql.md) 文章。\
b.否 — 打开 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以便进一步调查。

+++

[返回步骤1](#step-1)

单击 [此处](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md) 查看站点关闭疑难解答流程图。
