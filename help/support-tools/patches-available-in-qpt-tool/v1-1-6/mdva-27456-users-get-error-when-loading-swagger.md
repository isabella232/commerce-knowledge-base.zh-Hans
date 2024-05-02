---
title: 'MDVA-27456：用户加载Swagger时出错'
description: MDVA-27456修补程序修复了用户在尝试加载Swagger时出现错误的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-27456。 请注意，Adobe Commerce 2.3.7中已修复此问题。
exl-id: e331595f-a94b-4070-803a-60f559735b29
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# MDVA-27456：用户加载Swagger时遇到错误

MDVA-27456修补程序修复了用户在尝试加载Swagger时出现错误的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.1.6。 修补程序ID为MDVA-27456。 请注意，Adobe Commerce 2.3.7中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

Adobe Commerce（所有部署方法） 2.3.5-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户加载Swagger时出错。

<u>重现问题的步骤</u>：

转到 `../swagger.`

<u>预期结果</u>：

Swagger会加载，不会出现任何错误。

<u>实际结果</u>：

用户收到以下错误： *无法加载API定义*. 错误日志包含：

*report.CRITICAL：报表ID： webapi-5ea9c6da19cb1；消息：“\DateTime”参数类型无效。 请验证参数并重试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
