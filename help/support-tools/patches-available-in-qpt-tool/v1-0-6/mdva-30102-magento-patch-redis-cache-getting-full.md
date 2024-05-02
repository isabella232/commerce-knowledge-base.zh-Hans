---
title: 'MDVA-30102： Redis缓存已满'
description: MDVA-30102修补程序解决了Redis缓存已满并生成错误的问题，该错误会导致产品列表页面(PLP)和产品详细信息页面(PDP)出现问题，例如缺少产品。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6后，即可使用此修补程序。
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102：Redis缓存已满

MDVA-30102修补程序解决了Redis缓存已满并生成错误的问题，该错误会导致产品列表页面(PLP)和产品详细信息页面(PDP)出现问题，例如缺少产品。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.6。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Redis缓存已满，并且已分配 `maxmemory` 似乎不够。 布局缓存没有TTL，并且未被逐出，导致缓存增长并逐出Redis中的其他键。 因此，所有Redis内存都被分配给布局缓存。

<u>先决条件</u>：

* 用户必须使用Adobe Commerce 2.4，并且具有100,000个简单产品（产品类型无关紧要）和50个类别。
* 必须按照中给出的步骤配置Redis缓存 [Adobe Commerce配置指南>为Adobe Commerce页面和默认缓存使用Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) 在我们的开发人员文档中。

<u>重现问题的步骤</u>：

1. 浏览所有PDP和PLP。 您可以使用 [OWASP ZAP](https://www.zaproxy.org/) 以爬取站点。
1. 观察Redis内存使用情况。
1. 另外，检查当前配置和已使用的内存。 在CLI中运行以下命令。 它检查已用内存、最大内存、已收回密钥和Redis的启动时间（以天为单位）：

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>预期结果</u>：

Redis缓存不应快速增长。

<u>实际结果</u>：

Redis高速缓存可增长到约5 GB。 Redis内存的最大限制为8 GB，因此如果您有100万种产品，则内存会很快用完。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
