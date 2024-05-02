---
title: 未验证PayPal沙盒帐户
description: 本文解释了为什么无法验证您用于支付服务的PayPal沙盒帐户，从而阻止您完成沙盒载入。
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# 未验证PayPal沙盒帐户

本文解释了为什么无法验证您用于支付服务的PayPal沙盒帐户，从而阻止您完成沙盒载入。

## 受影响的产品和版本

* [支付服务](https://marketplace.magento.com/magento-payment-services.html) 现在与Adobe Commerce版本2.4.0到2.4.4兼容。

## 问题

我们的 [入门文档](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html) 指示您注册PayPal帐户，登录PayPal开发人员帐户，然后创建沙盒帐户。 如果您选择在新用户引导期间在PayPal新用户引导弹出窗口中创建新帐户，PayPal将无法验证您的沙盒帐户，并且您将无法完成新用户引导。

<u>重现问题的步骤</u>：

1. 您 [安装支付服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html) 和 [配置Commerce服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-commerce-services).
1. 您导航到 **支付服务** 在Admin和 [开始沙盒载入](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html).
1. 在出现的PayPal载入弹出窗口中，您创建一个新的企业帐户(而不是 [使用之前创建的PayPal沙盒帐户登录](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) 新用户引导期间。
1. 您已成功完成PayPal入门。
1. 您会在管理员中看到一则通知，表明您的沙盒支付正在等待处理，您必须通过PayPal确认您的电子邮件地址才能完成入门。

   您未收到确认电子邮件，因为PayPal无法验证您的电子邮件地址。

## 原因

如果您在PayPal帐户之前创建沙盒帐户，PayPal将无法验证您的沙盒帐户，并且您将无法完成沙盒载入（这意味着您无法接受付款或测试沙盒模式）。

## 解决方案

1. 使用在中创建的沙盒帐户 [PayPal开发人员](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) 门户。
1. 单击 [重置沙盒](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html#test-in-sandbox-environment) 并重新启动沙盒载入。
1. [联系支持人员](mailto:payment-services-support@adobe.com) 如果您无法缓解帐户问题，则可以继续载入并接受付款。
