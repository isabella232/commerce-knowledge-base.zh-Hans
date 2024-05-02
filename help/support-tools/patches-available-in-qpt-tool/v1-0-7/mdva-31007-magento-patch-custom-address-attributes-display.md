---
title: 'MDVA-31007：自定义地址属性显示'
description: MDVA-31007修补程序解决了自定义地址属性在“我的帐户”区域和后端(在**Sales &gt； Orders**位置)的订单详细信息页面中无法正确显示的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007：自定义地址属性显示

MDVA-31007修补程序解决了在“我的帐户”区域和后端(位于 **销售>订单** 位置)。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.7。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 登录到Admin后端。
1. 导航到 **商店** > **属性** > **客户地址**.
1. 创建两个属性：

   * 设置输入类型： *下拉面板*.
   * 设置输入类型： *文本*.

1. 导航到 **商店** > **配置** > **客户** > **客户配置**.
1. 选择 *范围* 作为 **默认存储** 视图。
1. 展开 **地址模板** 部分。 更新 *文本*， *文本一行*、和 *HTML* 要包含上述两个自定义属性，请执行以下操作：

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. 打开店面。
1. 创建用户并使用其登录。
1. 转到 **我的帐户** > **通讯簿**，并添加新地址（填写两个自定义属性）。
1. 将产品添加到购物车，然后下订单。
1. 在订单成功页面上，单击 **订单号** 链接。
1. 在订单详情页面上，观察 **订单信息** 部分。
1. 转到 **后端** > **销售** > **订购**，单击上面的顺序，然后观察 **地址信息** 部分。

<u>预期结果</u>：

在前端和后端上，帐单地址和送货地址均按预期显示。

<u>实际结果</u>：

在前端和后端上，计费地址显示不正确。 下拉属性的选定选项缺失，且输入属性的值包含属性代码。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
