---
title: 'MDVA-35984：同一产品的并发装运中的产品数量错误'
description: MDVA-35984修补程序修复了在为同一产品创建多个并发发运时产品数量(Qty)不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21后，即可使用此修补程序。 修补程序ID为MDVA-35984。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: b15e25e1-c451-4350-950d-ae4893835e54
feature: Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-35984：相同产品的并发装运中的产品数量错误

MDVA-35984修补程序修复了在为同一产品创建多个并发发运时产品数量(Qty)不正确的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.21。 修补程序ID为MDVA-35984。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 使用以下方式创建简单产品 **数量** = *100*.
1. 使用此产品创建两个订单。
1. 进行并发API调用以创建两个订单的发运，如以下示例所示：

   ```php
   POST <host>/rest/<store_code>/V1/order/3/ship    ```    where **order id** = *3* , with a payload like:    ```php    {        "items": [            {                "order_item_id": <order_item_id>,                "qty": 1            }        ],        "tracks": [            {                "track_number": "1Y-9876543210",                "title": "United Parcel Service",                "carrier_code": "ups"            }        ]    }
   ```

1. 在管理网格中检查产品数量。

<u>预期结果</u>：

结果是产品 **数量** = *98* 在两次装运后。

<u>实际结果</u>：

结果是产品 **数量** = *99* 在两次装运后。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
