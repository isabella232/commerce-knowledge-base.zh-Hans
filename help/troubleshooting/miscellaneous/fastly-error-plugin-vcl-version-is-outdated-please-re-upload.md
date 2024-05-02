---
title: 'Fastly错误：插件VCL版本已过时！ 请重新上传'
description: 当您看到消息“*Plugin VCL版本已过时”时，本文会为您提供解决方案！ 请重新上传。*”在Commerce管理员的Fastly配置中，由于未安装最新的Fastly模块。
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 快速错误：插件VCL版本已过时！ 请重新上传

本文提供了一种解决方案，让您能够及时看到消息“*插件VCL版本已过时！ 请重新上传。*”在Fastly配置中，在Commerce管理员中，由于未安装最新的Fastly模块。

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.2.x.、2.3.x<br>
Fastly：此错误可能会影响Fastly模块的所有版本，但最新版本除外。 有关最新版本的信息，请参阅 [Fastly发行说明](https://github.com/fastly/fastly-magento2/releases) 在GitHub上。

## 问题

1. 登录到Commerce管理面板。
1. 导航到 **商店** > **配置** > **高级** > **系统** > **全页缓存**   **快速缓存。**
1. 在 **自动上传和服务激活** 部分，将有一个&quot;*插件VCL版本已过时！ 请重新上传。*”通知。
1. 您尝试通过单击“Upload VCL to Fastly”按钮来上传VCL片段，但您仍然看到警告&#x200B;*插件VCL版本已过时！ 请重新上传。*&quot;

## 原因

Fastly扩展已更新（以及捆绑的VCL配置和模板），但更新的VCL配置尚未上载到Fastly服务。 更新Adobe Commerce模块时 `Fastly_Cdn`，您必须再次向Fastly上传更新的VCL配置。

## 解决方案

1. 检查您是否安装了最新的ECE-Tools，并且 [当前版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html) 在我们的开发人员文档中。 ECE-Tools在其依赖项中有一个版本的Fastly包。

   这可能不是Fastly插件的最新版本，但可能是比您当前安装的版本更新的版本，最佳做法是安装最新的ECE工具。

1. 如果您不在当前版本的ECE-Tools上，请按照以下步骤操作 [升级](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html) 在我们的开发人员文档中。
1. 升级ECE-Tools后，检查您现在是否拥有当前版本的 [Fastly插件](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets) 已安装。
1. 如果Fastly插件不是当前版本，请按照以下步骤操作 [将插件升级到最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module) 在我们的开发人员文档中。

## 相关阅读

* 有关设置和配置Fastly的信息，请参阅 [配置Fastly服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) 在我们的开发人员文档中。
* 有关Fastly的一般信息，请参见 [fastly.com](https://www.fastly.com/).
