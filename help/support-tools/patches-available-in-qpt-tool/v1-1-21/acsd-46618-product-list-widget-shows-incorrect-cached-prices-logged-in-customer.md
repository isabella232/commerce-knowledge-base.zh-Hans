---
title: “ACSD-46618：产品列表构件显示登录客户的错误缓存价格”
description: 应用补丁以修复Adobe Commerce问题，该问题导致产品列表构件为登录客户显示不正确的缓存价格。
exl-id: 8b182822-1d3d-4793-871b-cdf4565d0712
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46618：产品列表构件显示已登录客户的不正确缓存价格

ACSD-46618修补程序解决了产品列表构件为已登录的客户显示不正确的缓存价格的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 已安装1.1.21。 修补程序ID为ACSD-46618。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**
* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

ACSD-46618修补程序解决了产品列表构件为已登录的客户显示不正确的缓存价格的问题。

<u>重现问题的步骤</u>：

1. 在Adobe Commerce管理员中，选择 **[!UICONTROL Stores]**，则 **[!UICONTROL Configuration]**，展开 **[!UICONTROL Sales]**，并选择 **[!UICONTROL Tax]**. 更新税设置以显示含税和不含税的价格。
1. 设置 **[!UICONTROL Enable Cross Border Trade]** = _是_.
1. 创建一个仅适用于美国的税则。
1. 向主页添加一个包含多个产品的构件。
1. 创建两个具有美国地址和非美国地址的客户。
1. 从店面使用美国客户登录。 确保已缓存页面。
1. 观察主页小部件中显示的价格。
1. 注销并使用非美国客户登录。

<u>预期结果</u>：

主页小组件中显示的价格对应于客户的地址。

<u>实际结果</u>：

主页小组件显示针对非美国客户使用该税的价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
