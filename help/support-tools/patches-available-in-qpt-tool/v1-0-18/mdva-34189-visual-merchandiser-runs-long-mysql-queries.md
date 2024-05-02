---
title: 'MDVA-34189：可视化促销程序运行长MySQL查询'
description: MDVA-34189修补程序解决了在加载“管理类别”页面时Adobe Commerce执行大型可视化促销器查询的问题。
exl-id: 94143d80-3240-4a18-890d-fb759ea9c30d
feature: Categories, Merchandising, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-34189：可视化促销程序运行长MySQL查询

MDVA-34189修补程序解决了在加载“管理类别”页面时Adobe Commerce执行大型可视化促销器查询的问题。

此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.18。 修补程序ID为MDVA-34189。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.4-2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

网站在生产服务器上运行大型MySQL查询。

<u>重现问题的步骤</u>：

1. 要访问Visual Merchandiser，请访问 *管理员* 侧栏，单击 **目录** > **类别**.
1. 加载 **类别** 页面（初始根类别加载）并观察它执行的查询。

<u>预期结果</u>：

管理员 **类别** 页面应加载而不生成较慢查询。

<u>实际结果</u>：

这取决于您的PHP配置。 此错误最常见的示例是 **类别** 页面未打开并出现错误 *错误503第一字节超时* 显示。

或者，当Adobe Commerce加载Visual Merchandiser时，它会执行缓慢的MySQL查询。 此查询包含许多插入到的产品ID `ORDER BY FIELD(`e`.`entity_id`,  ...)`

在 `app/code/Magento/VisualMerchandiser/Model/Category/Products.php:: applyPositions`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
