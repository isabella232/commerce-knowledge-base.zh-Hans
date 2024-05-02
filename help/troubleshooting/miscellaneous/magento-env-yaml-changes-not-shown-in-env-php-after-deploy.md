---
title: 部署后.magento.env.yaml更改未显示在env.php中
description: 本文为部署后.magento.env.yaml文件中的更改未反映在app/etc/env.php中的问题提供了解决方案。
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 部署后.magento.env.yaml更改未显示在env.php中

>[!NOTE]
>
>如果您遇到此问题，请升级到ece-tools 2002.1.5进行修复。 2002.1.5具有在每次部署时重置opcache的功能，因此无需更改设置 `opcache.enable_cli=1`. 如果您不想升级，则必须按照解决方案中所述执行解决步骤。

本文为以下问题提供了解决方案： `.magento.env.yaml` 文件未反映在 `app/etc/env.php` 部署后。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce(所有 [支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf))。

## 问题

在中进行的更改 `.magento.env.yaml` 文件不会影响 `app/etc/env.php` 已生成。

<u>重现问题的步骤：</u>

更改中的任意值 `.magento.env.yaml` 和推送到服务器，它应该在其中定义当前签出环境的配置（和部署设置）。 有关步骤，请参阅 [“环境变量”>“部署变量”](https://devdocs.magento.com/cloud/env/variables-deploy.html) 在我们的开发人员文档中。

<u>预期结果：</u>

在中进行的更改 `.magento.env.yaml` 文件影响 `app/etc/env.php` 已生成。

<u>实际结果：</u>

这些更改对 `app/etc/env.php` 部署后的变量。

## 原因

问题可能是由于 `opcache.enable_cli` 中的参数 `php.ini` 文件。

## 解决方案

1. 检查系统是否根据 [Adobe Commerce性能最佳实践>软件推荐](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html).
1. 检查 `opcache.enable_cli` 中的指令 `php.ini` 设置为 `0` 通过执行： `php -i | grep opcache.enable_cli`
1. 如果输出与 `opcache.enable_cli=1` ，编辑 `php.ini` 在项目根目录中的文件并更改 `opcache.enable_cli=1` 到 `opcache.enable_cli=0`
1. 重新部署项目。

## 相关阅读

* [Cloud for Adobe Commerce >生成和部署](https://devdocs.magento.com/cloud/project/magento-env-yaml.html).
