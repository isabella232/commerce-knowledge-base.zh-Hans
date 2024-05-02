---
title: 在云基础架构上删除Adobe Commerce的Blackfire访问权限
description: 2020年4月11日，Adobe Commerce on cloud infrastructure Pro计划架构或Adobe Commerce on cloud infrastructure入门计划架构订阅将不再包括免费访问Blackfire性能监控。  您将无法再登录到您的Blackfire帐户。 在4月11日之后，可以直接通过Blackfire.io购买许可证，以继续使用Blackfire。 Adobe Commerce如果到2015年12月14日尚未直接从Blackfire购买许可证，则将停用其免费的Adobe提供Blackfire许可证。 除此之外，将禁用使用Profiler工具创建新报告的功能。 使用托管在云基础架构上的Pro架构的客户仍可以通过New Relic基础架构免费监控基础架构性能。
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# 在云基础架构上删除Adobe Commerce的Blackfire访问权限

2020年4月11日，Adobe Commerce on cloud infrastructure Pro计划架构或Adobe Commerce on cloud infrastructure入门计划架构订阅将不再包括免费访问Blackfire性能监控。  您将无法再登录到您的Blackfire帐户。 在4月11日之后，可以直接通过Blackfire.io购买许可证，以继续使用Blackfire。 Adobe Commerce如果到2015年12月14日尚未直接从Blackfire购买许可证，则将停用其免费的Adobe提供Blackfire许可证。 除此之外，将禁用使用Profiler工具创建新报告的功能。 使用托管在云基础架构上的Pro架构的客户仍可以通过New Relic基础架构免费监控基础架构性能。

**如果要继续使用Blackfire**：

1. 您必须直接通过Blackfire购买许可证。
1. 然后使用以下内容设置Blackfire [步骤](https://blackfire.io/docs/integrations/paas/magentocloud).
1. 如果在安装过程中遇到任何困难，您可以 [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 以请求帮助。 有关特定于Blackfire的问题，请直接联系Blackfire支持： [support@blackfire.io](mailto:support@blackfire.io).

## 如果在运行部署时出错：

如果运行部署时出现与Blackfire相关的错误，请执行以下操作：

1. 从配置中删除Blackfire。 编辑 `.magento.app.yaml` 文件并从运行时部分删除Blackfire：

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. 在本地开发环境中完成该操作并将其推送到云。

仅 [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 如果在运行部署后看到以下错误：

*PHP警告： PHP启动：无法在未知的行0中加载动态库“blackfire.so”(已尝试：/usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so：无法打开共享对象文件：没有此类文件或目录)、/usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so：无法打开共享对象文件：没有此类文件或目录)*

此错误表示必须更新并停止Blackfire插件加载。

**如果您要使用New Relic基础架构**：

要了解如何访问New Relic基础架构，请参阅 [访问New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) 在我们的支持知识库中。
