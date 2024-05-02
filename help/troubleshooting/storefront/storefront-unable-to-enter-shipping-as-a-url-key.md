---
title: 无法将“shipping”另存为URL键
description: 当您无法将“shipping”另存为产品或CMS页面的URL键（例如“/shipping”）时，本文提供了此问题的解决方法。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。
exl-id: df19b597-f615-4b19-82c1-59cc179fa720
feature: Marketing Tools, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# 无法将“shipping”另存为URL键

当您无法将“shipping”另存为产品或CMS页面的URL键（例如“/shipping”）时，本文提供了此问题的解决方法。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.x

## 问题

您无法在URL键中保存词为“shipping”的CMS页面。

<u>重现问题的步骤</u>：

创建一个URL键为“shipping”的CMS页面。

<u>预期结果</u>：

页面会在URL键中以“shipping”形式保存。

<u>实际结果</u>：

无法保存，并且出现以下错误： *在URL键字段中指定的值将生成已存在的URL。*

## 原因

送货是在中定义的保留字 `vendor/magento/module-shipping/etc/frontend/routes.xml`.

```xml
<router id="standard">
      <route id="shipping" frontName="shipping">
          <module name="Magento_Shipping" />
      </route>
  </router>
```

## 解决方案

您不能在URL密钥中使用术语“shipping”，但您可以将术语“shipping”与其他字母或数字（例如，“shipping1”和“shipping2”）结合使用。 尽管这个词不一定是“运送”+&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>  — 只要长度不超过255个字符，术语可以是任何字符串。

执行以下步骤：

1. 登录到Commerce管理员。
1. 转到 **营销** > SEO和搜索> **URL重写**.
1. 单击 **添加URL重写**.
1. 选择 *自定义* 创建URL重写下拉列表上的。
   1. 键入请求路径“shipping”。 注意：请求路径是用户在浏览器中输入的内容，目标路径是用户应重定向到的位置。
   1. 在目标路径中键入新的URL键（例如，“shipping1”）。
   1. 选择 **否** 在重定向下拉菜单中。

## 相关阅读

* [URL重写](https://docs.magento.com/user-guide/marketing/url-rewrite.html) 在我们的用户指南中。
* [seo最佳实践](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) 在我们的用户指南中。
