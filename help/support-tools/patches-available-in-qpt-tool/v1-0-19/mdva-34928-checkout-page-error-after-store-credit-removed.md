---
title: 'MDVA-34928：删除商店信用后出现签出页面错误'
description: MDVA-34928修补程序解决了以下问题：删除商店点数后，结账页面上有无限加载程序。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-34928。 请注意，Adobe Commerce 2.3.6中已修复此问题。
exl-id: 9ef6777a-88c8-4fed-a296-0cb4e6ad153a
feature: Checkout, Orders, Returns, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-34928：删除商店点数后出现签出页面错误

MDVA-34928修补程序解决了以下问题：删除商店点数后，结账页面上有无限加载程序。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.19。 修补程序ID为MDVA-34928。 请注意，Adobe Commerce 2.3.6中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

删除商店点数后，结账页面上有无限加载程序。

<u>重现问题的步骤</u>：

1. 创建客户帐户。
1. 确定要添加到购物车的可能项目 — 记下价格。
1. 在“管理员”中编辑帐户。
1. 单击 **商店点数**.
1. 添加金额以覆盖项目的价格。
1. 以客户身份登录店面。
1. 将项目添加到购物车。
1. 继续结帐。
1. 申请商店积分。
1. 尝试删除商店点数。

<u>预期结果</u>：

已删除商店点数。

<u>实际结果</u>：

无限加载器会旋转，直到页面刷新为止。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
