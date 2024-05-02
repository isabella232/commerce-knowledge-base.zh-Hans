---
title: 'MDVA-35312：空GraphQL请求引发500错误，而不是200确定'
description: MDVA-35312修补程序修复了空GraphQL请求引发错误响应代码500的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18后，即可使用此修补程序。 修补程序ID为MDVA-35312。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: 345fdbd4-8a43-4aab-a318-72792c8a7a78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# MDVA-35312：空GraphQL请求引发500错误，而不是200确定

MDVA-35312修补程序修复了空GraphQL请求引发错误响应代码500的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.18。 修补程序ID为MDVA-35312。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Magento版本创建的：**

云基础架构上的Adobe Commerce 2.4.2

**与Magento版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.4.1-p1-2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

空GraphQL请求引发错误响应代码500，而不是200。

<u>重现问题的步骤</u>：

发送一个GraphQL请求，例如：

```curl
curl -i -X OPTIONS http://inv.test/graphql
```

<u>预期结果</u>：

响应： *200 OK*.

<u>实际结果</u>：

响应： *HTTP/1.1 500内部服务器错误*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
