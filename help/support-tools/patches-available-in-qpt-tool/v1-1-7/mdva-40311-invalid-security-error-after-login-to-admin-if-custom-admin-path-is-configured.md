---
title: 'MDVA-40311：如果配置了自定义管理路径，则登录Admin后出现“安全或表单密钥无效”错误'
description: 'MDVA-40311修补程序修复了管理员用户收到错误消息的问题：*无效的安全性或表单密钥。 如果配置了自定义管理路径并且启用了密钥，请在登录Admin后刷新页面*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7后，即可使用此修补程序。 修补程序ID为MDVA-40311。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。'
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311：如果配置了自定义管理路径，则登录Admin后会出现“安全性或表单密钥无效”错误

MDVA-40311修补程序修复了管理员用户收到错误消息的问题： *无效的安全性或表单密钥。 请刷新页面*，在登录到Admin后（如果已配置自定义管理路径并且启用了密钥）。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.7。 修补程序ID为MDVA-40311。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员用户收到一条错误消息： *无效的安全性或表单密钥。 请刷新页面*，在登录到Admin后（如果已配置自定义管理路径并且启用了密钥）。

<u>重现问题的步骤</u>：

* 使用有效的用户名和密码以管理员用户身份登录。

<u>预期结果</u>：

用户登录时不会出现任何错误消息。

<u>实际结果</u>：

*无效的安全性或表单密钥。 请刷新页面* 将显示错误消息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
