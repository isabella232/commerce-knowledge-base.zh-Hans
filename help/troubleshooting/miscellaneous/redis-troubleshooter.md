---
title: Adobe Commerce上的Redis疑难解答
description: 本文是适用于Adobe Commerce内部部署和Adobe Commerce的故障排除工具，适用于云基础架构商家遇到与Redis相关的问题。 单击每个问题以显示故障诊断程序每个步骤的答案。 根据您的症状和配置，故障诊断程序将说明如何解决版本和内存问题并优化性能。
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Adobe Commerce上的Redis疑难解答

本文是适用于Adobe Commerce内部部署和Adobe Commerce的故障排除工具，适用于云基础架构商家遇到与Redis相关的问题。 单击每个问题以显示故障诊断程序每个步骤的答案。 根据您的症状，故障诊断程序将说明如何解决版本和内存问题并优化性能。

## 步骤1 - Redis问题 {#step-1}

+++Redis问题？

a.是 — 转到 [步骤2](#step2)</a>.

b.否 — 返回至 [support.magento.com](https://support.magento.com/hc/en-us) 和搜索相关的故障排除文章。

+++

## 步骤2 — 确认安装了Redis修补程序 {#step-2}

+++是否安装了当前的Redis修补程序？

a.是 — 转到 [步骤3](#step3)</a>.

b.否 — 确保您拥有最新版本的软件包 `magento-cloud-patches` 已安装。 此软件包具有用于Redis的必要修补程序。 要访问，请转到 [GitHub磁云修补程序](https://github.com/magento/magento-cloud-patches/).

+++

## 步骤3 — 确认支持Redis版本 {#step-3}

+++在Redis版本3.2或5.0上？

通过在CLI中运行以下命令来检查。 Pro或Staging： `$ redis-cli -p %port-number% info | grep redis_version`，其中 `%port-number%` 是端口编号，该编号可在 `app/etc/env.php` 文件或运行以下命令之一： `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` 或 `$ cat app/etc/env.php | grep redis -A 3` 入门或集成： `$ redis-cli -h 'redis.internal' info | grep redis_version`

a.是 — 转到 [步骤4](#step4).

b.否 — Adobe Commerce支持Redis版本3.2和5.0。如果您在云基础架构2.3.3或更高版本上运行Adobe Commerce，我们建议您升级到Redis 5。 有关云基础架构上Adobe Commerce的设置步骤专业规划架构、集成和入门环境（包括主分支），请参阅 [云基础架构上的Adobe Commerce >设置Redis服务](https://devdocs.magento.com/cloud/project/services-redis.html)</a> 在我们的开发人员文档中。 **您必须 [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 更改Pro体系结构生产和暂存环境中的服务配置。 此外，对于云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.5+，建议实施扩展的Redis缓存。 此类型的Redis缓存实施提供了增强功能，可最大限度地减少针对每个Adobe Commerce请求执行的Redis查询次数。 有关步骤，请参阅 [扩展Redis缓存实施Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) 在我们的支持知识库中。 对于所有其他Adobe Commerce用户，请参阅 [Adobe Commerce配置指南>配置Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) 有关步骤，请参阅我们的开发人员文档。

+++

## 步骤4 — 验证ECE-Tools的最新版本 {#step-4}

+++您是否拥有最新版本的 [ECE工具> v2002.1.1](https://github.com/magento/ece-tools/releases)？

通过在CLI/终端中运行命令来检查您具有的版本： `$php vendor/bin/composer info magento/ece-tools`.

a.是 — 转到 [步骤5](#step5).

b.否 —  [升级ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) 到最新版本。

+++

## 步骤5 — 评估网络流量 {#step-5}

+++应用程序和Redis之间是否有大量网络流量？

a.是 — 尝试以下操作：对于非拆分架构，请确保 [辅助连接](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) 已使用。 对于拆分体系结构， [必须启用二级缓存](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. NO — 配置L2缓存的方法有 [更新Redis后端](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). 继续到 [步骤6](#step6).

+++

## 步骤6 — 检查站点速度 {#step-6}

+++启用L2缓存后，站点是否仍在缓慢工作？

a.是 — 检查临时目录 `/dev/shm` 看看你是否需要增加空间。 如果你需要更多空间， [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b.否 — 启用L2缓存似乎已解决您的Redis问题。

+++

[返回步骤1](#step-1)
