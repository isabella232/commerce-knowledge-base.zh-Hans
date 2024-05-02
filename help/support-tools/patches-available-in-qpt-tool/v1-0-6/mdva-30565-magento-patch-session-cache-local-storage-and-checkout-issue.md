---
title: 'MDVA-30565：会话缓存本地存储和签出问题'
description: MDVA-30565修补程序解决了会话缓存本地存储和签出问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565：会话缓存本地存储和签出问题

MDVA-30565修补程序解决了会话缓存本地存储和签出问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.6。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当客户会话超时时，购物车页面上仍可以看到购物车项目。 这会导致估算配送方式错误，导致没有配送方式可用于访客结帐。

<u>重现问题的步骤</u>：

1. 在Commerce管理员中启用持久性购物车。 (**启用持久性** = &quot;*是*&quot;)
1. 以前端客户的身份登录。 这将创建 `persistent_shopping_cart` cookie并启动永久会话。
1. 将产品添加到购物车。
1. 等待前端会话超时，或删除 `PHPSESSID` Cookie。
1. 现在您是访客用户，但如果您转到购物车，您仍然可以看到已添加为登录客户的产品。
1. 从购物车中删除产品，现在购物车是空的。 您可以看到Adobe Commerce删除了 `persistent_shopping_cart` 此事件中的Cookie。
1. 将新产品添加到购物车，然后转到购物车页面。
1. 现在，在浏览器控制台中，它显示 `V1/guest-carts/4/estimate-shipping-methods` 请求现在返回带有消息的404响应 `{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>预期结果</u>：

预估配送方式请求返回正确结果。

<u>实际结果</u>：

估计配送方式请求失败，并出现错误，如“*抱歉，目前此订单没有报价。*&quot;

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
