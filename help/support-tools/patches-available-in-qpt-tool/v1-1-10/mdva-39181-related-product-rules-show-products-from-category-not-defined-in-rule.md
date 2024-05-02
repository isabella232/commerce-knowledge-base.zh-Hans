---
title: 'MDVA-39181：相关产品规则显示规则中未定义类别中的产品'
description: MDVA-39181修补程序解决了相关产品规则显示规则中未定义类别中的产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10后，即可使用此修补程序。 修补程序ID为MDVA-39181。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181：相关产品规则显示规则中未定义类别中的产品

MDVA-39181修补程序解决了相关产品规则显示规则中未定义类别中的产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.10。 修补程序ID为MDVA-39181。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

相关产品规则显示规则中未定义类别的产品。

<u>先决条件</u>：

安装示例数据。

<u>重现问题的步骤</u>：

1. 创建属性品牌并将其添加到 **Tops属性集**.
1. 选择 **乔西**， **奥古斯塔**、和 **英格丽** 要添加到品牌猫的夹克，来自 **女性** > **顶部** > **夹克类别**.
1. 选择 **博蒙**， **Hyperion**、和 **克诺比** 要添加到品牌猫的夹克，来自 **男子** > **顶部** > **夹克类别**.
1. 使用以下方式创建相关产品：

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * 要匹配的产品：

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * 要显示的产品：

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. 从前端打开SKU WJ04并检查相关产品。
1. 更新类别ID **女性** > **顶部** > **夹克** 万一它与此不同。

<u>预期结果</u>：

只有相同品牌和相同子类别的产品才会显示在相关产品中。

<u>实际结果</u>：

相关产品显示的是同一品牌，但来自随机父类别。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
