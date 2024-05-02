---
title: 当字段变灰时，如何更改magento.com帐户上的电子邮件地址
description: 本文讨论当字段呈灰色时，如何更改[Magento.com](https://account.magento.com)帐户上的电子邮件地址。
exl-id: cd527203-345c-4318-8ca8-0063109b5f79
feature: Communications
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 当字段呈灰色时，如何更改magento.com帐户上的电子邮件地址？

本文说明如何更改您网站上的 [Magento.com](https://account.magento.com) 当字段呈灰色时显示的帐户。

## 受影响的产品和版本

* 所有Adobe Commerce版本和基础设施类型

## 原因

您的电子邮件地址 [Magento.com](https://account.magento.com) 帐户链接到Adobe帐户，位于 <https://account.adobe.com> 并且必须在该处进行更新。

## 更改电子邮件地址的步骤

### 案例一：

更改拥有自己帐户的用户的电子邮件地址 <https://account.adobe.com>

<u>解决方案</u>

1. 向Grp-magento-HelpCenterLoginIssues@adobe.com发送电子邮件，说明以下内容：

   * 要更新的现有电子邮件地址
   * 新电子邮件地址
   * 新帐户的图像ID（如果可用）

1. 请求团队合并两个帐户，以更新现有帐户上的电子邮件地址。

### 案例二：

更改当前没有自己帐户的用户电子邮件地址 <https://account.adobe.com>

<u>解决方案</u>

如果您有权访问的 [当前所有者电子邮件]，按以下方式重置当前所有者电子邮件的密码 [重置或更改您的Adobe密码](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html) 《Creative Cloud用户指南》中的指南。

1. 找到发送到当前所有者的邮箱的密码重置链接，并附上相关说明。
1. 设置新密码，并将电子邮件更改为 [新建所有者电子邮件].
1. 导航至 [IMS帐户](https://account.adobe.com/) 以使用新电子邮件登录，并更改密码。
1. 更改电子邮件地址和密码后，导航到 [Magento.com](https://account.magento.com) 以使用 [新建所有者电子邮件].

但是，如果您无权访问发送给 [当前所有者电子邮件]，请按照以下步骤操作：

1. 从设置电子邮件转发 [当前所有者电子邮件] 使用您公司的邮件服务器配置发送新电子邮件。
1. 现在，请继续执行上述步骤。

## 相关阅读

[重置忘记的密码](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html) 《Creative Cloud用户指南》中的。
