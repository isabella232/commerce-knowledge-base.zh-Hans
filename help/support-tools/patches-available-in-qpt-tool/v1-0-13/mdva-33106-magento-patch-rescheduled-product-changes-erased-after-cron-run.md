---
title: 'MDVA-33106修补程序：重新计划的产品更改在cron运行后被清除'
description: MDVA-33106修补程序修复了在cron之后擦除重新计划的产品更改的问题
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-33106修补程序：重新计划的产品更改在cron运行后被清除

MDVA-33106修补程序修复了在cron之后擦除重新计划的产品更改的问题

```bash
bin/magento cron:run
```

命令被执行。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.13。 请注意，该问题计划在Adobe Commerce 2.4.2中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 在Commerce Admin中，转到 **目录** > **产品** 并单击“编辑”。 请注意 **价格** 值，例如 *9.99*.
1. 单击 **计划新更新** 并填写详细信息：
   * 更新名称不重要。
   * 将日期设置为将来的时间，+1年作为开始日期和结束日期。
   * 将价格设置为 *1.99*.
   * 保存更改。
1. 转到内容暂存仪表板，然后选择网格视图以查看上面是否安排了匹配。
1. 选择计划更新旁边的编辑操作。 数据仍应与上方的匹配。
1. 将计划日期更改为更近的时间。 请将其更改为+ 1周或+ 1个月，而不是从现在起+1年。
1. 保存更改并检查日期是否已在暂存功能板上更新。
1. 等待cron作业运行。
1. 在计划的更改中再次单击编辑并检查价格。

<u>预期结果</u>：

价格是1.99。

<u>实际结果</u>：

价格是9.99。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
