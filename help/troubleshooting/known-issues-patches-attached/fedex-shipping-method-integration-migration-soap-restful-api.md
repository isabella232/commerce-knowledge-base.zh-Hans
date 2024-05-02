---
title: ’[!DNL FedEx] 发运方法集成从SOAP迁移到RESTful API
promoted: true
description: 应用修补程序以处理 [!DNL FedEx] 适用于Adobe Commerce 2.4.4-p4 - 2.4.6-pX的配送方法集成从SOAP迁移到RESTful API。
feature: Shipping/Delivery
role: Developer
exl-id: 7e11a171-6924-41d0-a5c7-7b794d0da84c
source-git-commit: 7c468583883789a6bc6e41d1a787a356ea3205c4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# [!DNL FedEx] 将集成方法从SOAP迁移到RESTful API

本文提供了一个修补程序，用于解决的问题 [!DNL FedEx] 适用于Adobe Commerce 2.4.4-p4 - 2.4.6-pX的配送方法集成从SOAP迁移到RESTful API。

[!DNL FedEx Web Services] 跟踪、地址验证和验证邮政编码Web服务定义语言(WSDLS)将于2024年5月15日停用。 基于SOAP [!DNL FedEx Web Services] 处于开发密封状态，已替换为 [!DNL FedEx] RESTFUL API。 要了解更多信息，请参阅 [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

此更改将影响我们当前的 [!DNL FedEx] Adobe Commerce中的配送方法集成实施，需要我们修复当前的实施，并从已弃用的SOAP API迁移到最新版本 [!DNL FedEx] RESTFUL API。

从2024年5月15日开始，Adobe Commerce客户将无法使用我们当前的 [!DNL FedEx] 配送方式集成，因此Adobe将发布此修补程序，以便让Adobe Commerce 2.4.4及更高版本客户使用最新版本 [!DNL FedEx] RESTFUL API，而不是已弃用的SOAP API。


## 受影响的产品和版本

云基础架构和内部部署以及Magento Open Source上的Adobe Commerce：

* 2.4.4-p4
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6像素

## 原因

此 [!DNL FedEx] 已弃用基于SOAP的API，并改为使用RESTful API。 请参阅 [[!DNL FedEx Web Services]](https://www.fedex.com/en-us/developer/web-services.html).

## 解决方案

根据您的Adobe Commerce/Magento Open Source版本，使用以下附加的修补程序：

要解决2.4.4+、2.4.5+和2.4.6+版本中的问题，必须将相应的修补程序应用于下面的Adobe Commerce/Magento Open Source版本。

## Patch

根据您的Adobe Commerce/Magento Open Source版本，使用以下附加的修补程序：

### 对于版本2.4.4-p4：

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)

### 对于版本2.4.5、2.4.5-pX：

* [FedexPatch-Composer-245p5-244p6develop.patch.zip](assets/FedexPatch-Composer-245p5-244p6develop.patch.zip)


### 对于版本2.4.6、2.4.6-pX：


* [FedexPatch-Composer-246p3develop.patch.zip](assets/FedexPatch-Composer-246p3develop.patch.zip)


## 如何应用修补程序

解压缩文件并查看 [如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) 在我们的支持知识库中获取说明。

## 如何判断是否已应用修补程序

考虑到无法轻松检查问题是否已修补，您可能需要检查修补程序是否已成功应用。 它使用(例如： *AC-9363*)作为要检查的修补程序。

<u>为此，您可以执行以下步骤</u>：

1. [安装 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. 运行以下命令：

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. 您应该会看到类似以下内容的输出，其中AC-9363返回 *已应用* 状态：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
