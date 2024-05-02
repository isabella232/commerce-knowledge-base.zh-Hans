---
title: 解决加密密钥问题
description: 本文就如何解决加密密钥未随数据库转储一起移动到其他环境所导致的问题进行了讨论。
exl-id: 34410da0-1bd5-421e-9cd7-d3ee75ad8ed7
feature: Cache, Variables
role: Developer
source-git-commit: bee0263da487399ab07bf9158c4d60ab316d6ea1
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# 解决加密密钥问题

本文就如何解决加密密钥未随数据库转储一起移动到其他环境所导致的问题进行了讨论。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x

## 问题

导入后 [数据库转储](/help/how-to/general/create-database-dump-on-cloud.md) 从生产环境到暂存/集成环境，对于需要使用商家凭据的支付集成，保存的信用卡号显示错误和/或支付失败。

## 原因

用于加密敏感数据（如信用卡号和商户凭证）的加密密钥未存储在数据库中，因此在数据库转储导入/导出后不会传输到其他环境。

## 解决方案

您需要从源环境中复制加密密钥并将其添加到目标环境中。

要复制加密密钥，请执行以下操作：

1. SSH到作为数据库转储源的项目，如中所述 [SSH到环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) 在我们的开发人员文档中。
1. 打开 `app/etc/env.php` 在文本编辑器中。
1. 复制的值 `key` 对象 `crypt`.

```php
return array ('crypt' =>      array ('key' => '<your encryption key>', ),);
```

设置目标项目的键值：

1. 打开 [云控制台](https://console.adobecommerce.com) 并找到您的项目。
1. 设置值 [CRYPT\_KEY](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) （在我们的开发人员文档中）变量，如中所述 [配置项目](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html) 在我们的开发人员文档中。 这将触发部署过程并 `CRYPT_KEY` 将在 `app/etc/env.php` 每个部署中的文件。

或者，您可以手动覆盖 `app/etc/env.php` 文件：

1. SSH连接到目标环境。
1. 打开 `app/etc/env.php` 在文本编辑器中。
1. 将复制的数据粘贴为 `key` 值 `crypt`.
1. 保存已编辑的 `env.php`.
1. 通过运行清理目标环境中的缓存 `bin/magento cache:clean` 或在Commerce管理员中的 **系统** > **工具** > **缓存管理**.
