---
title: '''MDVA-31399 patch：小计(包括 Tax)（在购物车规则条件中）'
description: MDVA-31399修补程序将添加*小计(包括 Tax)*选项更改为[购物车价格规则条件](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions)，修复了无法根据小计应用购物车价格规则的问题(包括 税号。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12后，即可使用此修补程序。
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-31399修补程序：小计(包括 Tax)（在购物车规则条件中）

MDVA-31399修补程序将添加 *小计(包括 Tax)* 选项至 [购物车价格规则条件](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions)，修复了无法应用基于小计的购物车价格规则的问题(包括 税号。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.12。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.2 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法应用基于小计的购物车价格规则(包括 税号。

<u>重现问题的步骤</u>：

1. 配置产品价格以含税。
1. 创建20%的税则和税率。
1. 创建产品，使用 **价格** = *100* （此价格包含税金）。
1. 创建带有优惠券“10off”的新购物车价格规则，以便在小计符合以下条件时应用$10固定折扣：

**条件**： *如果所有这些条件都为TRUE ：*        * **小计** 等于或大于100。*

<u>预期结果</u>：

能够创建带有优惠券的购物车小计价格规则，以将折扣应用于小计（包括税金）。

<u>实际结果</u>：

购物车规则条件中有两个选项： *小计* 和 *小计(不包括 Tax)*，并且无论选择哪种规则，该规则都只应用于不含税的小计。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
