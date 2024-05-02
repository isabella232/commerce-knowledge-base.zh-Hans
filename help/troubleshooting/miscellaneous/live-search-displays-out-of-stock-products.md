---
title: ’[!DNL Live Search] 无论管理员中的库存状态设置如何，都会显示缺货产品
description: 本文提供有关产品列表页面(PLP)显示*我们找不到与所选内容匹配的产品*错误，而搜索弹出窗口返回某些项目的已知问题的信息。
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] 无论管理员中的库存状态设置如何，都会显示缺货产品

>[!IMPORTANT]
>
>此问题已在中修复 [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). 要安装最新版本，请参阅 [正在更新 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) （在用户指南中）。

本文介绍了产品列表页(PLP)中显示的已知问题。 *找不到与所选内容匹配的产品* 搜索弹出框返回某些项目时出错。

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.x

## 问题

[!DNL Live Search] 无论Adobe Commerce管理员中的库存状态设置如何，都会显示搜索结果。 即使 **[!UICONTROL Display Out-of-Stock Products]** 设置为 *否*，则会显示产品。 这会导致PLP错误 *找不到与所选内容匹配的产品*.

<u>重现问题的步骤</u>：

1. 创建类别、添加产品。 (例如：类别= _牛仔裤_，产品1 = _蓝色牛仔裤_，产品2 = _黑色牛仔裤_)
1. 使类别中的所有产品缺货。
1. 设置 **[!UICONTROL Display Out-of-Stock Products]** 到 *否*.
1. 在店面，进入 *牛仔裤* 在搜索字段中。
1. 单击 **[!UICONTROL View All]** 在弹出窗口中。

<u>预期结果</u>：

您会看到 *找不到与所选内容匹配的产品* PLP上出现消息，并且搜索弹出窗口中不显示任何产品。

<u>实际结果</u>：

您会看到 *找不到与所选内容匹配的产品* PLP上的消息，并且这两个产品都会显示在搜索弹出窗口中。

## 解决方案

目前此问题无解决方法。 我们的 [!DNL Live Search] 团队很快将提供要配置的设置 [!DNL Live Search] 以正确显示产品。

## 相关阅读

[安装 [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) 在我们的用户指南中。
