---
title: 无法将*contact*另存为URL键
description: 当您无法将*contact*另存为产品或CMS页面的URL键（例如“/contact”）时，本文提供了此问题的解决方法。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。
exl-id: eb340813-aba5-43a4-af5d-8fb64c93e021
feature: CMS, Marketing Tools, Storefront
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 无法保存 *联系人* 作为URL键

当您无法保存时，本文会提供该问题的解决方法 *联系人* 作为产品或CMS页面的URL键（例如“/contact”）。

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.x

## 问题

无法使用术语保存产品或CMS页面 *联系人* 作为URL键。 当您尝试保存URL键时，您会收到一个错误，指示URL键是重复的URL。

<u>重现问题的步骤</u>：

创建CMS页面，使用 *联系人* 作为URL键。

<u>预期结果</u>：

页面保存方式 *联系人* 作为URL键。

<u>实际结果</u>：

无法保存该页面。 您收到以下错误： *在URL键字段中指定的值将生成已存在的URL。*

## 原因

*联系人* 是中定义的保留字 `vendor/magento/module-contact/view/frontend/layout/contact_index_index.xml`.

```xml
<router id="standard">
      <route id="contact" frontName="contact">
          <module name="Magento_Contact" />
      </route>
  </router>
```

## 解决方案

不能使用术语 *联系人* 但是，作为您的URL密钥，您可以使用术语 *联系人* 与其他字母或数字组合(例如， *联系人1* 和 *联系人2*)。 虽然这个词不一定是 *联系人+\&lt;another number=&quot;&quot; or=&quot;&quot; letter=&quot;&quot;>*，只要长度不超过255个字符，术语可以是任何字符串。

执行以下步骤：

1. 登录到Commerce Admin。
1. 转到 **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL URL Rewrites]**.
1. 单击 **[!UICONTROL Add URL Rewrite]**.
1. 选择 *[!UICONTROL Custom]* 在 [!UICONTROL Create URL Rewrite] 下拉菜单。
   1. 在 [!UICONTROL Request Path]，键入“contact”。 请注意 [!UICONTROL Request Path] 是用户在浏览器中输入的内容，并且 [!UICONTROL Target Path] 是应该重定向到的位置。
   1. 在 [!UICONTROL Target Path]，键入新的URL键（例如，“contact1”）。
   1. 选择 *[!UICONTROL No]* 在 [!UICONTROL Redirect] 下拉菜单。

## 相关阅读

* [URL重写](https://docs.magento.com/user-guide/marketing/url-rewrite.html) 在我们的用户指南中。
* [seo最佳实践](https://docs.magento.com/user-guide/marketing/seo-best-practices.html) 在我们的用户指南中。
