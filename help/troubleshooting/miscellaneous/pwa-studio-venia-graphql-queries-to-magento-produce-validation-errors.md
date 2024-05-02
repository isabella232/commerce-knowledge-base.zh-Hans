---
title: 'PWA Studio： Venia GraphQL对Adobe Commerce的查询产生验证错误'
description: 本文就如何解决Venia storefront GraphQL查询到Adobe Commerce实例时产生验证错误的问题提供了建议。
exl-id: ba268945-2a10-4af5-8089-cde21f0687bd
feature: GraphQL
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# PWA Studio： Venia GraphQL对Adobe Commerce的查询产生验证错误

本文就如何解决Venia storefront GraphQL查询到Adobe Commerce实例时产生验证错误的问题提供了建议。

## 受影响的产品和版本

* Adobe Commerce内部部署2.2.x、2.3.x
* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce的PWA Studio项目

## 问题

对Adobe Commerce内部部署或Adobe Commerce云基础架构的Venia GraphQL查询会产生验证错误。

## 原因

导致此问题的原因之一可能是Venia及其GraphQL查询与连接的Adobe Commerce实例的架构不同步。

## 解决方案

要测试查询是否为最新版本，请在项目根目录中运行以下命令：

```bash
yarn run validate-queries
```

这将显示兼容性报告。 如果存在不兼容问题，则需要升级PWA Studio或Adobe Commerce实例。 查看 [Adobe Commerce兼容性矩阵](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/version-compatibility/) 查看您所需的确切版本。

有关如何升级的说明，请参阅以下文档：

* 对于PWA Studio升级，请搜索的“从以前的版本升级”部分 [PWA发行说明](https://github.com/magento/pwa-studio/releases/) 适用于您需要升级到的版本。
* [在云基础架构版本上升级Adobe Commerce](https://devdocs.magento.com/cloud/project/project-upgrade.html) 在我们的开发人员文档中
* [升级Adobe Commerce内部部署（使用“composer create-project”或archive安装）](https://devdocs.magento.com/guides/v2.3/comp-mgr/cli/cli-upgrade.html) 在我们的开发人员文档中
* [升级Adobe Commerce内部部署(通过克隆Adobe Commerce repo安装)](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/dev_update-magento.html) 在我们的开发人员文档中

## 相关阅读

* [PWA Studio：Webpack在开始编译前挂起](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md) 在我们的支持知识库中
* [PWA Studio：运行开发人员模式时出现验证错误](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md) 在我们的支持知识库中
* [PWA Studio：浏览器显示“无法代理到”错误](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md) 在我们的支持知识库中
* [配置NPM以便能够使用PWA Studio](/help/how-to/general/configure-npm-to-be-able-to-use-pwa-studio.md) 在我们的支持知识库中
* [Adobe Commerce文档PWA](https://magento.github.io/pwa-studio/)
