---
title: 'MDVA-43232：按特殊价格对可视化促销器中的产品进行排名靠前（或靠下）排序会导致错误'
description: MDVA-43232修补程序修复了在保存类别时，按特价到顶部（或底部）对可视化促销器中的产品进行排序而导致错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43232。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: e958a219-5e93-4ae4-94cb-f478f82ad060
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-43232：按特殊价格到顶部（或底部）对可视化促销器中的产品进行排序会导致错误

MDVA-43232修补程序修复了在保存类别时，按特价到顶部（或底部）对可视化促销器中的产品进行排序而导致错误的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.12。 修补程序ID为MDVA-43232。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在可视化促销器中按“特殊价格”到“顶部”（或“底部”）对产品进行排序时，会导致在保存类别时出错。

<u>重现问题的步骤</u>：

1. 确保有两个网站。
1. 导航到 **商店** > **配置** > **目录** > **价格** 设置目录价格范围=网站。
1. 再次，导航到 **商店** > **配置** > **目录** > **Visual Merchandiser** > **类别规则的可见属性** >并添加特价。
1. 创建一个简单的产品，并将这些产品分配给两个网站。
1. 向产品的默认范围添加特殊价格。
1. 切换到其他商店的范围并覆盖该产品的“价格”和“特殊价格”。
1. 执行 `catalog_product_price` 重新索引。
1. 转到 **目录** > **类别** 并创建新类别。
1. 添加类别规则以筛选具有特殊价格的产品。
1. 保存类别。
1. 在“类别中的产品”部分下，将排序顺序=特殊价格设置为顶部（或底部）。
1. 再次保存类别。

<u>预期结果</u>：

类别保存时没有出现错误。

<u>实际结果</u>：

引发异常：

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
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
