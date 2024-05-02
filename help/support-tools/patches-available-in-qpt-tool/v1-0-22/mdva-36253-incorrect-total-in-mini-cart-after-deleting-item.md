---
title: 'MDVA-36253：删除项目后，迷你购物车中的总计不正确'
description: MDVA-36253修补程序解决了以下问题：在使用多配送结账步骤时，如果在删除产品后返回迷你购物车页面，则无法更新产品价格。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22后，即可使用此修补程序。 修补程序ID为MDVA-36253。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: cbd436d7-7fbd-46dd-97cf-30f709da1ce5
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-36253：删除项目后，迷你购物车中的总计不正确

MDVA-36253修补程序解决了以下问题：在使用多配送结账步骤时，如果在删除产品后返回迷你购物车页面，则无法更新产品价格。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.22。 修补程序ID为MDVA-36253。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.0-2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

删除项目后，迷你购物车中的总计不正确。

<u>重现问题的步骤</u>：

1. 以至少具有一个地址的客户的身份登录。
1. 将四个产品添加到购物车（价格=每个$10）。
1. 转到购物车并单击 **使用多个地址签出**.
1. 删除一个项目。
1. 导航回主页。
1. 打开购物车并检查总价。

<u>预期结果</u>：

总共是30美元。

<u>实际结果</u>：

总共是40美元。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
