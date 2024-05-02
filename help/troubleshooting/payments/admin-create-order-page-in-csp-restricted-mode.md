---
title: 订单创建页面疑难解答 [!UICONTROL CSP] 受限模式
description: 本文介绍了在启用CSP限制模式时在管理员端创建订单时发生的错误，并提供修复这些错误的解决方案。
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 订单创建页面疑难解答 [!UICONTROL CSP] 受限模式

本文为在管理员端使用创建订单时出现Adobe Commerce 2.4.7问题提供了说明和修复 **[!UICONTROL CSP restricted mode]** 是 *已启用*，带有&quot;*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“浏览器控制台日志中显示错误消息。

## 受影响的产品和版本

云基础架构上的Adobe Commerce、Adobe Commerce内部部署和Magento Open Source：

* 2.4.7
* 2.4.6像素
* 2.4.5-pX
* 2.4.4像素

## 问题 — 管理员 **创建订单** 页面已损坏或无法加载

管理员 **创建订单** 页面已损坏或无法加载，使用&quot;*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“浏览器控制台日志中显示错误消息。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. 创建新订单。

<u>预期结果</u>：

管理员 **创建订单** 页面会正常完全加载。

<u>实际结果</u>：

管理员 **创建订单** 页面为空或缺少组件。 以下各项 [!DNL JS] 错误显示在浏览器控制台日志中：“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中， **[!UICONTROL CSP]** 在中配置 `restrict-mode`，默认情况下，适用于店面和管理区域以及中的付款页面 `report-only` 模式。
对应的 **[!UICONTROL CSP]** 标题不包含 `unsafe-inline` 中的关键词 `script-src` 付款页的指令。 此外，仅限 [!DNL whitelisted] 允许使用内联脚本。

### 解决方案

由于某些脚本被阻止，用户可能会看到浏览器错误 [!UICONTROL CSP]：

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

管理员缺少付款方法或无法使用该方法 **订单创建页面**，带有&quot;*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“浏览器控制台日志中显示错误消息。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. 创建新订单。
1. 创建新客户。
1. 输入客户详细信息。
1. 输入订单详细信息（产品、发运方法）。
1. 选择付款方式。

<u>预期结果</u>：

您可以选择付款方式并继续成功下单。

<u>实际结果</u>：

付款方式缺失或无法正常工作。 以下各项 [!DNL JS] 错误显示在浏览器控制台日志中：“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“。

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中， **[!UICONTROL CSP]** 在中配置 `restrict-mode`，默认情况下，适用于店面和管理区域以及中的付款页面 `report-only` 模式。
对应的 **[!UICONTROL CSP]** 标题不包含 `unsafe-inline` 中的关键词 `script-src` 付款页的指令。 此外，仅限 [!DNL whitelisted] 允许使用内联脚本。

### 解决方案

由于某些脚本被阻止，用户可能会看到浏览器错误 **[!UICONTROL CSP]**：

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

## 问题 — 管理员无法下订单

管理员无法向管理员提交订单 **创建订单页**，带有&quot;*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*“浏览器控制台日志中显示错误消息。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. 创建新订单。
1. 创建新客户。
1. 输入客户详细信息。
1. 输入订单详细信息（产品、发运方法）。
1. 选择付款方式。
1. 提交订单。

<u>预期结果</u>：

您可以成功提交订单。

<u>实际结果</u>：

您无法提交订单。 以下各项 [!DNL JS] 错误显示在浏览器控制台日志中：“*拒绝执行内联脚本，因为它违反了以下内容安全策略指令： &quot;script-src ...*&quot;

### 原因

在Adobe Commerce和Magento Open Source版本2.4.7及更高版本中， **[!UICONTROL CSP]** 在中配置 `restrict-mode`，默认情况下，适用于店面和管理区域以及中的付款页面 `report-only` 模式。
对应的 **[!UICONTROL CSP]** 标题不包含 `unsafe-inline` 中的关键词 `script-src` 付款页的指令。 此外，仅限 [!DNL whitelisted] 允许使用内联脚本。

### 解决方案

由于某些脚本被阻止，用户可能会看到浏览器错误 **[!UICONTROL CSP]**：

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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
