---
title: “ACSD-46581：在购物车中选择国家/地区后，预计税额合计未更新”
description: 应用ACSD-46581补丁以解决在购物车中切换国家/地区后税率未更新的Adobe Commerce问题。
exl-id: 17334f7b-e5a2-4091-8196-eff80875c003
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-46581：在购物车中选择国家/地区后，预计税额合计未更新

此ACSD-46581补丁解决了在购物车中切换国家/地区后税率未更新的问题。 它仅在选择配送方式后更新。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.21。 修补程序ID为ACSD-46581。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.1-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在购物车中切换国家/地区后，税率不会更新。

<u>重现问题的步骤</u>：

1. 在Adobe Commerce Admin中，转到 **[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**.
1. 创建新的税率 **[!UICONTROL Country]** = _美国_， **[!UICONTROL State]** = _*_， **[!UICONTROL Rate]** = _8.25_.
1. 创建新的税率 **[!UICONTROL Country]** = _印度_， **[!UICONTROL State]** = _*_， **[!UICONTROL Rate]** = _10_.
1. 创建包含美国和印度税率的税则。
1. 转到 **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]** 并启用多种配送方式(_统一费率_ 和 _免费送货_ 例如)。
1. 创建简单的产品，使用 **[!UICONTROL Taxable Goods]** 税分类。
1. 将产品添加到商店前面的购物车。
1. 打开购物车并检查税额。
1. 将应用美国的默认税务设置，并按8.25%的税率计算税额。
1. 把国家换成印度。

<u>预期结果</u>：

将该国改用印度时，税率改为10%。

<u>实际结果</u>：

在购物车的总部分中，税额保持不变。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
