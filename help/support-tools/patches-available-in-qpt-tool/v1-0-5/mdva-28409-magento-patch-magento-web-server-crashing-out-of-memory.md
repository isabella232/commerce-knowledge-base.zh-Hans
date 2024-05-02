---
title: 'MDVA-28409修补程序：Adobe Commerce Web服务器崩溃 — 内存不足'
description: MDVA-28409修补程序解决了由于必须处理大量项目而导致用于删除报价的cron作业停止的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.5后，即可使用此修补程序。
exl-id: 175e5f2f-2f76-42ee-83e9-c1b23ff81e96
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-28409修补程序：Adobe Commerce Web服务器崩溃 — 内存不足

MDVA-28409修补程序解决了由于必须处理大量项目而导致用于删除报价的cron作业停止的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装v.1.0.5。

## 受影响的产品和版本

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.4 - 2.3.5、2.4.0

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

问题是cron作业内存不足，因为作业尝试处理的数据量太大。 此问题的症状包括由于MySQL的磁盘使用率高和Web服务器内存不足而导致性能变慢。

<u>重现问题的步骤：</u>

要检查是否存在无法删除过期引号的cron作业，请运行以下查询：

```
select * from cron_schedule where job_code like '%sales_clean_quotes%'
```

<u>预期结果：</u>

的状态 `sales_clean_quotes` cron作业应为 `success`.

<u>实际结果：</u>

的状态 `sales_clean_quotes` cron作业为 `running` 或 `error`.

确认存在无法删除过期引号的cron作业的另一种方法是从映射查询的输出 **步骤1** (`executed_at`)的时间戳记来表示。 `/var/log/cron.log`. 如果某个cron作业无法处理大量数据，您可能会看到与以下内容类似的消息：

```
PHP Fatal error:  Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91

Fatal error: Allowed memory size of 1073741824 bytes exhausted (tried to allocate 4096 bytes) in /app/vendor/magento/framework/DB/Statement/Pdo/Mysql.php on line 91
--
[2020-05-30 05:00:27.224718] Launching command 'php bin/magento cron:run'.
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
