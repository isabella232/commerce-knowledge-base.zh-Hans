---
title: 'MDVA-31791修补程序：改进了包含相关产品和目标规则的产品页面'
description: 当使用[相关产品](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html)或[相关产品规则](https://docs.magento.com/user-guide/marketing/product-related-rules.html)（目标规则）时，MDVA-31791补丁程序可提高产品页面的性能。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.1中已修复此问题。
exl-id: e737bccb-d9eb-4794-9d6b-2c22fa8edaa2
feature: Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-31791修补程序：改进了包含相关产品和目标规则的产品页面

在以下情况下，MDVA-31791补丁程序可提高产品页面的性能 [相关产品](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) 或 [相关产品规则](https://docs.magento.com/user-guide/marketing/product-related-rules.html) （target规则）时，不会将反向链接计算两次。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.9。 请注意，Adobe Commerce 2.4.1中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.4、2.3.4-p1、2.3.4-p2、2.4.0、2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果使用相关产品或Target规则，则产品页面性能较低。

如果要使用，请考虑应用MDVA-31791修补程序 [相关产品](https://docs.magento.com/user-guide/catalog/settings-advanced-related-products.html) 或 [相关产品规则](https://docs.magento.com/user-guide/marketing/product-related-rules.html) 功能。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
