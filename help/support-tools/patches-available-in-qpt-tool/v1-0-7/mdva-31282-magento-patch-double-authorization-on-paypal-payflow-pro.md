---
title: 'MDVA-31282：Paypal PayFlow Pro的双重授权'
description: MDVA-31282修补程序解决了在Adobe Commerce中的Paypal PayFlow Pro上发生双重授权的问题。 这种双重授权还产生了绕过PayFlow Pro欺诈筛选器和将交易费用翻倍的效果。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282：Paypal PayFlow Pro的双重授权

MDVA-31282修补程序解决了在Adobe Commerce中的Paypal PayFlow Pro上发生双重授权的问题。 这种双重授权还产生了绕过PayFlow Pro欺诈筛选器和将交易费用翻倍的效果。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.7。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.3.3和2.3.5 - 2.3.6

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在Adobe Commerce的PayPal PayFlow Pro中会出现双重授权，这会绕过PayFlow Pro的欺诈筛选器和将交易费用加倍。

<u>先决条件</u>：

配置PayPal PayFlow Pro支付方式。

<u>重现问题的步骤</u>：

1. 作为客人前往前端。
1. 将产品添加到 **购物车** 从产品页面。
1. 继续到 **结帐**.
1. 指定 **配送地址** 作为国家/地区的地址\#1（例如：英国地址），并选择一种配送方式。
1. 选择 **PayPal PayFlow Pro** 作为付款方式。 指定 **帐单地址** 作为国家/地区的地址\#2（例如：美国地址）。
1. 输入信用卡数据并下订单。
1. 导航到 **销售** > **订购** 在管理员中，观察创建的顺序。

<u>预期结果</u>：

* 此时将显示“付款信息”块： *“触发的欺诈过滤器： RESPMSG：欺诈服务正在审查*. *订单处于可疑欺诈状态”*.
* Paypal PayFlow Pro按预期显示单个授权交易。

<u>实际结果</u>：

* 此时将显示“付款信息”块： *“触发的欺诈过滤器： RESPMSG：欺诈服务正在审查*. *订单处于处理状态”*.
* Paypal PayFlow Pro显示双重授权交易。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
