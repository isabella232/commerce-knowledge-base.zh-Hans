---
title: Adobe Commerce支持票证生命周期策略更新
description: 本文提供有关Adobe Commerce支持票证生命周期策略更新的信息。
exl-id: c3fbcb4a-107f-48b3-afed-b9a0c5d0425c
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Adobe Commerce支持票证生命周期策略更新

本文提供有关Adobe Commerce支持票证生命周期策略更新的信息。

下表说明了更新的方案。 您可以在下面部分中找到每个方案的详细信息。

<table>
 <tbody>
 <tr>
 <td class="wysiwyg-text-align-center"> </td>
 <td class="wysiwyg-text-align-center"><strong>票证状态</strong></td>
 <td class="wysiwyg-text-align-center"><strong>“已解决”的天数</strong></td>
 <td class="wysiwyg-text-align-center"><strong>“关闭”的天数</strong></td>
 <td class="wysiwyg-text-align-center"><strong>通知计时</strong></td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>工程师提供解决方案</strong></td>
 <td class="wysiwyg-text-align-center">“等待您的回复”</td>
 <td class="wysiwyg-text-align-center">3</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">第3天和第6天</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>等待客户提供的信息</strong></td>
 <td class="wysiwyg-text-align-center">“等待您的回复”</td>
 <td class="wysiwyg-text-align-center">不适用</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">第1、3和6天</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>客户将设置为“已解决”或请求工程师将设置为“已解决”</strong></td>
 <td class="wysiwyg-text-align-center">“已解决”</td>
 <td class="wysiwyg-text-align-center">立即</td>
 <td class="wysiwyg-text-align-center">1</td>
 <td class="wysiwyg-text-align-center">第1天</td>
 </tr>
 </tbody>
 </table>

## 详细情景

### 当工程师提供解决方案时

1. 将解决方案提供给客户后，工程师会将票证状态设置为“等待您的回复”。
1. 如果在状态更改为“等待您的回复”后3天内客户没有回应，则票证将移至“已解决”状态并通知客户。
1. 如果在状态更改为“等待您的回复”后6天内客户没有回应，则票证已关闭并通知客户。

### 需要客户提供其他信息时

1. 如果要求客户进行更新，工程师会将票证设置为“等待您的回复”。
1. 在第1天和第3天向客户发送通知，要求客户跟进。
1. 如果在状态更改为“等待您的回复”后6天内客户没有回应，则票证已关闭并通知客户。

### 客户将票证设置为“已解决”

当客户将票证设置为“已解决”时，该票证会在一天内关闭并通知客户。

### 客户指示支持人员关闭票证

当客户指示Adobe Commerce支持关闭票证时，票证在一天内关闭并通知客户。

## 相关阅读

* [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
* [Adobe Commerce帮助中心起始页上未显示“提交票证”链接](/help/help-center-guide/help-center/magento-help-center-user-guide.md#no-submit-link)
* [票证提交表单：商家未显示在“组织”下拉列表中](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)
