---
title: 'MDVA-29389：高级报告相关cron作业失败'
description: “MDVA-29389修补程序修复了高级报表中存在的一个问题，即“analytics_collect_data”cronjob指示：“*Port必须在主机参数（如localhost：3306）*”中进行配置。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 修补程序ID为MDVA-29389。 已在Adobe Commerce 2.4.2中修复此问题。'
exl-id: eee909d5-9d0d-46b6-846a-665f89db0eee
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-29389：高级报告相关cron作业失败

MDVA-29389修补程序修复了高级报表的问题，其中 `analytics_collect_data` cronjob说：“*必须在host参数（如localhost：3306）中配置端口*“。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.7。 修补程序ID为MDVA-29389。 已在Adobe Commerce 2.4.2中修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法）2.3.4。

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.3.0 - 2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 在Adobe Commerce实例中，启用高级报告。
1. 运行以下查询以在数据库中插入analytics/general/token值：

   ```sql
   INSERT INTO core_config_data VALUES(NULL,'default',0,'analytics/general/token','ABCDE',now());
   ```

1. 打开env.php并按照以下格式在数据库配置中将端口添加到主机参数： `'host' => 'hostname:port',`
1. 清除缓存。
1. 执行 `analytics_collect_data` cron作业。

<u>预期结果</u>：

此 `analytics_collect_data` 在env.php中使用默认或非默认端口连接到MySQL时，作业成功运行。

<u>实际结果</u>：

此 `analytics_collect_data` 作业引发错误&#39;&#39;*必须在host参数（如localhost：3306）中配置端口*”（使用非默认端口连接到env.php中的MySQL）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
