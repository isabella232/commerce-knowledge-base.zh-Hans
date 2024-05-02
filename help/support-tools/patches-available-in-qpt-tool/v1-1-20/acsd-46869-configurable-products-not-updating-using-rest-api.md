---
title: 'ACSD-46869：可配置产品未在签出时使用REST API进行更新'
description: ACSD-46869修补程序修复了可配置产品在签出时未使用REST API进行更新的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20后，即可使用此修补程序。 修补程序ID为ACSD-46869。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869：可配置产品未在签出时使用REST API进行更新

ACSD-46869修补程序修复了可配置产品在签出时未使用REST API进行更新的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.20。 修补程序ID为ACSD-46869。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL QPT] 登陆页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在签出期间，不会使用REST API更新可配置产品。

<u>重现问题的步骤</u>：

1. 创建具有颜色和大小属性的可配置产品。
1. 选择 **[!UICONTROL Options]** 并将产品添加到购物车。
1. 转到 **[!UICONTROL Checkout]**，除数量外多次更新大小，并检查请求和响应。
1. 更新大小时，您会获得以下响应。

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>预期结果</u>：

根据更改更新值。

<u>实际结果</u>：

`option_value` 不会更新，因此下达订单时，其大小值为旧值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tools] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在“Quality Patches Tool（质量修补程序工具）”指南中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) 在我们的支持知识库中。

有关中可用的其他修补程序的信息 [!DNL QPT]，请参阅 [中提供的修补程序 [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在“Quality Patches Tool（质量修补程序工具）”指南中。
