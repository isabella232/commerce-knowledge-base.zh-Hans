---
title: Adobe Commerce上的数据库存储疑难解答
description: 对于Adobe Commerce上遇到数据库问题的客户，本文是一个故障排除工具。 单击每个问题以显示故障诊断程序每个步骤的答案。 根据您的症状和配置，故障诊断程序将说明如何诊断数据库的空间和配置问题。
exl-id: f7b09023-7129-4fd0-9bb5-02a2228bc148
feature: Observability, Services, Storage, Support
role: Developer
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---

# Adobe Commerce上的数据库存储疑难解答

对于Adobe Commerce上遇到数据库问题的客户，本文是一个故障排除工具。 单击每个问题以显示故障诊断程序每个步骤的答案。 根据您的症状和配置，故障诊断程序将说明如何诊断数据库的空间和配置问题。

## 步骤1 — 标识存在空间问题的目录 {#step-1}

+++**您是否拥有 `/tmp` 空间不足导致的问题？**

这可以通过一系列症状来指示，包括 `/tmp` 装载为已满、站点已关闭或无法通过SSH连接到节点。 您可能还会遇到以下错误 _设备无剩余空间(28)_. 对于由生成的错误列表 `/tmp` 完整，复查 [/tmp装载已满](/help/troubleshooting/miscellaneous/tmp-mount-full.md).

还是说，你有 `/data/mysql` 空间不足导致的问题？ 这也可能由各种症状指示，包括站点中断、客户无法将产品添加到购物车、与数据库的连接失败以及galeria错误，例如 _SQLSTATE\[08S01\]：通信链接失败：1047 WSREP_. 有关MySQL磁盘空间不足导致的错误列表，请参阅 [云基础架构上的Adobe Commerce上的MySQL磁盘空间不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md).

如果您不确定您是否遇到磁盘空间问题，并且您使用的是New Relic帐户，请转到 [“New Relic基础架构：监视主机”页](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/). 从那里，单击 **存储** 选项卡，更改 **图表显示** 从5个结果下拉至20个，并在“已用磁盘百分比”图表或表中查看表中磁盘使用率是否较高。 有关更多详细步骤，请参阅 [“New Relic基础架构监控”>“存储”选项卡]https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage)。

如果您出现上述任何症状，请检查索引节点的状态，确保这不是由文件编号问题引起的。 为此，请在CLI/终端中运行以下命令：\
`df -ih`

IUse% > 90%吗？

a.是 — 这是由于文件过多所致。 查看在中安全删除文件的步骤 [磁盘空间不足时安全删除文件，在云基础架构上使用Adobe Commerce](/help/troubleshooting/miscellaneous/safely-delete-files-when-out-of-disk-space-adobe-commerce-on-our-cloud-architecture.md). 继续到 [步骤2](#step-2) 完成这些步骤后。 如果你想申请更多空间， [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b.否 — 检查空间。 运行 `df -h | grep mysql` 然后 `df -h | grep tmp` 在CLI/终端机中检查磁盘空间的使用 `/tmp` 和 `/data/mysql` 目录。 继续到 [步骤3](#step-3).

+++

## 步骤2 — 检查磁盘空间 {#step-2}

+++**检查磁盘空间使用情况？**

减少文件数后，运行 `df -h | grep mysql` 然后 `df -h | grep tmp` 在CLI/终端中检查磁盘空间的使用情况 `/tmp` 和 `/data/mysql`. 大于70%用于 `/tmp` 或 `/data/mysql`？

a.是 — 转到 [步骤3](#step-3).
b.否 — 查询可能会耗尽可用存储。 这可能会造成节点崩溃，从而终止查询并删除 `tmp` 文件。 检查 `SHOW PROCESSLIST;` 在MySQL CLI中查找可能导致问题的查询。 [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求更多空间。

+++

## 步骤3 — 识别高使用率的目录 {#step-3}

+++**哪个目录的使用率超过70%？**

哪个目录的使用率超过70%？ `/tmp` 或 `/data/mysql`？

>[!NOTE]
>
>默认情况下，数据库tmpdir写入 `/tmp`. 要检查您的数据库配置是否仍保留此缺省设置，请在MySQL CLI中运行以下命令： `SHOW VARIABLES LIKE "TMPDIR";` 如果数据库tmpdir仍在写入 `/tmp`，您将会看到 `/tmp` 在值列中。

答： `/tmp`  — 继续访问 [步骤4](#step-4). \
b. `/data/mysql`  — 继续访问 [步骤5](#step-5).

+++

## 步骤4 — 故障排除/tmp mount full {#step-4}

+++**/tmp装载已满故障诊断**

[Adobe Commerce的/tmp mount full故障诊断](/help/troubleshooting/miscellaneous/tmp-mount-full.md)，向下滚动文章，并尝试解决方案和最佳实践。 然后运行 `df -h | grep mysql` 然后 `df -h | grep tmp` 在CLI/终端中检查磁盘空间的使用情况 `/tmp` 和 `/data/mysql` 目录\
  &lt; 70%已使用？

>[!NOTE]
>
>中的解决方案 [Adobe Commerce的/tmp mount full故障诊断](/help/troubleshooting/miscellaneous/tmp-mount-full.md) 专门为未更改数据库tmpdir（默认写入）的变量的商家设计 `/tmp`. 如果您更改了tmpdir值，则按照 [Adobe Commerce的/tmp mount full故障诊断](/help/troubleshooting/miscellaneous/tmp-mount-full.md) 不会帮到你。

答：是的，你已经解决了这个问题。 \
b.否 —  [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求更多空间。

+++

## 步骤5 — 检查默认值 {#step-5}

+++**选中默认值**

数据库配置可能不再为原始默认值。 通过在MySQL CLI中运行来查找数据库tmpdir配置： `SELECT @@DATADIR;`. 如果 `/data/mysql/` 输出，数据库tmpdir `/data/mysql/`. 尝试按照中的步骤增加此目录中的空间 [我们的云基础架构上的Adobe Commerce上的MySQL磁盘空间不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md). 然后运行 `df -h | grep mysql` 然后 `df -h | grep tmp` 在CLI/终端中检查磁盘空间的使用情况 `/data/mysql` 和 `/tmp`.\
  &lt; 70%已使用？

答：是的，你已经解决了这个问题。 \
b.否 —  [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求更多空间。

+++

[返回步骤1](#step-1)
