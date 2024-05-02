---
title: “MDVA-30593修补程序：未清理过期的引号”
description: MDVA-30593修补程序解决了根据**Quote Lifetime**设置过期的引号无法清理的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5后，即可使用此修补程序。 请注意，Adobe Commerce 2.3.4中已修复此问题。
exl-id: 5ee91546-a5cb-4282-bdfc-c9bb3438af50
feature: Cache, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# MDVA-30593修补程序：未清理过期的引号

MDVA-30593修补程序解决了根据 **引用生命周期** 设置，将不会清除。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.5。 请注意，Adobe Commerce 2.3.4中已修复此问题。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.3.0 - 2.3.3.x

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

报价单，根据 **引用生命周期** 设置，将不会清除。

<u>重现问题的步骤：</u>

1. 在Commerce Admin中，转到 **商店** > **配置** > **销售** > **结帐** > **购物车**.
1. 设置 **报价生命周期（天）** = *1*
1. 保存配置并清除缓存。
1. 以客户身份登录。
1. 将产品添加到购物车。
1. 一天后，返回购物车。

<u>预期结果：</u>

由于旧价格不再有效，因此将清除报价并从购物车中删除产品。

<u>实际结果：</u>

产品仍在购物车中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
