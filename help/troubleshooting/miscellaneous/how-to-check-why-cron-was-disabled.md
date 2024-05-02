---
title: 如何检查原因 [!DNL cron] 已禁用
description: 本文为云基础架构产品上的Adobe Commerce中的cron问题提供了故障排除解决方案。
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# 如何检查原因 [!DNL cron] 已禁用

本文提供了有关的问题的故障排除解决方案。 [!DNL cron] 云基础架构产品上的Adobe Commerce中的。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

## 以下是 [!DNL cron] 问题：

您已经注意到 [!DNL cron] 没有运行。
例如：您会在 `app/etc/env.php` 文件：

```'cron' =>
  array (
    'enabled' => 0
  ),
```

空数组表示 [!DNL cron] 是 **已启用**：

```'cron' =>
  array (
  ),
```

## 原因

原因有多个 [!DNL cron] 当前非活动：

1. 此 [!DNL cron] 因错过而被禁用 [!DNL OpCache] 设置。
1. 基础架构团队已禁用 [!DNL cron]，因为它会导致您的网站性能不佳/不可用。
1. 此 [!DNL cron] 未重新启用，因为您的部署失败。

请参阅以下部分之一，了解您的问题的解决方案。

## 解决方案

### 针对缺失的解决方案 [!DNL OpCache] 设置 {#solution-missed-opcache-settings}

请参阅 [[!DNL Cron] 由于配置错误或缺少而停止 [!DNL OpCache] 设置](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings) 在我们的Commerce知识库中。

### 基础架构团队禁用的解决方案 {#solution-disabled-by-infrastructure-team}

1. 检查您以前的支持工单，其中您的站点已关闭或未响应。
1. 然后，检查基础架构团队是否表明他们已禁用该功能。
1. 确认您已解决基础架构团队提出的问题/顾虑。
1. 提交 [支持请求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) 如果您需要进一步的帮助来请求重新启用 [!DNL cron] 并解释您如何解决基础架构团队指出的问题。

### 部署解决方案失败 {#solution-deployment-failed}

检查部署日志：

* [查看和管理日志](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations) 在我们的Commerce on Cloud Infrastructure指南中。
* [检查Cloud UI是否具有 *`log snipped`* 错误](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error) 在我们的Commerce知识库中。

1. 如果部署在 `setup:upgrade` 步骤， [!DNL cron] 将不会重新启用。
例如：您会在部署日志中看到以下行：

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. 否则，部署可能在其他某个阶段失败。 检查部署日志，并确保这两行都显示（如下示例）。 如果您在日志中未看到与此类似的两行，则表示 [!DNL cron] 未重新启用：

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

**提交 [支持请求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets) 如果您需要进一步的帮助。**
