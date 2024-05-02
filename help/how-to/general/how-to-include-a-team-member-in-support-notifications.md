---
title: 如何在支持通知中包含团队成员
description: 本文解释了如何在支持通知中包含团队成员。
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 1c568d75534bbfe322d9f980b40c5dd64fc5b7a2
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 如何在支持通知中包含团队成员

本文介绍了如何让团队成员通过电子邮件通知自动接收支持更新。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，全部 [支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## 原因

* 尚未将团队成员添加到 [!DNL cloud project] 拥有必要的权限。
* 团队成员没有支持帐户。

## 解决方案

1. 转到 **[!DNL Cloud Project URL]** (示例： `https://us-3.magento.cloud/projects/xxxxxx/edit`)。
1. 验证团队成员是否已添加到项目中，并且是 [!DNL Super User].

如果它们不需要 [!DNL cloud project] 访问，提交 [向Adobe Commerce支持中心提出支持请求](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 自动抄送：在所有票证上抄送，并提供其 **[!DNL MAGE ID]** （如果可用）。

如果它们尚未添加到项目中，您将需要添加它们作为 [!DNL Super User] 和grant [!DNL Shared Access]：

* [管理用户访问权限](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) 在我们的用户指南中。
* [无法将用户添加到Adobe Commerce云项目](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html) 在我们的Commerce知识库中。
* [Adobe Commerce帮助中心用户指南：共享访问](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access) 在我们的Commerce知识库中。

如果它们已添加到 [!DNL cloud project]，但没有 [!DNL Super User role]，更新其 [!DNL role] 相应地，在 [管理用户访问权限](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html).

## 相关阅读

[以前的团队成员会收到Adobe Commerce Cloud通知电子邮件](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
