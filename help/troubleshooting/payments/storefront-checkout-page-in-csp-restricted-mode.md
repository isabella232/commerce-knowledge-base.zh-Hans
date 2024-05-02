---
title: 中的storefront结帐页面疑难解答 [!UICONTROL CSP] 受限模式
description: 本文介绍了在CSP限制模式下查看签出页面时可能遇到的错误，并提供修复这些错误的解决方案。
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# 中的storefront结帐页面疑难解答 [!UICONTROL CSP] 受限模式

本文介绍了在中查看签出页面时，有关Adobe Commerce 2.4.7问题的解释和修复 **[!UICONTROL CSP restricted mode]**，带有&quot;*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“浏览器控制台日志中显示错误消息。

## 受影响的产品和版本

云基础架构上的Adobe Commerce、Adobe Commerce内部部署和Magento Open Source：

* 2.4.7
* 2.4.6像素
* 2.4.5-pX
* 2.4.4像素

## 问题 — Storefront结帐页面已损坏或无法加载

此 **店面结帐** 页面已损坏或无法加载，使用&quot;*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“浏览器控制台日志中显示错误消息。

<u>重现问题的步骤</u>：

1. 去店面。
1. 将产品添加到购物车并继续结帐。

<u>预期结果</u>：

签出页面会正常完全加载。

<u>实际结果</u>：

签出页面为空或缺少组件。 以下各项 [!DNL JS] 错误显示在浏览器控制台日志中：“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中， **[!UICONTROL CSP]** 在中配置 `restrict-mode`，默认情况下，适用于店面和管理区域以及中的付款页面 `report-only` 模式。
对应的 **[!UICONTROL CSP]** 标题不包含 `unsafe-inline` 中的关键词 `script-src` 付款页的指令。 此外，仅限 [!DNL whitelisted] 允许使用内联脚本。

### 解决方案

由于某些脚本被阻止，用户可能会看到浏览器错误 **[!UICONTROL CSP]**：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>要解决此问题，您必须</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 阻止的脚本使用 `SecureHtmlRenderer` 类。
1. 使用 `CSPNonceProvider` 类以允许执行脚本。
Adobe Commerce和Magento Open Source2.4.7及更高版本包括 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 提供商，以便于生成唯一的 [!DNL nonce] 每个请求的字符串。 这些 [!DNL nonce] 字符串随后将附加到 [!UICONTROL CSP] 标题。

   使用 `generateNonce` 函数位于 `Magento\Csp\Helper\CspNonceProvider` 以获取 [!DNL nonce] 字符串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [添加 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 至模块的 `csp_whitelist.xml` 文件。

## 问题 — 付款方法缺失或无法正常工作

付款方式缺失或无法用于 **店面结帐** 页面，带有&quot;*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“浏览器控制台日志中显示错误消息。

<u>重现问题的步骤</u>：

1. 去店面。
2. 将产品添加到购物车并继续结帐。
3. 选择付款方式。

<u>预期结果</u>：

您可以选择付款方式并继续成功下单。

<u>实际结果</u>：

付款方式缺失或无法正常工作。 以下各项 [!DNL JS] 错误显示在浏览器控制台日志中：“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中， **[!UICONTROL CSP]** 在中配置 `restrict-mode`，默认情况下，适用于店面和管理区域以及中的付款页面 `report-only` 模式。
对应的 **[!UICONTROL CSP]** 标题不包含 `unsafe-inline` 中的关键词 `script-src` 付款页的指令。 此外，仅限 [!DNL whitelisted] 允许使用内联脚本。

### 解决方案

由于某些脚本被阻止，用户可能会看到浏览器错误 **[!UICONTROL CSP]**：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>要解决此问题，您必须</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 阻止的脚本使用 `SecureHtmlRenderer` 类。
1. 使用 `CSPNonceProvider` 类以允许执行脚本。
Adobe Commerce和Magento Open Source2.4.7及更高版本包括 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 提供商，以便于生成唯一的 [!DNL nonce] 每个请求的字符串。 这些 [!DNL nonce] 字符串随后将附加到 [!UICONTROL CSP] 标题。

   使用 `generateNonce` 函数位于 `Magento\Csp\Helper\CspNonceProvider` 以获取 [!DNL nonce] 字符串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [添加 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 至模块的 `csp_whitelist.xml` 文件。

## 问题 — 客户无法下订单

客户无法使用&#39;&#39;下达订单&#x200B;*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“浏览器控制台日志中显示错误消息。

<u>重现问题的步骤</u>：

1. 去店面。
2. 将产品添加到购物车并继续结帐。
3. 选择付款方式。
4. 单击 **下单**.

<u>预期结果</u>：

您可以成功下订单。

<u>实际结果</u>：

你无法下订单。 以下各项 [!DNL JS] 错误显示在浏览器控制台日志中：“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中， **[!UICONTROL CSP]** 在中配置 `restrict-mode`，默认情况下，适用于店面和管理区域以及中的付款页面 `report-only` 模式。
对应的 **[!UICONTROL CSP]** 标题不包含 `unsafe-inline` 中的关键词 `script-src` 付款页的指令。 此外，仅限 [!DNL whitelisted] 允许使用内联脚本。

### 解决方案

由于某些脚本被阻止，用户可能会看到浏览器错误 **[!UICONTROL CSP]**：

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>要解决此问题，您必须</u>：

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) 阻止的脚本使用 `SecureHtmlRenderer` 类。
1. 使用 `CSPNonceProvider` 类以允许执行脚本。
Adobe Commerce和Magento Open Source2.4.7及更高版本包括 **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] 提供商，以便于生成唯一的 [!DNL nonce] 每个请求的字符串。 这些 [!DNL nonce] 字符串随后将附加到 [!UICONTROL CSP] 标题。

   使用 `generateNonce` 函数位于 `Magento\Csp\Helper\CspNonceProvider` 以获取 [!DNL nonce] 字符串。

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [添加 [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) 至模块的 `csp_whitelist.xml` 文件。
