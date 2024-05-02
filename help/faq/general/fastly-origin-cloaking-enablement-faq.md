---
title: '"[!DNL Fastly] origin coloaking启用常见问题解答”'
description: 此常见问题解答讨论了以下常见问题 [!DNL Fastly] Adobe Commerce中的源遮盖功能（已于2021年完全实施）。
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 348a1f6e455aff9ad7c562ea20c95f27c9ee0b86
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# [!DNL Fastly] 源隐匿启用常见问题解答

此常见问题解答讨论了以下常见问题 [!DNL Fastly] Adobe Commerce中的源遮盖功能（已于2021年完全实施）。

## 什么是 [!DNL Fastly] 原产地遮蔽？

源遮盖是一项安全功能，允许云基础架构上的Adobe Commerce阻止任何 [!DNL non-Fastly] 流量(为了防止DDoS攻击，流向云基础架构（来源）)。

## 隐瞒原产地有什么好处？

源遮盖旨在防止流量绕过 [!DNL Fastly Web Application Firewall] (WAF)并通过严格定义的 **[!DNL Fastly]** > **负载平衡器** > **实例**. 通过此实施，所有流量均可保证通过 [!DNL Fastly] WAF以及内置于负载平衡器中的内部WAF。

## 为什么这种起源掩盖会发生？

这项功能最初是为了在云基础架构上让Adobe Commerce受益而创建的。

## 我是否需要请求为项目启用源遮蔽？

不适用。 此功能应该已在所有云项目上实施，并且自2021年以来配置的任何项目默认情况下都将启用此功能。 但是，您可以请求通过以下方式为项目禁用源遮蔽 [提交支持请求](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 来源遮蔽是否会更改传出IP地址？

不，它没有。

## 源遮盖是否会影响REST API？

[!DNL Fastly] 不会缓存API调用，因此客户端应该不会受到此更改的影响。 源位置遮盖只会阻止直接转到源位置的请求，例如：

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

在本例中，如果客户端将URL更改为，则他们仍可以点击API ``mywebsite.com``：

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## 此更改是否会影响部署和停机时间？

否，此更改将会 **NOT** 会影响部署和停机时间。

## 如果项目具有多个暂存环境，原始遮盖是否会应用于所有暂存环境？

可以，如果项目有多个暂存环境，则更改将应用于所有暂存环境。
