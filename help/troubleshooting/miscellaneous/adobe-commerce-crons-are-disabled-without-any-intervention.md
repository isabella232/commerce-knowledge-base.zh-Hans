---
title: Adobe Commerce [!DNL crons] 无干预残疾
description: 使用本文修复以下问题： [!DNL crons] 已禁用，无需干预。
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 9cd7cabc37c0f290c41f790b0fb06177c3156d48
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons已禁用，无需干预

本文为以下情况提供了解决方案： [!DNL crons] 已禁用，无需干预。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，全部 [支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 问题

您的 [!DNL crons] 在部署后禁用。

<u>重现问题的步骤</u>：

部署。

<u>预期结果</u>：

您的 [!DNL crons] 正在运行。

<u>实际结果</u>：

您的 [!DNL crons] 在部署后禁用。

## 原因

的问题 [!DNL OPcache] 设置。

## 解决方案

升级 [!DNL ECE Tools] 到最新版本 [2002.1.13](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html#v2002113).

## 相关阅读

* [性能缓慢、运行缓慢且时间长 [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html) 在我们的支持知识库中。
* [[!DNL Cron] 任务从其他组锁定任务](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en) 在我们的支持知识库中。
* [[!DNL Cron] 作业卡在“正在运行”状态](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) 在我们的支持知识库中。
