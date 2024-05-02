---
title: 'MDVA-39384：无法保存公司用户的自定义客户属性'
description: MDVA-39384修补程序解决了未保存公司用户的自定义客户属性的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39384。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384：无法保存公司用户的自定义客户属性

MDVA-39384修补程序解决了未保存公司用户的自定义客户属性的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.2。 修补程序ID为MDVA-39384。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.1 - 2.3.6、2.4.1 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

未保存公司用户的自定义客户属性。

<u>先决条件</u>：

已安装B2B模块。

<u>重现问题的步骤</u>：

1. 转到 **商店** >设置> **配置** > **B2B功能** 并设置 **启用公司** 更改为是。
1. 创建自定义客户属性：
   * 必需值：是（可选，启用该选项以显示验证错误）。
   * 在店面显示：是。
   * Forms在中使用：列表中的所有可用。
1. 创建公司并以公司管理员身份登录。
1. 导航到帐户中的公司结构。
1. 单击 **添加用户** 链接。
1. 填写包含自定义属性的表单。
1. 单击 **保存**.

<u>预期结果</u>：

自定义属性值会与新的公司用户一起保存。

<u>实际结果</u>：

自定义属性值不会与新的公司用户一起保存。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
