---
title: 数据迁移工具故障排除
description: 本文提供了在运行数据迁移工具时可能发生的错误的解决方案。
exl-id: 9beb31ae-ed3c-42e1-b0bf-33fb1c91e0ea
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# 数据迁移工具故障排除

本文提供了在运行数据迁移工具时可能发生的错误的解决方案。

## 未映射源文档/字段 {#source-documents-fields-not-mapped}

### 错误消息

* ```bash    Source documents are not mapped: <EXTENSION_TABLE>    ```
* ```bash    Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <EXTENSION_FIELD>    ```

在极少数情况下，该邮件可能会提及

```bash
Destination documents
```

或

```bash
Destination fields
```

而不是源代码。

### 原因

某些Adobe Commerce版本1实体（大多数情况下来自扩展）在Adobe Commerce版本2数据库中不存在。

出现此消息的原因是，数据迁移工具运行内部测试以验证表和字段之间是否一致。 *源* (Adobe Commerce 1)及 *目标* (Adobe Commerce 2)数据库。

### 可能的解决方案

* 从安装相应的Adobe Commerce 2扩展 [Commerce Marketplace](https://marketplace.magento.com/).     如果冲突的数据源自添加自己的数据库结构元素的扩展，则相同扩展的Adobe Commerce 2版本可以将此类元素添加到目标(Adobe Commerce 2)数据库中，从而修复问题。
* 使用 `-a` 参数以执行工具以自动解决错误并阻止迁移停止。
* 配置工具以忽略有问题的数据。

要忽略数据库实体，请添加 `<ignore>` 标记到中的实体 `map.xml` 文件，如下所示：

```xml
...
    <source>
        <document_rules>
            ...
            <!-- Ignore `sales_flat_invoice_grid` table -->
            <ignore>
                <document>sales_flat_invoice_grid</document>
            </ignore>
            <!-- Ignore `address_id` field of `sales_flat_order_address` table -->
            <ignore>
                <field>sales_flat_order_address.address_id</field>
            </ignore>
            ...
        </document_rules>
    </source>
    ...
```

>[!WARNING]
>
>在按映射文件忽略图元或使用 `-a` 选项，确保您的Adobe Commerce 2存储中不需要受影响的数据。

## 类未在记录中映射 {#class-does-not-exist-but-mentioned}

### 错误消息

```bash
Class <extension/class_name> is not mapped in record <attribute_id=196>
```

### 原因

在Adobe Commerce 2代码库中找不到Adobe Commerce 1代码库中的类 [EAV迁移步骤](https://devdocs.magento.com/guides/v2.3/migration/migration-tool-internal-spec.html#eav) 在我们的开发人员文档中。 在大多数情况下，缺少的类属于 [扩展](https://glossary.magento.com/extension).

### 可能的解决方案

* 安装相应的Adobe Commerce 2扩展。
* 忽略导致问题的属性。    为此，将属性添加到 `ignore` 组中的组 `eav-attribute-groups.xml.dist` 文件。
* 使用添加类映射 `class-map.xml.dist` 文件。

## 外键约束失败

### 错误消息文本

```bash
Foreign key <KEY_NAME> constraint fails on source database. Orphan records id: <id_1>, <id_2> from <child_table>.<field_id> has no referenced records in <parent_table>
```

### 原因

中缺少数据库记录 `parent_table` ，则 `field_id` 的 `child_table` 正指向。

### 可能的解决方案

从删除记录 `child_table` ，如果您不需要它们。

要保留记录，请禁用 `Data Integrity Step` 通过修改数据迁移工具的 `config.xml` .

## URL重写中存在重复项

```xml
There are duplicates in URL rewrites:
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/10
Request path: towel.html Store ID: 2 Target path: catalog/product/view/id/12
```

### 原因

此 `Target path` 在URL重写中，必须由唯一的 `Request path` + `Store ID` . 此错误报告使用相同的两个条目 `Request path` + `Store ID` 与两个不同对象配对 `Target path` 值。

### 可能的解决方案

启用 `auto_resolve_urlrewrite_duplicates` 中的选项 `config.xml` 文件。

此配置向冲突记录添加一个哈希字符串 [URL](https://glossary.magento.com/url) 重写并在命令行界面中显示解析结果。

## 实体不匹配 {#mismatch-of-entities}

### 错误消息

```bash
Mismatch of entities in the document: <DOCUMENT> Source: <COUNT_ITEMS_IN_SOURCE_TABLE> Destination: <COUNT_ITEMS_IN_DESTINATION_TABLE>
```

### 原因

在“Volume Check（卷检查）”步骤中出错。 这意味着文档的Adobe Commerce 2数据库记录数与Adobe Commerce 1中的不同。

当客户在迁移过程中下订单时，会发生丢失记录。

### 可能的解决方案

在中运行数据迁移工具 `Delta` 用于传输增量更改的模式。

## 未安装Deltalog {#deltalog-is-not-installed}

### 错误消息

```bash
Deltalog for <TABLE_NAME> is not installed
```

### 原因

此错误发生于 [增量迁移](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-delta.html) （在我们的开发人员文档中）更改数据。 这意味着删除表（带前缀） `m2_cl_*`)在Adobe Commerce 1数据库中未找到。 该工具会在以下过程中安装这些表： [数据迁移](https://devdocs.magento.com/guides/v2.3/migration/migration-migrate-data.html) （位于我们的开发人员文档中）以及数据库触发器，用于跟踪更改和填充增量表。

出现该错误的一个原因可能是您正在尝试从 *复制* Adobe Commerce ，而不是来自Live Store本身。 当您从从未迁移的Adobe Commerce 1实时存储中创建副本时，该副本不包含完成增量迁移所需的触发器和其他增量表，因此迁移失败。 数据迁移工具不会比较AC1和AC2的DB以迁移差异。 相反，该工具使用在首次迁移期间安装的触发器和增量表来执行后续的增量迁移。 在这种情况下，实时Adobe Commerce 1数据库的副本将不包含数据迁移工具用于执行迁移的触发器和删除表。

### 可能的解决方案

我们建议从Adobe Commerce 1数据库的副本测试迁移过程以修复迁移问题。 修复了副本上的问题后，从实时Adobe Commerce 1数据库中重新开始迁移过程。 这将有助于确保顺利迁移过程。
