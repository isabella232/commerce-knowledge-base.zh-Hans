---
title: Adobe Commerce [!DNL Site-Wide Analysis Tool] 报表常见问题解答
description: 了解 [!DNL Site-Wide Analysis Tool]，这是一个主动式自助服务工具和中央存储库，其中包含详细的系统分析和建议，以确保Adobe Commerce安装的安全性和可操作性。
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Adobe Commerce [!DNL Site-Wide Analysis Tool] 报表常见问题解答

>[!IMPORTANT]
>
>自二零二四年四月二十三日起， [!DNL Site-Wide Analysis Tool] 将为所有Adobe Commerce内部部署客户停用。

本文介绍 [!DNL Site-Wide Analysis Tool] 为云基础架构上的Adobe Commerce客户每月或每季度自动生成的报表。

>[!NOTE]
>
>在Adobe Commerce on cloud infrastructure v2.4.1及更高版本中， [!DNL Site-Wide Analysis Tool] 通过Commerce管理面板提供。 因此， [!DNL Site-Wide Analysis Tool] 报告可以直接由客户运行。 有关访问详情，请参阅 [[!DNL Site-Wide Analysis Tool] 指南](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html).

## 什么是 [!DNL Site-Wide Analysis Tool]？

[!DNL Site-Wide Analysis Tool] 是一个SaaS应用程序，它执行端到端“时间点”客户站点分析(在 [!DNL Site-Wide Analysis Tool] 环境，而不是客户网站上)。 全部 [!DNL Site-Wide Analysis Tool]按预定计划从每3小时收集一次客户地点信息到每天收集一次。 这意味着 [!DNL Site-Wide Analysis Tool] 在不断分析客户站点数据以寻找发现。

## 什么是 [!DNL Site-Wide Analysis Tool] 报告？

此 [!DNL Site-Wide Analysis Tool] 报告是自助服务与最佳实践推荐的调查结果（问题）列表，可通过Adobe Commerce支持票证系统以PDF形式发送给客户。

## 中包含哪些信息 [!DNL Site-Wide Analysis Tool] 报告？

网站信息，请参见 [!DNL Site-Wide Analysis Tool] 报表，包括：

* 调查结果
   * 概述，包括实施修复顺序的“优先级”
   * 查找结果描述
   * 前提条件（如果有）
   * 网站影响
   * 根本原因
   * 推荐
* 异常日志
   * 记录异常信息
   * 上次发生的日期
   * 异常发生的次数

## 谁每月自动接收 [!DNL Site-Wide Analysis Tool] 报告？

目前，拥有较少客户群 [!DNL Site-Wide Analysis Tool] 运行状况索引（达到或低于当前设置的性能阈值）将每月接收一次 [!DNL Site-Wide Analysis Tool] 通过支持工单系统报告其生产环境。

## 谁每季度自动接收一次 [!DNL Site-Wide Analysis Tool] 报告？

所有客户，无论 [!DNL Site-Wide Analysis Tool] 健康指数，每季度 [!DNL Site-Wide Analysis Tool] 通过支持工单系统报告其生产环境。

## 如何传送报表？

[!DNL Site-Wide Analysis Tool] 每月或每季度通过Adobe Commerce支持票证系统自动交付报表。 [!DNL Site-Wide Analysis Tool] 报告也可以手动生成 [!DNL Site-Wide Analysis Tool] 仪表板并保存到桌面。 这些 [!DNL Site-Wide Analysis Tool] 然后，可以将报告作为附件通过电子邮件发送。

>[!NOTE]
>
>应用推荐后，手动生成报告不会更新推荐 — 可能需要几天时间才能将其从删除 [!DNL Site-Wide Analysis Tool Dashboard].
