---
title: 安装失败；无法创建install.log
description: 本文修复了由于安装向导在安装期间未创建“install.log”而导致安装失败的问题。
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 安装失败；无法创建install.log

本文修复了由于安装向导未创建 `install.log` 安装期间。

## 问题

同时运行Adobe Commerce进程可能会导致创建安装日志时出现问题。 （例如，将两个不同的安装放在不同的选项卡页面中。）

## 原因

Installation-fails-cannot-create-install.log检查您的设置 `open_basedir` 在 `php.ini`. 安装向导使用 [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP调用以获取临时目录的值。 如果 [open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir) 设置为拒绝连接到指定的目录 `sys_get_temp_dir`，则安装失败。
检查您的设置 `open_basedir` 在 `php.ini`. 安装向导使用 [sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP调用以获取临时目录的值。 如果 [open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir) 设置为拒绝连接到指定的目录 `sys_get_temp_dir`，则安装失败。


## 解决方案

要解决此问题，请更改值 `open_basedir` 并重新启动web服务器。

如果不确定如何更改此值，请执行以下步骤：

1. 如果您尚未这样做，请创建 [phpinfo.php](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo).
1. 在浏览器的地址或位置字段中输入以下URL： `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. 查找位置 `php.ini`.     `php.ini` 通常指定为 **已加载的配置文件** 在显示的结果中。
1. 作为具有超级用户权限的用户，打开 `php.ini` 在文本编辑器中。
1. 找到以下项的值： `open_basedir` 然后改变它。
1. 将更改保存到 `php.ini`.
1. 重新启动Web服务器。
