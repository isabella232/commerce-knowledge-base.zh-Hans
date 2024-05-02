---
title: “ACSD-55241：**已使用**和**已使用次数**属性显示的已生成优惠券值不正确”
description: 应用ACSD-55241修补程序以修复Adobe Commerce问题，该问题导致**已使用**和**使用次数**属性显示生成的赠券的值不正确
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241： **已使用** 和 **使用时间** 属性显示的已生成优惠券值不正确

ACSD-55241修补程序修复了 **已使用** 和 **使用时间** 属性显示的已生成优惠券值不正确。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.47。 修补程序ID为ACSD-55241。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

**已使用** 和 **使用时间** 属性显示的已生成优惠券值不正确。

<u>重现问题的步骤</u>：

1. 创建 **[!UICONTROL Cart Price Rules]** 从 **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** 并添加在下订单时匹配的任何条件(示例：小计大于 *5$*)

* 应用任何折扣。
* 选择 **[!UICONTROL Auto Coupon]**.
* 它将从中生成一些优惠券代码 **管理优惠券代码**.
* 重新索引并清理缓存。

1. 创建 **[!UICONTROL customer account]** 登入前台。
1. 添加一个产品，其多项 *2* 购物车中的数量并申请一张优惠券。
1. 单击 **[!UICONTROL Check Out with Multiple Addresses]**.
1. 为每个数量选择单独的地址，下订单，然后完成结帐流程。
1. 观察管理员的订单总额并查看应用的折扣。
1. 使用其他优惠券再次下订单。
1. 运行 `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` 命令更新优惠券代码用法。

<u>预期结果</u>：

正确的计数应显示在 **使用时间** 和 **已使用** 列替换为 **是** 值 **[!UICONTROL manage coupon]** 在 **[!UICONTROL cart price rule]** 在管理员中。

<u>实际结果</u>：

使用的优惠券代码计数不会在 **使用时间** 列中，并且 **已使用** 列显示 *否* 值（如果下单时带有多个送货地址）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
