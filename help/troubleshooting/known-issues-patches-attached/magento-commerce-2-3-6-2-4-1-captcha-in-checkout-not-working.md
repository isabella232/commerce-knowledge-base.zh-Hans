---
title: Adobe Commerce 2.3.6、2.4.1签出的验证码不起作用
description: 本文提供了一个修补程序，用于解决在Adobe Commerce中使用Paypal Express、Payflow Pro或CyberSource等第三方支付提供商时，用于结账的CAPTCHA功能在“下单”页面上无法按预期工作的问题。
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Adobe Commerce 2.3.6、2.4.1签出的验证码不起作用

本文提供了一个修补程序，用于解决在Adobe Commerce中使用Paypal Express、Payflow Pro或CyberSource等第三方支付提供商时，用于结账的CAPTCHA功能在“下单”页面上无法按预期工作的问题。

我们的开发人员文档提到了此已知问题：

<u>适用于Adobe Commerce 2.3.6的</u>：

* [Adobe Commerce 2.3.6发行说明：已知问题](https://devdocs.magento.com/guides/v2.3/release-notes/commerce-2-3-6.html#known-issues)
* [Magento Open Source2.3.6发行说明：已知问题](https://devdocs.magento.com/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>适用于Adobe Commerce 2.4.1的</u>：

* [Adobe Commerce 2.4.1发行说明：已知问题](https://devdocs.magento.com/guides/v2.4/release-notes/commerce-2-4-1.html#known-issues)
* [Magento Open Source2.4.1发行说明：已知问题](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-1.html#known-issues)

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.3.6和2.4.1
* Magento Open Source2.3.6和2.4.1

## 问题

<u>重现问题的步骤</u>

1. 在Commerce中至少设置以下一种支付方式：Paypal Express、Payflow Pro或CyberSource。
1. 转到 **管理员>商店>配置>客户>客户配置>验证码** .
   * 设置 **在店面启用验证码** = *是* .
   * 在中选择 **Forms** ： *结帐/下单* ， *登录* 、和 *忘记密码* .
   * 设置 **显示模式** = *尝试登录的次数之后* (以使 **失败的登录尝试次数** 设置)。
   * 设置 **失败的登录尝试次数** = *0* （使验证码始终有效）。
1. 在前端，将产品添加到购物车并尝试结帐。
1. 在支付信息页面上，输入captcha并尝试使用Paypal Express、Payflow Pro或CyberSource进行结账。

<u>预期结果：</u>

验证码功能按预期运行。

<u>实际结果：</u>

将显示以下错误消息： *请提供验证码并重试。*

## 解决方案

根据您在Adobe Commerce本地/Adobe Commerce上部署的是cloud infrastructure/Magento Open Source 2.3.6还是2.4.1，应用以下修补程序之一。

## 补丁程序

这些修补程序已附加到本文中，可在以下两个站点中下载： `.composer` 和 `.git` 格式。

要下载补丁程序，请向下滚动到文章的结尾并单击文件名，或单击以下链接之一：

<u>适用于Adobe Commerce on-premise/Adobe Commerce on cloud infrastructure/Magento Open Source 2.3.6</u> ：

* [Composer修补程序MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git修补程序MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>适用于Adobe Commerce on-premise/Adobe Commerce on cloud infrastructure/Magento Open Source 2.4.1</u> ：

* [Composer修补程序MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Git修补程序MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

这些修补程序与任何其他Adobe Commerce或Magento Open Source版本不兼容。

## 如何应用修补程序

<u>Composer修补程序</u>

请参阅 [如何应用Adobe提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 支持知识库中的编辑器修补程序说明。

<u>Git修补程序</u>

请参阅开发人员文档 [应用修补程序：自定义修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) 有关Adobe Commerce/Magento Open Source的Git修补程序说明，
