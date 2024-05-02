---
title: 云上的Adobe Commerce存在变量/导出文件夹权限问题
description: 解决由于服务器“var/export/email”文件夹中的文件权限问题而无法导出产品数据的问题，本文提供了解决方案。 症状包括产品和目录导出在用户界面中不可用，但在使用SSH时可见。
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 云上的Adobe Commerce存在变量/导出文件夹权限问题

本文提供了解决方案，来解决由于中的服务器存在文件权限问题而无法导出产品数据的问题。 `var/export/email` 文件夹。 症状包括产品和目录导出在用户界面中不可用，但在使用SSH时可见。

## 受影响的产品和版本

云基础架构上的Adobe Commerce，2.3.0-2.3.7-p2、2.4.0-2.4.3-p1

## 问题

不能在中导出文件 `var/export/email` 或 `var/export/archive` 文件夹。
由于以下项的权限，部署失败： `var/export/email` 或 `var/export/email/archive` 因为存档文件夹是在电子邮件下创建的，如果我只是执行导出/电子邮件操作，有时仍会遇到问题)，无法添加内容以说明子文件夹 `var/export/email/archive`.

<u>重现问题的步骤</u>：

在“管理员”中，转到 **系统** > *数据传输* > **导出**.
选择要保存在中的CSV文件 `var/export/` 文件夹。

<u>预期结果</u>：

CSV文件可见，并且可以导出。

<u>实际结果</u>：

CSV文件不可见。 您还会看到一条权限被拒绝消息： *RecursiveDirectoryIterator：：__construct(/app/project id>/var/export/email)：无法打开目录：权限被拒绝*

对于所有导出类型，您都会收到相同的消息：“高级定价”、“客户财务”、“客户主文件”和“客户地址”。

## 原因

这是由于在中创建的文件夹导致的 `/var` 具有不完美权限的用户： `d-wxrwsr-T`. T粘性位表示用户只能删除他们拥有的文件，而缺少可执行文件则表示他们无法在目录中创建文件。

当系统创建名为的文件夹时，经常会注意到这种情况 `export`，其中包含名为的文件夹 `email`，其中包含名为的文件夹 `archive`.

要检查目录是否具有这些配置错误的权限，请在CLI/终端中运行以下命令：

`ls -ld var/export/`

如果权限配置错误，输出将为：

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## 解决方案

要解决此问题，请运行以下命令，将文件夹的权限更新为777 ，然后递归更新所有文件：

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## 相关阅读

* [导出](https://docs.magento.com/user-guide/system/data-export.html) 在我们的用户指南中。
