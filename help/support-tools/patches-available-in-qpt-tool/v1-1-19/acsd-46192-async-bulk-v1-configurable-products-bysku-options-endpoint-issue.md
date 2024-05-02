---
title: 'ACSD-46192：异步/bulk/V1/configurable-products/bySku/options端点问题'
description: ACSD-46192修补程序修复了“async/bulk/V1/configurable-products/bySku/options”端点的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19后，即可使用此修补程序。 修补程序ID为ACSD-46192。 请注意，Adobe Commerce 2.4.5中已修复此问题。
exl-id: fed49708-868a-48ec-8dbc-638d75506a40
feature: Configuration, Products
role: Admin
source-git-commit: 6c04285321879dae82fe3c5aa04f165fdba42bbd
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46192：异步/bulk/V1/configurable-products/bySku/options端点问题

ACSD-46192修补程序修复了 `async/bulk/V1/configurable-products/bySku/options` 端点。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.19。 修补程序ID为ACSD-46192。 请注意，Adobe Commerce 2.4.5中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.3.6 - 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3和2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将POST请求发送到时出现错误 `async/bulk/V1/configurable-products/bySku/`.

<u>重现问题的步骤</u>：

1. 发送POST请求到 `async/bulk/V1/configurable-products/bySku/`.

```JSON
[{
  "sku": "MS-Champ",
  "option": {
    "attribute_id": "141",
    "label": "Size",
    "position": 0,
    "is_use_default": true,
    "values": [
      {
        "value_index": 9
      }
    ]
  }
}]
```

<u>预期结果</u>：

没有错误。 您将获得以下响应：

```JSON
{
  "bulk_uuid": "e5a94361-e16e-432b-a000-c1351a0d01b3",
  "request_items": [
    {
      "id": 0,
      "data_hash": "3e7369ffc0a1602c1f25601a2e11b130f65fd01e68b5091ad746d0cac5b7f35d",
      "status": "accepted"
    }
  ],
  "errors": false
}
```

<u>实际结果</u>：

出现以下错误：

```PHP
TypeError: Argument 3 passed to Magento\Framework\Webapi\ServiceInputProcessor::process() must be of the type array, string given, called in /var/www/html/vendor/magento/module-webapi-async/Controller/Rest/Asynchronous/InputParamsResolver.php on line 154 and defined in /var/www/html/vendor/magento/framework/Webapi/ServiceInputProcessor.php:172
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
