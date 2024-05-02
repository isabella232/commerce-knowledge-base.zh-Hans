---
title: 快速签出问题疑难解答
description: 本文介绍了在使用Quick Checkout for Adobe Commerce扩展时可能遇到的问题，并提供相应的解决方案来修复这些问题，以便您可以成功使用该扩展。
exl-id: 8ab46318-d62a-4b7e-bbe5-4c52cfeb9e36
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 快速签出问题疑难解答

本文介绍了在使用Quick Checkout for Adobe Commerce扩展时可能遇到的问题，并提供相应的解决方案来修复这些问题，以便您可以成功使用该扩展。

## 受影响的产品和版本

* 此 [快速签出](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/overview.html) 与Magento Open Source和Adobe Commerce兼容。 请参阅 [生命周期政策](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) 有关支持的版本的详细信息。

## Composer键不正确，对的最低稳定性为 `RC`

<u>原因</u>：

如果您看到以下错误消息，则可能是由于编写器键不正确：

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

<u>解决方案</u>：

验证您的编辑器键已链接到 _MAGENTOID_ 在Quick Checkout注册期间使用。

要查看已配置的编辑器键，请执行以下操作：

1. 查找的位置 `auth.json` 文件：

   ```bash
   composer config --global home
   ```

1. 查看 `auth.json` 文件：

   ```bash
   cat /path/to/auth.json
   ```

1. 请参阅 [哪些键与您的MagentoID关联](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

1. 将最小稳定性设置为 `RC` 在 `composer.json` 文件。

   ```json
   "minimum-stability": "RC"
   ```

## 内存不足，无法用于PHP

<u>原因</u>：

如果看到以下错误消息，表示您没有足够的内存来安装PHP：

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

<u>解决方案</u>：

[增加内存限制](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 环境上的PHP的 `php.ini`.

或者，也可以使用此命令指定内存限制： `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

例如：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## 使用新送货地址添加街道地址行

Quick Checkout扩展存在已知问题。

当您 [使用Bolt帐户登录](https://help.bolt.com/shoppers/guides/checkout/log-in/)，您可以添加新的送货地址，每个街道地址限制为4行。

如果新的送货地址包含4行以上，则不会存储这些行。

Adobe Commerce通常可以配置为支持最多20个街道地址行。

## 出现以下情况时出现意外行为 `Display Billing Address On` 设置为 `payment page`

Quick Checkout扩展存在已知问题。

如果您设置 `Display Billing Address On` 参数到 `payment page` 和 [使用Bolt帐户登录](https://help.bolt.com/shoppers/guides/checkout/log-in/) 当您检查 `My billing and shipping address are the same` 复选框，则显示单选按钮 `use existing card`. 由于帐单地址仅适用于新信用卡，因此在Bolt用户决定添加新信用卡选项之前，该地址将不可见。

请参阅 [结帐](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 主题以了解有关 `Display Billing Address On` 参数。
