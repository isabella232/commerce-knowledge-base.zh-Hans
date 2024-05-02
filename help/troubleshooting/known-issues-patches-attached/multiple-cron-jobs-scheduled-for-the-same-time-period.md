---
title: 为同一时间段计划了多个CRON作业
description: 本文为已知的Adobe Commerce 2.2.2问题提供了一个修补程序，该问题与在Commerce管理员中编辑某些任务的时间变量后计划同时运行多个cron作业有关。
exl-id: a3c1fe77-ed4c-43b5-8d6f-e5c549096c73
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# 为同一时间段计划了多个CRON作业

本文为已知的Adobe Commerce 2.2.2问题提供了一个修补程序，该问题与在Commerce管理员中编辑某些任务的时间变量后计划同时运行多个cron作业有关。

## 问题

如果将cron配置为每分钟运行一次，那么如果您在Admin中编辑三个计划任务的时间变量， `cron_schedule` 数据库表显示计划同时运行的多个任务组。

<u>重现问题的步骤</u>：

1. 在Commerce管理中，导航到 **商店** >设置> **配置** > **高级** > **系统** > **Cron（计划任务）** > **组的Cron配置选项：默认。**
1. 配置以下选项：
   * **历史记录清理间隔**：清除 **使用系统** 复选框，并将设置为 *1440*.
   * **成功历史记录生命周期**：清除 **使用系统** 复选框，并将设置为 *1440*.
   * **失败历史记录生命周期**：清除 **使用系统** 复选框，并将设置为 *1440*.

1. 单击 **保存配置**.
1. 在SSH中，运行 `crontab -e` 命令。
1. 将cron设置为每分钟运行一次。
1. 打开三个终端选项卡/窗口。
1. 转到Adobe Commerce `root/base/project` 目录。
1. 在每个选项卡/窗口中运行以下命令：

   ```bash
   bin/magento cache:flush && bin/magento cron:run && bin/magento cache:flush && bin/magento cron:run
   ```

1. 转到MySQL并运行以下查询：

   ```sql
   SELECT job_code, scheduled_at, count as count FROM cron_schedule GROUP BY job_code, scheduled_at HAVING count > 1 ORDER BY scheduled_at;
   ```

1. 查看计划同时运行的任务组。

<u>预期结果</u>：一个cron `job_code` 应该安排在特定时间段内。

<u>实际结果</u>：同一时间段内计划了多个cron作业。

## 解决方案

对于Adobe Commerce on cloud infrastructure商家， [更新ECE工具](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) 可以解决这个问题。

Adobe Commerce本地商家应应用附加的修补程序之一来解决此问题。

## 补丁程序

修补程序已附加到本文。 要下载，请向下滚动到文章的结尾并单击文件名，或单击以下链接之一：

* [下载MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip)
* [下载MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip)
* [下载MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* [下载MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip)
* [下载MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip)
* [下载MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip)
* [下载MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip)

### 兼容的Adobe Commerce版本

修补程序是为修补程序文件名中注明的特定版本创建的。 例如，MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch是为Adobe Commerce 2.2.4创建的，它是用于此版本的最佳修补程序。

这些修补程序还与以下版本兼容：

* 对于Adobe Commerce内部部署2.1.0 - 2.1.4： [下载MDVA-11304\_EE\_2.1.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.4_COMPOSER_v1.patch.zip) 该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：
   * 云基础架构上的Adobe Commerce 2.1.0 - 2.1.4
* 对于Adobe Commerce内部部署2.1.5 - 2.1.12： [下载MDVA-11304\_EE\_2.1.5\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.5_COMPOSER_v1.patch.zip) 该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：
   * 云基础架构上的Adobe Commerce 2.1.5 - 2.1.12
* 对于Adobe Commerce on cloud infrastructure 2.1.13： [下载MDVA-11304\_EE\_2.1.13\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.13_COMPOSER_v1.patch.zip)
* 对于Adobe Commerce内部部署2.1.14-2.1.17： [下载MDVA-11304\_EE\_2.1.14\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.1.14_COMPOSER_v1.patch.zip) 该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：
   * Adobe Commerce内部部署2.1.18
   * 云基础架构上的Adobe Commerce 2.1.14-2.1.18
* 对于Adobe Commerce内部部署2.2.0 - 2.2.1： [下载MDVA-11304\_EE\_2.2.0\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.0_COMPOSER_v1.patch.zip) 该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：
   * 云基础架构上的Adobe Commerce 2.2.0 - 2.2.1
* 对于Adobe Commerce内部部署2.2.0 - 2.2.3： [下载MDVA-11304\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.2_COMPOSER_v1.patch.zip) 该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：
   * 云基础架构上的Adobe Commerce 2.2.0 - 2.2.3
* 对于Adobe Commerce内部部署2.2.4： [下载MDVA-11304\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-11304_EE_2.2.4_COMPOSER_v1.patch.zip) 该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：
   * 云基础架构上的Adobe Commerce 2.2.4

## 如何应用修补程序

请参阅 [如何应用Adobe Commerce提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) ，以获取相关说明。

## 附加文件
