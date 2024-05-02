---
title: 'MDVA-39305：启用了Google reCAPTCHA的登录问题'
description: MDVA-39305修补程序修复了已注册客户无法使用已启用的Google reCAPTCHA登录的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1后，即可使用此修补程序。 修补程序ID为MDVA-39305。 请注意，该问题计划在Adobe Commerce版本2.4.4和2.4.7中修复。
exl-id: 1e8e7dc7-f8f1-4432-90f4-dc73d85f353a
feature: Console
role: Admin
source-git-commit: d48abbf3ecc19a78ee1d86a12d9c32cba17d53e5
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-39305：启用了Google reCAPTCHA的登录问题

MDVA-39305修补程序修复了已注册客户无法使用已启用的Google reCAPTCHA登录的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.1。 修补程序ID为MDVA-39305。 请注意，该问题计划在Adobe Commerce版本2.4.4和2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.4.2-p1、2.4.3-p3、2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1-p1 - 2.4.3-p3、2.4.4-p1 - 2.4.4-p5、2.4.5 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

注册客户无法使用启用的Google reCAPTCHA登录。

<u>重现问题的步骤</u>：

1. 转到 **存储** > **配置** > **安全性** > **Google reCAPTCHA店面** 并启用 **Google reCAPTCHA**.
1. 转到 **前端**.
1. 打开 **开发人员工具控制台** 在浏览器中。

<u>预期结果</u>：

控制台中没有CSP警告。

<u>实际结果</u>：

控制台中出现CSP警告。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
