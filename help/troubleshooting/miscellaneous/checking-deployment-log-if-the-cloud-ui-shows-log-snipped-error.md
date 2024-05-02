---
title: 检查部署日志，如果Cloud UI出现“日志截断”错误
description: 本文为以下问题提供了解决方案：云基础架构上的Adobe Commerce UI在尝试查看部署日志时显示*日志片段，因为它太长*错误消息。
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 检查部署日志，如果Cloud UI出现“日志截断”错误

本文为云基础架构UI上的Adobe Commerce显示的问题，提供了一个解决方案 *日志被截断，因为它太长* 尝试查看部署日志时出现错误消息。

## 受影响的产品

云基础架构上的Adobe Commerce（所有受支持的版本）

## 问题

在尝试查看部署日志时，云基础架构UI上的Adobe Commerce显示以下错误消息： *日志被截断，因为它太长*.

## 重现问题的步骤

1. 转到项目URL并单击 **状态** 相关部署的ID。
1. 如果日志太长而无法在UI中显示，则会显示错误消息： *日志被截断，因为它太长*.

## 原因

请注意，不应将UI中显示的日志视为事实来源，尤其是当您在以“成功”状态列出部署后发现站点未响应或无法正常工作时。 您还应使用服务器上的日志进行验证。 请参阅 [查看和管理日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) 在我们的开发人员文档中。

## 解决方案

1. 确保您拥有 [MagentoCloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html) 已安装在本地环境中。
1. 运行以下命令：

   ```bash
   magento-cloud activity -p <project id> -e <environment>
   ```

1. 它将返回类似于以下内容的输出：

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. 复制受影响部署的活动ID，然后运行命令：

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   检查失败部署的日志的示例：

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## 我们的开发人员文档中的相关阅读：

* [云基础架构上的Adobe Commerce >构建和部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)
* [云基础架构上的Adobe Commerce >查看和管理日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
