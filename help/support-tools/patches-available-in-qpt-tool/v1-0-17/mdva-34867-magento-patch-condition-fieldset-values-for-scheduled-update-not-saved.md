---
title: 'MDVA-34867：未保存计划更新的条件字段集值'
description: MDVA-34867修补程序解决了在编辑目录价格规则时，新计划更新中的条件的值未保存的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867：未保存计划更新的条件字段集值

MDVA-34867修补程序解决了在编辑目录价格规则时，新计划更新中的条件的值未保存的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.17。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

编辑目录价格规则时，未保存新计划更新中的条件的值。

<u>重现问题的步骤</u>：

1. 登录到Admin。
1. 创建 **目录规则** 替换为 **条件** = &quot;*类别为1*“。
1. 计划一个开始日期在未来（例如：明天）的更新，并设置 **条件** = &quot;*类别为2、3*&#39;&#39;，并保存更新。
1. 单击 **查看/编辑** ，并检查条件字段。

<u>预期结果</u>：

此 **目录规则的**  **条件** = &quot;*类别为2、3*“，如预期。

<u>实际结果</u>：

此 **目录规则的**  **条件** = &quot;*类别为1*“”表示未保存更新。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
