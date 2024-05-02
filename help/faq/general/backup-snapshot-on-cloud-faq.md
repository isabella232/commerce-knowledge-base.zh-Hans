---
title: '云上的备份（快照）：常见问题解答'
description: 本文介绍了在云基础架构上的Adobe Commerce上使用快照备份环境的要点。
exl-id: 0077db74-3e7e-4c98-b215-7f6c089f49e8
feature: Cloud, Iaas
source-git-commit: 9491279d147eac9ed36ad236c227b08e7c6e0211
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# 云上的备份（快照）：常见问题解答

本文介绍了如何在云基础架构上的Adobe Commerce上使用快照备份环境。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.x
* 体系结构计划：入门级、专业级旧版、专业级

## 环境快照， Pro计划

### 暂存和生产环境

* 在Pro计划中，手动快照不适用于暂存和生产环境。
* 创建自动快照 **无论处于何种活动状态** （也为尚未启动的站点创建快照）。 不能公开访问自动备份，因为它们存储在单独的系统中。 您可以 [提交Adobe Commerce支持票证](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 请求特殊备份，或从票证中提供日期、时间和时区的特定备份中恢复。 另外，请注意，支持人员不会为您执行数据库回滚或还原 — 他们检索快照，但您必须自行还原数据库。
* 备份是使用 **加密的Amazon Web Services Elastic Block Store (AWS EBS)快照**.
* 环境快照包括完整系统（文件系统和数据库）。
* 自动快照的保留时间 **不同** 和关注 [计划](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=en#backup-and-disaster-recovery).

>[!NOTE]
>云控制台始终显示 [!UICONTROL No backup] 在暂存和生产环境中。 您只能从集成环境中获取备份。 选择 **[!UICONTROL Backup]** 在省略号下拉菜单中。
>![cloud_console_backup.png](assets/cloud_console_backup.png)





### 集成（开发）环境

* 您的 [集成环境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) 是 **未自动备份**，但您可以创建快照 **手动**.
* 您可以为非实时存储上的集成环境创建手动快照。
* 您可能已 **多个快照** 已手动触发的响应。
* 手动触发的快照存储于 **7天**.

**我们的开发人员文档中的相关文章：**

* [备份和灾难恢复](/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [创建快照](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html)

## 环境快照，入门计划

* 所有类型的环境（集成、暂存、生产） **未自动备份**，但您可以手动创建快照。
* 您可以创建手动快照 **无论处于何种活动状态** （也为尚未启动的站点创建快照）。
* 手动触发的快照存储于 **7天**.

## 恢复环境快照

要恢复现有快照（在支持的环境中：集成、暂存、生产开始计划或集成Pro计划），请按照中的步骤操作 [备份管理：恢复手动备份](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-a-manual-backup) 在我们的Commerce on Cloud Infrastructure指南中。

## 数据库(DB)备份

数据库备份是云快照的一部分：

>>
快照是环境的完整备份，包括来自所有正在运行的服务(例如， **您的MySQL数据库**、Redis等)以及装载的卷上存储的任何文件。

>[!NOTE]
>
>装入的卷仅包含/参照 [可写挂载](/docs/commerce-cloud-service/user-guide/configure/app/properties/properties.html?lang=en#mounts) 和将不包含您的所有/app目录。 至于其他文件，它们由创建/生成 [构建和部署过程](/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=en#deployment-workflow)，您还必须从Git存储库中签出剩余的文件。

[快照和备份管理](/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) 在我们的开发人员文档中。

仅提交 [支持请求](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) 适用于从Pro Production和Staging获取数据库快照（如果您需要特定时间点的DB）。 如果仅需要数据库的当前备份（在任何环境中），请参阅知识库文章： [在云上生成数据库转储](/help/how-to/general/create-database-dump-on-cloud.md).
