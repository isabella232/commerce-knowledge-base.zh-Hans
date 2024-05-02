---
title: 索引失效，并且“indexer_reindex_all_invalid”不断运行
description: 索引失效，并且“indexer_reindex_all_invalid”不断运行
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# 索引失效和 `indexer_reindex_all_invalid` 持续运行

当网站因不断重新索引而出现性能问题时，本文会提供相应的可能解决方法。 这是由于 [!DNL cron] 作业 `indexer_reindex_all_invalid` 持续运行并清理缓存 [!DNL reindex].

## 受影响的产品和版本

* Adobe Commerce（云和内部部署） 2.4.0+(作为 **[!UICONTROL Category Permissions]** 是仅限Commerce的Adobe功能，它不会影响Magento Open Source。)

## 问题

在 [!DNL New Relic One] 错误日志应显示 `indexer_update_all_views` 以大于1秒的时间运行多次（即，它正在处理某些内容）。

## 原因

运行核心Adobe Commerce导入程序时(手动或 [!DNL cron])，然后执行跨多个核心模块的一组插件，以确定应该使哪些索引失效。

出现以下情况时，会出现问题 **[!UICONTROL Category Permissions]** 模块在中启用 [!DNL Commerce Admin]. 如果为true，则模块插件在执行导入时始终使Product &amp; Category索引（以及链接索引）失效。 如果检查标准导入类型，则所有导入类型都会影响 **[!UICONTROL Category Permissions]**. 预期无效。

此外，当站点启用了B2B模块时，如果 **[!UICONTROL Shared Catalog]** 激活，打开并锁定 **[!UICONTROL Category Permissions]**. 关闭 **[!UICONTROL Shared Catalog]** 将解锁 **[!UICONTROL Category Permissions]**，但不要将其关闭。

<u>正在检查 [!DNL cron] 登录 [!DNL MySQL] 数据库</u>：

如果您登录至 [!DNL MySQL] 数据库，他们可以检查您的 `cron` 日志 **[!DNL reindex all indexes]** 进程。
此 **应该** 虽然出现过很多次，但重要的是这个过程会完成两种可能的事情之一。

该过程只能执行以下两项操作之一：

1. 无：0到1秒（1秒或更短） — 该进程检查它是否需要执行任何操作，如果它不需要执行任何操作，则停止。
1. [!DNL Reindex] 一切：这始终需要时间，通常需要几分钟。

通常情况下，您会希望看到流程多次出现，但执行时间小于1秒。
商户因此可以使用此功能 [!DNL MySQL] 查询以查找采用的事务处理 **超过1秒** 要运行，请执行以下操作：

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

通过运行以下命令，您可以查看期间记录时间：

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

如果这不能为您提供足够长的时间来进行适当的评估，那么您可以增加成功评估的时间 `cron` 进程将保留在日志中，并在此之后 [[!DNL Cron] （计划任务）](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 指导并提升 **[!DNL Success History Lifetime]** 值（默认值为60分钟）。


## 解决方案

扩展 `Magento\CatalogPermissions\Model\Indexer\Plugin\Import` 这样， `afterImportSource` 方法不包括自定义导入器。

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

位置 `ENTITY_CODE` 是中实体名称参数的值 `import.xml` 自定义导入器的文件。

## 相关阅读

[配置 [!DNL cron] 作业](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 《Adobe Commerce操作配置指南》中的。
