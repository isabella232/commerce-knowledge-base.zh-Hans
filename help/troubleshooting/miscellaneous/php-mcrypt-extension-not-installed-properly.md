---
title: PHP mcrypt扩展未正确安装
description: PHP mcrypt扩展未正确安装
exl-id: 1010349e-6631-4a05-8883-5cc903d67534
feature: Extensions, Install
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# PHP mcrypt扩展未正确安装

>[!WARNING]
>
>请注意：加密库功能为 [已从PHP 7.1弃用并从PHP 7.2中删除](https://www.php.net/manual/en/intro.mcrypt.php).

## 详细信息

错误可能包括：

```php
exception 'Exception' with message 'PHP Warning: [PHP](https://glossary.magento.com/php) Startup: Unable to load dynamic [library](https://glossary.magento.com/library) '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory
```

```php
Installing data fixtures:
/usr/bin/php -f '/Users/username/www/magento/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/Users/username/www/magento' 2>&1
[ERROR] [exception](https://glossary.magento.com/exception) 'Exception' with message '
Fatal error: Uncaught exception 'Exception' with message 'Module 'Magento_Core' depends on 'mcrypt' PHP [extension](https://glossary.magento.com/extension) that is not loaded.'
```

```php
======================================================================
   The application has thrown an exception!
======================================================================
 Magento\Framework\Exception
 Command returned non-zero exit code:
`/usr/bin/php5 -f '/var/www/magento2/dev/shell/run_data_fixtures.php' -- --bootstrap='MAGE_DIRS[base][path]=/var/www/magento2' 2>&1`
```

## 描述

特别是在包含独立于操作系统的Linux/Apache/MySQL/PHP (LAMP)“栈栈”的开发人员系统中，可能根本未安装mcrypt，或者它安装在LAMP栈栈的路径中，而不是操作系统的路径中。

因此，Adobe Commerce安装程序无法找到该扩展，并且安装失败。

## 建议

确定是否通过以下任一方式加载mcrypt扩展：

* 设置 [phpinfo.php](http://kb.mediatemple.net/questions/764/How+can+I+create+a+phpinfo.php+page%3F#gs) 文件，并在Web浏览器中检查输出。
* 运行以下命令：    `$ php -r "phpinfo();" | grep mcrypt`

如果mcrypt *非* 已安装，将显示与以下内容类似的消息：

```php
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/mcrypt.so' - /usr/lib/php5/20121212/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

在某些情况下，您可能需要从安装Adobe Commerce软件 [命令行](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html) 并指定已安装mcrypt的LAMP栈栈的完整路径。
