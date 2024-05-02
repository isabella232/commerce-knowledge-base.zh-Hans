---
title: 在2.4.6升级之前减少过期的“oauth_tokens”
description: 当您在“oauth_token”表中看到大量“oauth_tokens”时，可能会导致升级到版本2.4.6时出现长时间延迟，本文提供了这个问题的解决方案。建议使用CleanExpiredTokens.php减少“oauth_token”表。
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# 减少过期时间 `oauth_tokens` 在2.4.6升级之前

本文针对您看到大量此类数据的问题，提供了解决方案： `oauth_tokens` 在您的 `oauth_token` 表格的详细信息，这会造成升级到版本2.4.6时出现长时间延迟。建议减少 `oauth_token` 表使用 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 删除过期令牌的作业。

## 受影响的产品和版本

* Adobe Commerce 2.4.0 - 2.4.6，所有部署方法

## 问题

如果存在大量 `oauth_tokens` 在您的 `oauth_token` 表，这会造成升级到版本2.4.6时出现长时间延迟。

升级过程包括加密这些令牌以实现额外的安全层，并且一次仅完成100条记录。 如果令牌数量很大，这可能需要几个小时。

减少大量的 `oauth_tokens` 在您的 `oauth_token` 表可以防止在升级到版本2.4.6时出现长时间延迟。

## 解决方案

在开始升级之前，请首先确保 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 作业正在运行。 它缩小了 `oauth_token` 通过删除过期日期生成的表 `oauth_tokens` 令牌，默认情况下应该已经启用和。

手动触发 [`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron] 作业，运行：
```bin/magento cron:run --group=default```

## 相关阅读

* [服务> [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html) (在Commerce配置参考指南中)。
* [Authentication指南](https://developer.adobe.com/developer-console/docs/guides/authentication/) 在Adobe Developer指南中。
