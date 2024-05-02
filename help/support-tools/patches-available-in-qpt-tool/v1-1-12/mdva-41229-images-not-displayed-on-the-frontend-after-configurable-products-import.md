---
title: 'MDVA-41229：可配置产品导入后，前端未显示后端可用的图像'
description: MDVA-41229修补程序解决了导入可配置产品后，前端上未显示后端可用图像的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-41229。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 69d7374f-9f8b-4ec4-8a7f-135ee06135a3
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 2%

---

# MDVA-41229：可配置产品导入后，前端不显示后端可用的图像

MDVA-41229修补程序解决了导入可配置产品后，前端上未显示后端可用图像的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.12。 修补程序ID为MDVA-41229。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法）2.3.2-p2和2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可配置产品导入后，前端上可用的图像不会显示在前端上。

<u>重现问题的步骤</u>：

1. 安装干净的Adobe Commerce。
1. 通过转到 **商店** > **属性** > **产品** > **添加新属性** 具有以下设置：
   * 属性：
      * 属性属性：
         * 默认标签：设置大小
         * 商店所有者的目录输入类型：文本样本
         * 所需值：否
         * 更新产品预览图像：是
      * 管理样本（属性的值）：

        | 默认 | 管理员样本 | 管理员描述 | 默认商店视图样本 | 默认商店视图说明 |
        |---|---|---|---|---|
        | 否 | 4 | 4 | 4 | 4 |
        | 否 | 24 | 24 | 24 | 24 |
        | 否 | 30 | 30 | 30 | 30 |
        | 否 | 60 | 60 | 60 | 60 |
        | 否 | 68 | 68 | 68 | 68 |
      * 高级属性属性：
         * 属性代码：set_size
         * 范围：全局
         * 唯一值：否
         * 存储所有者的输入验证：无
         * 添加到列选项：否
         * 在筛选器选项中使用：否
   * 管理标签：
      * 管理标题（大小、颜色等）
         * 默认存储视图：设置大小
   * 店面属性：
      * 在搜索中使用：是
      * 搜索权重：1
      * 在高级搜索中可见：否
      * Storefront上的比较：是
      * 在分层导航中使用：可筛选（包含结果）
      * 在搜索结果分层导航中使用：是
      * 用于促销规则条件：否
      * 在店面的目录页面上可见：是
      * 在产品列表中使用：是
      * 用于产品清单中的排序：否
1. 将此属性添加到产品详细信息组中的默认属性集(**商店** > **属性** > **属性集**)。
1. 将图像集下载到Adobe Commerce根目录内的var文件夹中。
1. 转到 **系统** > **数据传输** >并使用以下选项导入文件：
   * 导入设置：
      * 实体类型：产品
   * 导入行为：
      * 导入行为：添加/更新
      * 验证策略：出错时停止
      * 允许的错误数： 1
      * 字段分隔符： `;`
      * 多值分隔符： `,`
      * 属性值常量：EMPTYVALUE
      * 字段存储模块：未选中
   * 要导入的文件：
      * 选择要导入的文件
      * 图像文件目录：将其留空
1. 转到店面 `/product-set.html` 分页并在不同的集大小之间切换。 对于“设置大小24”，将没有图库。

<u>预期结果</u>：

可配置产品中所有简单产品的图库会与所有相关图像一起显示。

<u>实际结果</u>：

产品没有图库。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
