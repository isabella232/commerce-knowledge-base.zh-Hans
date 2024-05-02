---
title: 'MDVA-33559修补程序：PayflowPro付款被拒绝错误'
description: MDVA-33559补丁解决了PayPal PayflowPro付款被拒绝的问题。
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# MDVA-33559修补程序： PayflowPro付款已拒绝错误

MDVA-33559补丁解决了PayPal PayflowPro付款被拒绝的问题。

此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.15。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：** 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此问题与名称中使用的&amp;符号和等号(=)特殊字符有关。

<u>重现问题的步骤</u>：

1. 将简单产品添加到购物车。
1. 去结帐。
1. 设置送货地址。 (示例送货地址： **名字** = ** *约翰的* **  **姓氏** = ** *苹果和橘子公司* **  **街道地址** = *1234 E Nameless St*  **国家/地区** = *US*  **省/市/自治区** = *Anystate*  **城市** = *Anytown*  **Zip** = *12345*  **电话** = *1234567890*)
1. 将付款设置为 **PayPal PayflowPro** 并尝试完成结帐。

<u>预期结果</u>：

如预期，交易会导致付款成功或出现正确的错误消息。

<u>实际结果</u>：

交易被拒绝，客户收到一封电子邮件，上面写着“交易已被拒绝”。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
