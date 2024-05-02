---
title: 在云基础架构上重置Adobe Commerce上的环境
description: 本文显示了在Adobe Commerce上回滚云基础架构上环境的各种方案。
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: f2aeb0262ddcb3d7e78028d08b9323db243fc96b
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 0%

---

# 在云基础架构上重置Adobe Commerce上的环境

本文显示了在Adobe Commerce上回滚云基础架构上环境的各种方案。

选择最适合您的具体情况：

* 如果您有计划的活动（计划的部署或升级） —  [场景1：计划活动)](#scen1).
* 如果您具有有效的快照 —  [场景2：恢复快照](#scen2).
* 如果您具有稳定的内部版本，但没有有效的快照 —  [场景3：无快照，构建稳定（可用SSH连接）](#scen3).
* 如果内部版本已损坏，并且您没有有效的快照 —  [场景4：没有快照；构建中断（没有SSH连接）](#scen4).

## 场景1：计划活动

在计划的部署或升级中，最简单、建议使用的是 [!UICONTROL Rollback] 作为准备工作的一部分，将允许商家执行以下操作：

>[!NOTE]
>
>请始终在您的网站中测试这些步骤 **[!UICONTROL Staging Environment]** 第一！

<u>在升级/部署活动开始前的5天</u>：

1. 检查当前数据库的大小。
1. 检查您是否有足够的磁盘空间 `/data/exports` 保留 [!UICONTROL Database Dump]. 如果磁盘空间不足，请删除不需要的数据，或者创建支持案例并请求扩展磁盘。

<u>更改日期</u>：

1. 将网站放置到 [!UICONTROL Maintenance Mode].<br>
详细了解 [启用或禁用 [!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html) ，以及 [[!UICONTROL Maintenance Mode] 升级选项](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html) ，位于我们的升级指南中。
1. 以本地为例 [[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html).

<u>如果 [!UICONTROL Rollback] 为必填项</u>：

1. 如果应用程序 [!DNL MariaDB] 已作为此计划活动的一部分升级，请首先将该应用程序重新安装到以前的版本。
1. [!UICONTROL Rollback] 数据库使用本地 [!UICONTROL Database Dump]，并将其导入回 [!DNL MariaDB].
1. [!UICONTROL Rollback] 代码通过 [!DNL Git] 到上一个工作版本。

使用 [!UICONTROL Snapshots] 不建议采用的方法进行升级/计划的活动 [!UICONTROL rollbacks/restores]，因为检索数据所需的时间要比检索本地数据所需的时间长得多 [!UICONTROL Database Dump]，如上面的步骤2中所述 **如果 [!UICONTROL Rollback] 为必填项** 部分。

[!UICONTROL Snapshots] 它们不是保存在节点/服务器上，而是保存在单独的存储块上，而且由于数据必须通过网络从块存储传输到新磁盘，所以这个过程需要时间。 然后，将该新磁盘装载到节点上，准备检索/导入到连接到节点/服务器的原始磁盘上。

当您将此与导入本地环境进行比较时 [!UICONTROL Database Dump]，则节点/服务器上已经可以检索数据，因此可以将大量时间仅保存为 [!UICONTROL Database Import] 为必填项。

## 场景2：恢复快照

阅读： [在云基础架构上的Adobe Commerce上恢复快照](https://devdocs.magento.com/cloud/project/project-webint-snap.html#restore-snapshot) 在我们的开发人员文档中。

>[!NOTE]
>
>在访问云基础架构帐户上的Adobe Commerce之后以及在应用重大更改之前，创建快照必须是我们的第一步。 这是最佳实践，强烈推荐。

阅读： [创建快照](https://devdocs.magento.com/cloud/project/project-webint-snap.html#create-snapshot) 在我们的开发人员文档中。

## 场景3：无快照，构建稳定（可用SSH连接）

此部分说明如何在尚未创建快照但可以通过SSH访问环境时重置环境。

步骤如下：

1. 禁用配置管理。
1. 卸载Adobe Commerce软件。
1. 重置 [!DNL git] 分支。

执行这些步骤后：

* Adobe Commerce安装将返回到其Vanilla状态(数据库已恢复；删除了部署配置；目录位于 `var` 已清除)。
* 您的 [!DNL git] 分支在过去被重置为所需的状态。

请阅读下面的详细步骤。

### 步骤0（先决条件）：删除config.php以禁用配置管理

我们需要禁用配置管理，以便它不会在部署期间自动应用以前的配置设置。

要禁用配置管理，请确保 `/app/etc/` 目录不包含 `config.php` 文件。

要删除配置文件，请执行以下步骤：

1. [通过SSH连接到环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 删除配置文件： `rm app/etc/config.php`

阅读有关配置管理的更多信息：

* [减少云基础架构上Adobe Commerce的部署停机时间](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md) 在我们的支持知识库中。
* [商店设置的配置管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) 在我们的开发人员文档中。

### 步骤1：使用setup：uninstall命令卸载Adobe Commerce软件


卸载Adobe Commerce软件将删除并恢复数据库，删除部署配置，并清除以下目录 `var`.

阅读： [卸载Adobe Commerce软件](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html) 在我们的开发人员文档中。

要卸载Adobe Commerce软件，请执行以下步骤：

1. [通过SSH连接到环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 执行 `setup:uninstall` ： `bin/magento setup:uninstall`
1. 确认卸载。

将显示以下消息以确认卸载成功：

```php
[SUCCESS]: Magento uninstallation complete.
```

这意味着我们已将Adobe Commerce安装（包括DB）恢复到其正版(Vanilla)状态。

### 第2步：重置 [!DNL git] 分支

替换为 [!DNL git] 重置，我们会将代码还原到过去所需的状态。

1. 将环境克隆到本地开发环境。 您可以在Cloud Console中复制命令：    ![copy_git_clone.png](assets/copy_git_clone.png)
1. 访问提交历史记录。 使用 `--reverse` 为了更加方便起见，请按相反顺序显示历史记录： `git log --reverse`
1. 选择已完成的提交哈希。 要将代码重置为其真实状态(Vanilla)，请查找创建分支（环境）的第一次提交。
   ![在Git控制台中选择承诺哈希](assets/select_commit_hash.png)
1. 硬应用 [!DNL git] 重置： `git reset --h <commit_hash>`
1. 将更改推送到服务器： `git push --force <origin> <branch>`

执行这些步骤后，我们的 [!DNL git] 分支将重置，并且整个 [!DNL git] 更改日志已清除。 最后一个 [!DNL git] 推送会触发重新部署以应用所有更改并重新安装Adobe Commerce。

## 场景4：无快照；内部版本损坏(否 [!DNL SSH] connection)

本节说明如何在环境处于关键状态时重置环境：部署过程无法成功构建工作应用程序，从而导致 [!DNL SSH] 连接不可用。

在此方案中，您必须首先使用恢复Adobe Commerce应用程序的工作状态 [!DNL git] 重置，然后卸载Adobe Commerce软件（删除和恢复数据库、删除部署配置等）。 该场景包含与场景3相同的步骤，但步骤顺序不同，并且还有一个额外的步骤 — 强制重新部署。 步骤如下：

1. [重置 [!DNL git] 分支。](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [禁用配置管理。](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [卸载Adobe Commerce软件。](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. 强制重新部署。

执行这些步骤后，您的结果将与场景3中的结果相同。

### 步骤4：强制重新部署

进行提交（这可能是空提交，但我们不建议这样做）并将它推送到服务器以触发重新部署：

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## 如果安装：卸载失败，请手动重置数据库

如果执行 `setup:uninstall` 命令因错误而失败，无法完成，我们可以通过以下步骤手动清除数据库：

1. [通过SSH连接到环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. 连接到MySQL数据库： `mysql -h database.internal` (对于Pro环境，请参阅： [设置MySQL服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html))。
1. 放下 `main` 数据库： `drop database main;`
1. 创建空的 `main` 数据库： `create database main;`
1. 删除以下配置文件： `config.php` ， `config.php` ， `.bak,` ， `env.php`， `env.php.bak`

重置数据库后， [设为 [!DNL git] 推送到环境以触发重新部署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html) 并将Adobe Commerce安装到新创建的数据库中。 或 [运行重新部署命令](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html#environment-commands).
