---
title: 'MDVA-29954：发送新的公司用户注册电子邮件的地址错误'
description: MDVA-29954修补程序解决了从错误的电子邮件地址发送“新公司注册请求”和“您已链接到公司”电子邮件的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 9b3d1b93-3fe6-40a0-a68a-3e3d789c6d66
feature: B2B, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29954：发送新的公司用户注册电子邮件的地址错误

MDVA-29954修补程序解决了从错误的电子邮件地址发送“新公司注册请求”和“您已链接到公司”电子邮件的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.8。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.3.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.3.5-p2、2.4.0和2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

使用B2B安装Adobe Commerce **B2B功能** 和 **公司** 已启用。

<u>重现问题的步骤</u>：

1. 单击 **创建帐户** 店面中的下拉菜单，然后选择 **新建公司帐户**.
1. 填写必填字段，然后注册帐户。
1. 启用 **公司** 从后端(**客户** > **公司**)。
1. 检查用于注册的电子邮件地址。
1. 设置 **公司管理员密码** 按照电子邮件中的说明执行操作。
1. 使用登录到前端 **公司管理员密码**.
1. 新建 **公司用户** 在 **我的帐户** > **公司用户** > **添加新用户**.
1. 转到 **商店** > **配置** > **通用商店电子邮件地址** > **常规联系人**，并选中 **发件人电子邮件**.
1. 转到用于注册 **新用户** 步骤7.

<u>预期结果</u>：

“您已链接到公司”电子邮件是从与的值相同的电子邮件地址发送的 **发件人电子邮件** 步骤8.

<u>实际结果</u>：

“您已链接到公司”电子邮件发送自 **公司管理员** 电子邮件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
