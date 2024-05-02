---
title: 与Adobe Commerce上max_allowed_packet相关的数据库错误
description: 本文针对“var/log/exception.log”中的数据库连接错误，提供了一种解决方案，在导入大量产品或执行其他任务以强制服务器处理大于“max_allowed_packet”中设置的大于默认值16MB的数据包时，可能会发生这种错误。
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# 与Adobe Commerce上max_allowed_packet相关的数据库错误

本文为中的数据库连接错误提供了解决方案。 `var/log/exception.log` 在导入大量产品或执行其他任务强制服务器处理比中设置的更大的数据包时，可能会发生这种情况 `max_allowed_packet` 大于默认值16MB。

## 受影响的产品和版本

* Adobe Commerce内部部署，所有 [支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

当MySQL客户端或 [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html) 服务器接收的数据包大于 [max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet) 字节，它会发出 [ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large) 错误(可在 `exception.log`)并关闭连接。 对于某些客户，您还可以获得 *查询期间与MySQL服务器的连接丢失* 如果通信数据包太大，则出现错误。

<u>重现问题的步骤</u>

各种任务都可能导致此问题。 这可能包括尝试将大量产品导入Adobe Commerce或发送过多数据的事务性查询。 结果是，中出现数据库连接错误 `var/log/exception.log` 以及其他问题，例如产品未成功导入。

## 原因

MySQL的默认值为16MB `max_allowed_packets` 设置不够大，无法满足您的需求。

## 解决方案

1. 标识单个行超过当前值的查询 `max_allowed_packet` 限制。 需要重写此类查询以减少返回的数据量。 这可以通过以下方法实现：在 `SELECT` 语句或为各种列选择较小的数据类型作为表设计的一部分。 如果您拥有New Relic帐户，请使用 [New Relic APM错误页面](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors) 和 [“New Relic APM数据库”页](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)、和 [New Relic日志](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management) 以搜索相关查询。
1. 为了快速修正，您可以临时请求 `max_allowed_packet` 大小将在以下情况下增加： [提交票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，但这由客户工程团队自行决定，因为值过大可能会导致网络拥塞，进而导致复制失败。
1. 作为最佳实践，您应在CLI中针对某些大型数据库表运行以下命令：

   ```
   show table status like [table name to match]
   ```

   评估在这些表上运行的查询，以确定是否超过推荐值 `max_allowed_packet` 大小为16MB。 执行步骤一中的相同过程，减少此类查询返回的数据。

## 相关阅读

* [安装指南> MySQL](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=max%20allowed%2016%20MB) 在我们的开发人员文档中。
* [数据库上载断开与MySQL的连接](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md) 在我们的支持知识库中。
* [云基础架构上Adobe Commerce的数据库最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) 在我们的支持知识库中。
* [解决数据库性能问题的最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) 在我们的支持知识库中。
