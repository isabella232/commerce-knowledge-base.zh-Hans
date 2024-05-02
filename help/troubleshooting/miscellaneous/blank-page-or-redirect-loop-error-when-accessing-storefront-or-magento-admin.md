---
title: 访问storefront或Commerce管理员时出现空白页面或重定向循环错误
description: 本文为访问Adobe Commerce店面或后端时出现空白页面或重定向循环的问题提供了解决方案。
exl-id: 65869de2-1939-481b-844b-69122345b407
feature: Admin Workspace, Cache, Storefront
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# 访问storefront或Commerce管理员时出现空白页面或重定向循环错误

本文为访问Adobe Commerce店面或后端时出现空白页面或重定向循环的问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本
* Adobe Commerce内部部署，所有版本
* Magento Open Source，所有版本

## 问题

<u>重现问题的步骤</u>

打开店面或管理页面。

<u>预期结果</u>

此时将打开页面。

<u>实际结果</u>

页面为空白或显示 *“此网页具有重定向循环”* 错误消息。

## 原因

导致该问题的最可能原因之一是，Adobe Commerce设置为从不安全URL重定向到安全URL，但为安全URL设置提供了不安全URL。

要解决此问题，您需要更正安全链接的值。

## 解决方案

要确保这是问题的原因，请执行以下步骤：

1. 查看 `web/secure/enable_upgrade_insecure` ， `web/secure/use_in_adminhtml` （如果您的Admin中存在空白/循环重定向问题）或 `web/secure/use_in_frontend` （如果您在商店前端遇到空白/循环重定向问题）值 `'core_config_data'` 数据库表。
   * 如果 `web/secure/enable_upgrade_insecure` 设置为“1”，然后设置Adobe Commerce以添加响应标头 `Content-Security-Policy: upgrade-insecure-requests`，从而指示浏览器使用HTTPS，将所有通过HTTP进行的查询重定向到HTTPS，以供管理员和店面使用。
   * 如果 `web/secure/use_in_adminhtml` 将设置为“1”，Adobe Commerce将为管理员页面的所有HTTP请求返回HTTPS重定向。
   * 如果 `web/secure/use_in_frontend` 将设置为“1”，Adobe Commerce会为商店头页的所有HTTP请求返回HTTPS重定向。
1. 查看 `web/secure/base_url` 和 `web/unsecure/base_url` 中的值 `'core_config_data'` 表格。 如果它们都从    `http`，则需要更正“安全”值。

修复问题：

1. 设置值，其开头为 `https` 对象 `web/secure/base_url.`
1. 对于要应用的更改，请通过运行以下命令清除配置缓存：

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```
