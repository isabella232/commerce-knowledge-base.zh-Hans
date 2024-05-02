---
title: 无法访问最新的测试版
description: 本文为尝试使用Adobe Commerce的最新测试版代码时出现的问题提供了解决方案。 测试版代码仅适用于遵循[Adobe Commerce测试版计划](https://github.com/magento/magento2/wiki/Magento-Beta-Program)中所述过程的官方Adobe合作伙伴。
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# 无法访问最新的测试版

本文为尝试使用Adobe Commerce的最新测试版代码时出现的问题提供了解决方案。 测试版代码仅适用于已遵循中所述流程的官方Adobe合作伙伴。 [Adobe Commerce Beta计划](https://github.com/magento/magento2/wiki/Magento-Beta-Program).

## 问题

本文介绍了以下有关访问早期访问代码的问题：

* Adobe Commerce Beta版本在以下位置不可下载： **我的帐户** > **下载** 日期 [magento.com](https://account.magento.com/customer/account/login).
* 无法从下载早期访问的Adobe Commerce版本 [magento.com](https://account.magento.com/customer/account/login) 使用Composer。

## 原因

这些是导致问题的最常见原因：

* 您在错误的位置查找早期访问代码。
* 您使用了错误的MageID。
* 开发人员需要从正确的MageID获取访问密钥。
* 您的帐户不属于Beta计划。

## 解决方案

### 提前访问代码位置

在Beta版访问期间，仅可通过上的编辑器访问发行包 [repo.magento.com](https://repo.magento.com/). 在此期间，发行包在GitHub和Adobe Commerce门户上不可用，我们将在GA日期将它们发布到这些位置。 有关如何使用编辑器的更多详细信息，请单击 [此处](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html).

### 您需要使用的图像ID

您必须使用与合作伙伴帐户关联的主MageID。 Beta计划未链接到具有共享访问权限的任何联系人。 早期访问只能通过Composer或 [repo.magento.com](https://repo.magento.com/) 按与您的合作伙伴许可证关联的MageID查找。

#### 如何确定我的MageID是否是主要的ID

要确定您的MageID是否为主映像，请尝试以下操作：

1. 登录 [magento.com](https://account.magento.com/customer/account/login) 然后转到 **我的产品和服务** 选项卡。 在Partners子部分中，检查您是否看到有效的Partner许可证信息：
   * 如果您看到有效的Partner许可证信息，则表示您的MageID是主要的。 如果END DATE值是未来的日期，则合作伙伴许可证有效。
   * 如果您看不到有效的合作伙伴许可证信息，则您的MageID仅具有共享访问权限。 要了解谁是主要ID持有者，请转到 **与我共享** 请注意此处指定的SHARENAME。 单击 **切换帐户** 并选取您在SHARENAME中记下的值。 在欢迎页面上，您将看到主ID持有者的电子邮件。
1. 如果由于任何原因无法查找此信息 [magento.com](https://account.magento.com/customer/account/login)，请联系您的合作伙伴经理。
1. 如果以上都不管用，请 [联系支持人员](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed).

#### 开发人员没有正确的密钥访问权限

如果您是主要MageID所有者并需要向团队中的开发人员授予访问权限，请执行以下步骤：

1. 让主MageID所有者登录 [account.magento.com](https://account.magento.com/customer/account/login).
1. 选择 **市场** 选项卡，然后单击 **访问密钥**.
1. 选择 **创建新的访问密钥** 并为其命名。
1. 将密钥发送给开发人员。

### 不是抢先体验计划的一部分

我们的测试版访问计划仅向我们的解决方案和技术合作伙伴提供，以便他们能够评估我们的预生产代码。 要包含在测试版访问计划中，贵组织必须拥有一个信誉良好且已签署测试版保密协议的有效Adobe合作伙伴帐户 [此处](https://github.com/magento/magento2/wiki/Magento-Beta-Program). 如果您认为您符合这些标准并且无法访问测试版代码，请联系 [commercebeta@adobe.com](mailto:commercebeta@adobe.com).
