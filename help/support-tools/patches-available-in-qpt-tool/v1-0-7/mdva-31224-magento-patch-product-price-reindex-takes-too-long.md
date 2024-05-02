---
title: 'MDVA-31224修补程序：产品价格重新指数耗时过长'
description: MDVA-31224修补程序解决了产品价格重新指数需要很长时间才能完成或永远不会完成的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7后，即可使用此修补程序。
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# MDVA-31224修补程序：产品价格重新指数耗时过长

MDVA-31224修补程序解决了产品价格重新指数需要很长时间才能完成或永远不会完成的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装v.1.0.7。

## 受影响的产品和版本

* 该补丁是为Cloud Infrastructure 2.3.3上的Adobe Commerce设计的。
* 该补丁还兼容本地Adobe Commerce和Cloud Infrastructure 2.3.3 - 2.3.4-p2上的Adobe Commerce。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品价格重新指数需要很长时间才能完成，或者永远不会完成。

<u>重现问题的步骤：</u>

1. 创建包含15个选项的6000个捆绑产品。
1. 创建包含30个选项的1个捆绑产品。
1. 从CLI运行价格重新索引：     `bin/magento indexer:reindex catalog_product_price`

<u>预期结果：</u>

完成产品价格重新索引需要1.5小时或更长时间。

<u>实际结果：</u>

产品价格重新索引需要很短时间（一两分钟）才能完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
