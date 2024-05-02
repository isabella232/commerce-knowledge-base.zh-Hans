---
title: 'cURL错误60： SSL证书已过期'
description: '本文说明如何在收到cURL错误60后检查上次部署分支的时间：云基础架构上的Adobe Commerce上的主分支或集成分支中的SSL证书已过期。'
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: 6f631ca35b663c386bca9efe6e56db266502c0b1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# cURL错误60： SSL证书已过期

本文说明如何检查分支在收到 `cURL error 60`： [!DNL SSL certificate] 过期时间 [!DNL Master] 或 [!DNL Integration] 云基础架构上的Adobe Commerce上的分支。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce， [所有受支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 原因

此 [!DNL SSL certificates] 这些分支中的有效期限仅为30天，并且可能在30天以上没有重新部署。

该错误将类似于以下内容：

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

## 解决方案

检查上次部署分支的时间。 如果超过30天的阈值，则重新部署分支。

检查上次执行部署的时间的两种方法：

* [方法1：使用 [!DNL magento-cloud] CLI](#meth2).
* [方法2：打开 [!DNL Project URL]](#meth3).

如果部署成功完成， [!DNL SSL certificate] 将自动续订。

如果部署失败，您需要帮助来解决该问题， [提交支持服务单](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

### 方法1：使用 [!DNL magento-cloud] CLI {#meth2}

运行此命令： `magento-cloud activity:list`

### 方法2：打开 [!DNL Project URL] {#meth3}

例如，转到： `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`，并检查上次执行部署的时间。

## 相关阅读

在我们的开发人员文档中：

* [Cloud Manager API：SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [设置Fastly：设置SSL/TLS证书](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates)

在我们的支持知识库中：

* [自定义SSL证书过期信息](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html)
* [云基础架构上Adobe Commerce的SSL (TLS)证书](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html)
