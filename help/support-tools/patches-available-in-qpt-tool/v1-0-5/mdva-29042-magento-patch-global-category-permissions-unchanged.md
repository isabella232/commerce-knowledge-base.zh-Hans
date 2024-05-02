---
title: 'MDVA-29042：全局类别权限未更改'
description: MDVA-29042修补程序修复了以下问题：在“Commerce管理”中将新产品添加到共享目录后，目录权限会自动更改为“*Allow*”。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5后，即可使用此修补程序。 请注意，Adobe Commerce 2.3.6中已通过B2B扩展修复该问题。
exl-id: 491b8881-87ec-4820-8f87-54961682e961
feature: Catalog Management, Categories, Customer Service, Roles/Permissions
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# MDVA-29042：全局类别权限未更改

MDVA-29042修补程序修复了目录权限被更改为&#39;&#39;的问题&#x200B;*允许*”在将新产品添加到Commerce管理中的共享目录后自动进行。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.5。 请注意，Adobe Commerce 2.3.6中已通过B2B扩展修复该问题。

## 受影响的产品和版本

Adobe Commerce（所有部署方法）从2.3.3到2.3.4-p2，带有B2B扩展

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在Commerce管理员的全局类别权限中取消选择客户组不会将该客户组自动设置为&quot;*拒绝*&#x200B;类别权限中的&quot;。

<u>先决条件</u>：

* 在下定义和选择客户组的B2B实例 **商店** > **配置** > **目录** > **目录** > **类别权限** 对于：
   * **允许浏览类别**
   * **显示产品价格**
   * **允许添加到购物车**
* 在每个 **类别**，则客户组被定义为&quot;*允许*”用于：
   * **浏览类别**
   * **显示产品价格**
   * **添加到购物车**

<u>重现问题的步骤</u>：

1. 在Commerce Admin中，转到 **商店** > **配置** > **目录** > **目录** > **类别权限** 并从以下位置取消选择客户组：
   * **允许浏览类别**
   * **显示产品价格**
   * **允许添加到购物车**
1. 单击 **保存配置** 按钮。
1. 等待索引器运行。
1. 查看 **目录** > **类别** > **类别权限**.

<u>预期结果</u>：

**类别权限** 将设置为&quot;*拒绝*”代表客户组的所有类别。

<u>实际结果</u>：

客户组的任何类别权限未发生更改。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。

要了解有关B2B公司功能的更多信息，请参阅我们的开发人员文档中的以下文章：

* [B2B开发人员指南](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [管理公司角色](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B扩展配置路径参考](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
