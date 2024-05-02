---
title: Adobe Commerce支持知识库
description: 排除Commerce商店故障和维护所需了解的一切。
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 95509b717d41436b68ad94c3c28ac72e1887fdfc
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 1%

---

# Adobe Commerce支持知识库

![知识库主页](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

本知识库中的信息旨在补充 [Adobe Commerce开发人员文档](https://developer.adobe.com/commerce/docs)、和 [《Adobe Commerce商户指南》](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)和其他Adobe Commerce出版物。 它涵盖故障排除和最佳实践，发布公告，回答常见问题，并重点说明官方文档中未提及（出于任何原因）的特定场景。

## 知识库中的内容

| 类别 | 描述 |
| --- | --- |
| [支持工具](/help/support-tools/overview.md) | 使用Adobe Commerce提供的各种支持工具改善您的电子商务商店体验。 我们提供个性化的最佳实践、诊断和监控工具，以及有关您站点的最相关信息。 |
| [公告](/help/announcements/overview.md) | 从 Adobe Commerce 团队获取重要更新。 |
| [疑难解答](/help/troubleshooting/overview.md) | 从Adobe Commerce支持团队获取自助解决方案和修补程序。 |
| [帮助中心用户指南](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | 了解如何有效地管理支持工单、授予共享访问权限和浏览知识库。 |
| [操作方法](/help/how-to/overview.md) | 从Adobe Commerce支持团队获取明确的分步说明。 |
| [常见问题解答](/help/faq/overview.md) | 查找有关Adobe Commerce策略、策略的常见问题解答以及有关Adobe Commerce功能的详细信息。 |

>[!NOTE]
>
>要提交新票证，请登录 [Adobe Commerce帮助中心](https://support.magento.com/) 并遵循中详述的步骤 [提交支持服务单](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
>
>如果看不到提交票证的选项，请参阅 *[提交未显示的票证链接](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* 部分(位于 [帮助中心用户指南](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## 新增功能

<table style="width:100%">
  <tr>
    <th style="width:70%">描述</th>
    <th style="width:15%">类型</th>
    <th style="width:15%">日期</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-update-the-cloud-account-profile">如何更新云帐户配置文件：</a> 本文介绍了如何在云帐户上修改用户档案的步骤。
    </td>
    <td>新文章</td>
    <td>2024年4月22日</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/admin-create-order-page-in-csp-restricted-mode">对CSP限制模式下的创建订单页面进行故障诊断：</a> 本文提供了在CSP限制模式下在管理员端创建订单时，有关Adobe Commerce 2.4.7问题的解释和修复 <em>已启用</em>.  
    </td>
    <td>新文章</td>
    <td>2024年4月22日</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/storefront-checkout-page-in-csp-restricted-mode">对CSP限制模式下的storefront签出页面进行故障排除：</a> 本文介绍了在CSP限制模式下查看签出页面时，出现Adobe Commerce 2.4.7问题的解释和修复，其中使用 <em>“拒绝执行内联脚本，因为它违反了以下内容安全策略指令："script-src ..."</em> 浏览器控制台日志中的错误消息。 
    </td>
    <td>新文章 </td>
    <td>2024年4月22日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-54656-invisible-recaptcha-fails-during-checkout-preventing-order-placement">ACSD-54656：在签出期间不可见的reCAPTCHA不起作用，导致订单无法下达：</a> ACSD-54656修补程序修复了在签出期间，不可见的reCAPTCHA无法正常工作，从而导致无法下订单的问题。 此修补程序在以下情况下可用： <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 已安装1.1.46。 
    </td>
    <td>新文章 </td>
    <td>2024年4月22日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-46767-category-page-caches-invalidate-when-the-stock-quantity-changes">ACSD-46767：库存数量更改时，“类别”页将缓存失效：</a> ACSD-46767修补程序修复了库存数量更改时，即使产品仍有库存，类别页面缓存也会失效的问题。 此修补程序在以下情况下可用： <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 已安装1.1.46。  
    </td>
    <td>新文章 </td>
    <td>2024年4月22日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-45/acsd-56415-performance-of-partial-price-indexing-is-slowed-down-due-to-a-delete-query">ACSD-56415：由于DELETE查询，部分价格索引的性能降低：</a> ACSD-56415修补程序修复了在数据库具有大量局部价格数据索引时，由于DELETE查询而导致局部价格索引的性能变慢的问题。 此修补程序在以下情况下可用： <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 已安装1.1.45。  
    </td>
    <td>新文章 </td>
    <td>2024年4月22日</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56858-role-permissions-display-issue-in-b2b-company-admin-panel">ACSD-56858：B2B公司管理员中的角色权限差异：</a> ACSD-56858修补程序修复了以下问题：在B2B环境中，针对受限制的公司管理员的角色权限显示不正确。 此修补程序在以下情况下可用： <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 已安装1.1.47。 
    </td>
    <td>新文章 </td>
    <td>2024年4月22日</td>
 </tr>
</table>

## 受欢迎的文章

* [在Cloud 2.4.4上切换到OpenSearch for Adobe Commerce](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Adobe Commerce中的Apache log4j2漏洞](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [可用于Adobe Commerce APSB22-12的安全更新](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [识别和测量云基础架构上Adobe Commerce的中断](/help/how-to/general/how-to-identify-outages.md)
* [在Adobe Commerce上的群集中查看环境vCPU层](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [云基础架构上的Adobe Commerce：CPU分配计算](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [云基础架构上的Adobe Commerce：检查主机的CPU配置](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
