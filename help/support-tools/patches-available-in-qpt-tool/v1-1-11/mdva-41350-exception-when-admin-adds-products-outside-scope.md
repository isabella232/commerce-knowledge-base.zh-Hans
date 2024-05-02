---
title: 'MDVA-41350：当管理员将产品添加到其访问权限之外时会出现异常'
description: MDVA-41350修补程序修复了在管理员用户按其访问范围以外的SKU的顺序添加产品时引发异常错误而不是限制访问通知的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11后，即可使用此修补程序。 修补程序ID为MDVA-41350。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350：当管理员将产品添加到其访问权限之外时会出现异常

MDVA-41350修补程序修复了在管理员用户按其访问范围以外的SKU的顺序添加产品时引发异常错误而不是限制访问通知的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.11。 修补程序ID为MDVA-41350。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.3.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当具有受限访问权限的管理员用户按SKU在订单中超出其访问权限添加产品时，会发生异常，而不是出现消息通知用户其有限访问权限。

<u>重现问题的步骤</u>：

1. 以仅有权访问特定网站的用户身份登录管理员。
1. 转到 **销售** > **订购** 并单击 **创建新订单**.
1. 选择客户和商店视图。
1. 单击 **按SKU添加产品**.
1. 搜索未分配给任何网站或未分配给您有权访问的网站的SKU。
1. 单击 **添加到订单**.

<u>预期结果</u>：

将显示相应的错误消息。

<u>实际结果</u>：

出现异常。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
