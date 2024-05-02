---
title: 'MDVA-12304：存储前端出现503错误和Cookie错误'
description: 此MDVA-12304 Adobe Commerce修补程序解决了存储前端的503错误，其中*无法发送Cookie。 将超出Cookie的最大数量。*日志中出现错误消息。 这是一个已知的Adobe Commerce 2.2.5问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12后，即可使用此修补程序。
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304：存储前端出现503错误和Cookie错误

此MDVA-12304 Adobe Commerce修补程序使用以下软件解决了存储前端的503错误： *无法发送Cookie。 将超出Cookie的最大数量。* 日志中的错误消息。 这是一个已知的Adobe Commerce 2.2.5问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.12。

## 受影响的产品和版本

* **该修补程序是为Adobe Commerce版本创建的：** Adobe Commerce内部部署2.2.5。
* **与Adobe Commerce版本兼容：** Adobe Commerce（所有部署方法）2.x.x。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户在商店前面导航时遇到503错误。 在 `var/log/exception.log` 文件出现以下错误消息 *无法发送Cookie。 将超出Cookie的最大数量。*

出现此问题的原因是Adobe Commerce的默认Cookie限制设置为50，而如果客户端的浏览器达到此限制，则Commerce会引发异常。 补丁中提供的解决方案将Cookie限制增加到200。

<u>重现问题的步骤：</u>

客户尝试登录并查看购物车时，随时都会显示503错误。

在 `var/log/exception.log` 文件出现以下错误消息 *无法发送Cookie。 将超出Cookie的最大数量。*

<u>实际结果：</u> 客户无法检查购物车或完成订单。

<u>预期结果：</u> 客户可以检查其购物车并完成订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。


## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
