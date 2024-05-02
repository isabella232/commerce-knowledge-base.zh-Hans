---
title: QPT工具中提供的修补程序概述
description: 本文概述了 [!DNL Quality Patches Tool] (QPT)和解释如何使用它的资源链接。
exl-id: ac1c6088-44fe-452c-a39b-3c35697e1cc3
feature: Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# QPT工具中提供的修补程序概述

本文概述了 [!DNL Quality Patches Tool] (QPT)和解释如何使用它的资源链接。

## 受影响的产品和版本

* Adobe Commerce内部部署，所有 [支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 云基础架构上的Adobe Commerce，全部 [支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 什么是质量修补程序工具？

此 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) (QPT)是一种允许您应用由Adobe和Magento Open Source团体开发的单个质量补丁程序的工具。

它允许您：

* 将优质补丁程序应用到包
* 还原以前应用的修补程序
* 查看有关适用于已安装的Adobe Commerce版本的质量修补程序的一般信息。

下面是状态表的示例，您可以获得该表以查看可用的修补程序：

![Magento修补程序列表](assets/status_table.png)

该工具旨在让您能够自助提供修补程序，以解决在Adobe Commerce中可能遇到的问题，或轻松应用Adobe Commerce支持人员建议的修补程序。

>[!NOTE]
>
>QPT仅适用于高质量的修补程序。 安全修补程序可在 [Adobe Commerce和Magento Open Source的发行说明](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html).

## 中提供的修补程序 [!DNL Quality Patches Tool]

在Adobe Commerce支持知识库的此部分中，您将找到按QPT修补程序解决的问题按QPT发行版本分组的详细说明。
您还可以查看可用QPT修补程序的列表，并使用上动态生成的表按组件筛选 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在我们的支持知识库中。

## 如何安装和使用 [!DNL Quality Patches Tool]

对于云基础架构上的Adobe Commerce内部部署和Adobe Commerce，安装和使用命令有所不同，因为对于云，QPT包包含在ece-tools包中。

### 如何在Adobe Commerce内部部署安装和使用QPT

请参阅 [Commerce >工具>使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) ，以了解有关如何安装和使用QPT来应用和还原修补程序的详细信息。

### 如何在云基础架构上安装和使用QPT for Adobe Commerce

请参阅 [Commerce on Cloud Infrastructure指南>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 请参阅我们的开发人员文档，详细了解如何安装和使用QPT在云基础架构上的Adobe Commerce上应用和还原修补程序。

## 相关阅读

* [[!DNL Quality Patches Tool] 发行说明](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) 在我们的开发人员文档中。
