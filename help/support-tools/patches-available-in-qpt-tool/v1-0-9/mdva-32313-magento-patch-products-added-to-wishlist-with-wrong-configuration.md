---
title: 'MDVA-32313修补程序：产品已添加到包含错误配置的愿望清单'
description: MDVA-32313修补程序解决了无法将可配置产品正确添加到愿望列表的问题，因为在将可配置产品添加到愿望列表时，会向这些产品分配错误的配置。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.2中已修复此问题。
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-32313修补程序：使用错误的配置添加到愿望清单中的产品

MDVA-32313修补程序解决了无法将可配置产品正确添加到愿望列表的问题，因为在将可配置产品添加到愿望列表时，会向这些产品分配错误的配置。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.10。 请注意，Adobe Commerce版本2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.0

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.3.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 创建客户。
1. 登录到客户帐户。
1. 导航至 **产品列表** 页面。
1. 选择可配置的产品(例如： *可配置\_1* )，并在上选择首选的颜色和大小选项 **产品列表** 页面(**请勿打开产品页面。**)。
1. 单击另一个可配置产品的愿望清单图标(例如： *可配置\_2*)，而不选择任何颜色/大小选项。

<u>预期结果</u>：

此 *可配置\_2* 产品会按预期添加到愿望清单，但未选择任何选项。

<u>实际结果</u>：

此 *可配置\_2* 产品已从配置添加到愿望清单 *可配置\_1* 产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
