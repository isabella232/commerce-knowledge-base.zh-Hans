---
title: 适用于Adobe Commerce的高级报表疑难解答程序
description: 使用此故障诊断程序工具可解决Adobe Commerce上的高级报表问题。 这包括高级报告未显示任何数据和404错误。 单击每个问题以显示故障诊断程序每个步骤的答案。
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 84b4ca4c4144381f0b404d2eae6684e7b21755df
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# 适用于Adobe Commerce的高级报表疑难解答程序

使用此故障诊断程序工具可解决Adobe Commerce上的高级报表问题。 这包括高级报告未显示任何数据和404错误。 单击每个问题以显示故障诊断程序每个步骤的答案。

## 第1步 — 确认站点符合高级报告要求 {#step-1}

+++**您的网站是否满足高级报告要求？**

使用高级报告时，出现“404错误”页面。 您的网站是否符合 [高级报告要求](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements)？

a.是 — 转到 [步骤2](#step-2).\
b.否 — 按照中的步骤完成站点的高级报告要求 [高级报告要求](https://docs.magento.com/user-guide/reports/advanced-reporting.html#requirements). 然后，转到 [步骤2](#step-2).

+++

## 第2步 — 是否存在使用多种基础货币的订单？ {#step-2}

+++**是否使用了多个基础货币？**

是否使用了多个基本货币（在订单和配置中）？ 运行此SQL命令以获取当前配置： `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` .

a.是 — 如果查询返回了多行，则不能使用“高级报告”，因为我们仅支持一种货币。\
b.否 — 输出仅显示一种货币。 示例： `USD`. 是否曾经使用过多个基础货币（按订单）？ 运行此SQL命令以获取历史订单数据：\
`SELECT DISTINCT base_currency_code FROM sales_order;`.
**注：此命令要求进行完整的表扫描，因此对于记录数量多的表，这可能会在执行查询时对性能产生影响** 以获取历史订单数据。
如果曾经使用过多种基础货币，则不能使用高级报告，因为我们只支持一种货币。 如果输出仅显示一种货币，请转到 [步骤3](#step-3).

+++

## 步骤3 — 检查是否正在使用拆分数据库 {#step-3}

+++**您是否使用拆分数据库解决方案？**

您是否使用 [拆分数据库解决方案](https://devdocs.magento.com/guides/v2.3/config-guide/multi-master/multi-master.html)？

a.是 — 使用修补程序 **MDVA-26831** 在 [拆分数据库解决方案的高级报告404错误](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-404-error-on-split-database-solution.md) 并清除缓存。 请等待24小时以使作业再次运行，然后重试。\
b.否 — 继续访问 [步骤4](#step-4).

+++

## 步骤4 — 确认启用高级报告 {#step-4}

+++**是否启用了高级报告？**

Check **管理员** > **商店** > **设置** > **配置** > **常规** > **高级**. 有关详细步骤，请查看 [高级报告：启用高级报告](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting).

a.是 — 转到 [步骤5](#step-5).\
b.否 —  [启用高级报告](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 并保存，等待24小时让Adobe Commerce和高级报表同步。 检查您的数据现在是否加载。 如果它确实解决了这个问题。 如果未继续 [步骤5](#step-5).

+++

## 步骤5 — 检查令牌 {#step-5}

+++**有没有令牌？**

通过运行以下查询检查是否存在令牌： `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G` 有没有令牌？

a.是 — 转到 [步骤7](#step-7).\
b. NO — 如果令牌值为NULL或数据库中没有记录，请继续 [步骤6](#step-6).

+++

## 步骤6 — 使用行 {#step-6}

+++**查询是否返回行？**

通过运行此查询检查标志表中的计数器值： ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G`` 查询是否返回行？

a.是 — 执行以下步骤：1. 运行以下查询：\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\。 [禁用和启用高级报告模块](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 在设置和 [重新授权令牌](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
3\。 等待24小时，以便Adobe Commerce和高级报表进行同步。 如果您仍然无法在高级报表中查看数据， [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b.否 — 如果查询未返回任何内容，请执行以下步骤：1. [禁用和启用高级报告模块](https://docs.magento.com/user-guide/reports/advanced-reporting.html#step-1-enable-advanced-reporting) 在设置和 [重新授权令牌](https://docs.magento.com/user-guide/reports/advanced-reporting.html#verify-that-the-integration-is-active).\
2\。 等待24小时，以便Adobe Commerce和高级报表进行同步。 如果您仍然无法在高级报表中查看数据， [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## 步骤7 — 检查中的记录 `cron_schedule` 表 {#step-7}

+++**以下位置是否有记录： `cron_schedule` 桌子？**

检查该作业 `analytics_collect_data` 通过运行此查询来执行： `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a.是 — 如果有记录和 **状态** 列显示 _已错过_，使用本知识库文章中的修补程序 [更新高级报告以在其自己的cron组上运行](/help/troubleshooting/known-issues-patches-attached/update-advanced-reporting-to-run-on-its-own-cron-group.md).\
b.是 — 如果有记录和 **状态** 列显示 _success_，继续执行 [步骤9](#step-9).\
c.是 — 如果有记录和 **状态** 列显示 _错误_，继续执行 [步骤8.](#step-8)\
d.否 — 如果没有记录，请转到 [步骤8](#step-8).

+++

## 步骤8 — 在中检查作业 `support_report.log` {#step-8}

+++**作业是否已登录 `support_report.log`？**

运行以下命令： `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a.是 — 如果查询的输出指示成功的任务，例如 `Cron Job analytics_collect_data is successfully finished` 继续到 [步骤9](#step-9).\
b.否 — 如果日志中没有记录， [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
c.是 — 如果有记录但存在错误，请转至 [步骤10](#step-10).

+++

## 步骤9 — 检查 `data.tgz` 文件 {#step-9}

+++**文件是 `data.tgz` 系统中存在，并且访问日志中是否有记录？**

检查文件 `data.tgz` 存在，运行命令：

```
ls -ltr pub/media/analytics/<there should be a directory with hash name>/
```

要检查access.logs中是否存在记录，请运行命令：

```
zgrep -i analytics /var/log/platform/[cluster_id|cluster_id_stg]/access.log* | grep MagentoBI
```

a.是 — 如果文件 `data.tgz` 存在并且访问日志中有记录，但您仍然存在404错误，您需要 [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b.否 — 继续访问 [步骤10](#step-10).

+++

## 步骤10 — 检查错误消息 {#step-10}

+++**cron作业是否引发错误消息？**

示例：在 `core_config_data` 表 — 您看到该错误 *无法删除“/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0”文件*. 警告！unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0？lang=en)：没有此类文件或目录*

a.是 — 使用ACSD-50165修补程序 [无法删除该文件。 警告！unlink：管理员没有此类文件或目录错误](/help/troubleshooting/miscellaneous/file-cannot-be-deleated-no-file-or-directory.md)，请等待24小时以使作业再次运行，然后重试。\
b.否 — 继续访问 [步骤11](#step-11).

+++

## 步骤11 — 验证是否存在页面生成器错误 {#step-11}

+++**是否因页面生成器而出错？**

示例： `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a.是 — 使用MDVA-19391修补程序 [Adobe Commerce上的常见高级报告cron作业错误](/help/troubleshooting/known-issues-patches-attached/advanced-reporting-cron-job-errors-magento-commerce.md)，请等待24小时以使作业再次运行，然后重试。\
b.否 —  [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

[返回步骤1](#step-1)
