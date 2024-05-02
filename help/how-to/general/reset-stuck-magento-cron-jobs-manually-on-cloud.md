---
title: 手动重置云基础架构cron作业上受阻的Adobe Commerce
description: 云基础架构上的Adobe Commerce cron作业无法完成执行、卡住并阻止其他cron作业运行。 本文介绍了如何手动重置卡住的cron作业。
exl-id: aec6de8e-c3a9-4a6d-8ecd-a213e77c97a1
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 手动重置云基础架构cron作业上受阻的Adobe Commerce

云基础架构上的Adobe Commerce cron作业无法完成执行、卡住并阻止其他cron作业运行。 本文介绍了如何手动重置卡住的cron作业。

使用此命令时请务必小心！ 我们建议您阅读 [重置cron作业](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html) 请参阅我们的支持知识库中的文章，以了解更多详细信息。

## 步骤

>[!INFO]
>
>从 [ECE-Tools v2002.0.4](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-release-archive.html#v2002.0.4) 您可以通过SSH访问使用CLI命令手动重置卡住cron作业。

1. [通过SSH连接到环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 执行此命令： `./vendor/bin/ece-tools cron:unlock`

## 警告

* 该命令会重置 **所有** CRON工作，包括那些正在运转的工作； **仅在特殊情况下使用**.
* 避免在索引器运行时使用此解决方案。

## 请阅读我们的支持知识库：

[重置cron作业](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html)
