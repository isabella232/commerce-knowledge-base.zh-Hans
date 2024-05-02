---
title: 'PWA Studio：Webpack在开始编译之前挂起'
description: 本文介绍了当Javascript [Webpack](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)在Progressive Web App Studio(PWA Studio)中开始编译之前挂起很长一段时间时的建议解决方案。
exl-id: 692eeafa-9289-4d66-9f2f-1e0fe36e681d
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# PWA Studio：Webpack在开始编译前挂起

本文讨论当javascript运行时，为提供建议的解决方案 [网络包](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack) 挂起PWA Studio后，即开始在Progressive Web App Studio中进行编译。

## 受影响的产品和版本

* PWA Studio

## 问题

[查看pwa-buildpack的最新版本](https://github.com/magento/pwa-studio/tree/master/packages/pwa-buildpack)，和

```yaml
pwa-buildpack
```

版本号将位于 `package.json` 文件名列表。 如果您拥有旧版本的

```yaml
pwa-buildpack
```

项目时，webpack可能会长时间挂起，然后才能开始编译。

<u>重现问题的步骤</u>：

<u>先决条件</u>：使用本地Adobe Commerce实例设置PWA Studio店面（例如Venia）并运行

```yaml
build
```

或

```yaml
watch
```

命令。

<u>预期结果</u>：

* 如果使用    ```yaml    build    ```    命令，它通常会为Venia生成生成构件。
* 如果使用    ```yaml    watch    ```    命令，正常启动Venia店面。

<u>实际结果</u>：

您的

```yaml
build
```

或

```yaml
watch
```

命令似乎已停止并且不会完成，也不会显示任何错误。

## 解决方案

使用以下命令更新项目：

```yaml
yarn upgrade
```

使用以下命令确保您的系统上有openssl的当前版本：

```yaml
openssl version
```

版本应为1.0或更高版本（对于OSX High Sierra，则为LibreSSL 2）。

您可以通过以下方式安装较高版本的OpenSSL： [Homebrew](https://brew.sh/) 在OSX上， [巧克力](https://chocolatey.org/) 在Windows上或Linux分发的包管理器上。

## 相关阅读

* [Javascript Webpack：概念](https://webpack.js.org/concepts/)
* [Venia店面设置](https://magento.github.io/pwa-studio/venia-pwa-concept/setup/)
* [PWA构建包](https://magento.github.io/pwa-studio/pwa-buildpack/)
* [buildpack命令行界面](https://magento.github.io/pwa-studio/pwa-buildpack/reference/buildpack-cli/)
* [工具和库：构建包](https://magento.github.io/pwa-studio/technologies/tools-libraries/#webpack)
