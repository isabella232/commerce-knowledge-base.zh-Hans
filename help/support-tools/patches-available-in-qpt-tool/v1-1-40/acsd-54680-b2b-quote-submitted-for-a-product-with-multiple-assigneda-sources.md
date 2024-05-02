---
title: 'ACSD-54680：无法处理具有多个已分配来源的产品的B2B报价'
description: 应用ACSD-54680修补程序以修复无法处理具有多个已分配来源的产品的B2B报价的Adobe Commerce问题。
feature: B2B
role: Admin, Developer
exl-id: 4d05714c-d32d-46f3-b857-81704c9e96cd
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-54680：无法处理具有多个已分配来源的产品的B2B报价。

ACSD-54680修补程序修复了无法处理具有多个已分配源的产品的B2B报价的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.40。 修补程序ID为ACSD-54680。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法处理具有多个已分配来源的产品的B2B报价。

<u>重现问题的步骤</u>：

1. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** 并创建两个新源： **源1** 和 **源2**.
1. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** 并创建新的Stock： **库存A**，将其分配到主网站，然后分配 **源1** 和 **源2** 敬它。
1. 创建简单产品，分配 **源1** 和 **源2**，并设置数量= *2* 每个源。 (产品的可销售数量应为 *4* 因此)。
1. 创建公司帐户。
1. 转到 **[!UICONTROL Storefront]** 并登录到公司帐户。
1. 将简单产品添加到购物车，数量为 *4*.
1. 打开 *[!UICONTROL Shopping cart]* 并单击 **[!UICONTROL Request a quote]** 按钮。
1. 添加注释和报价名称，然后单击 **[!UICONTROL Send a Request]** 按钮。
1. 转到 **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. 打开最近提交的报价。

<u>预期结果</u>：

引用项包含订购的产品。

<u>实际结果</u>：

引用页面中的项目部分为空，无法处理报价。
`var/log/system.log` 包含

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
