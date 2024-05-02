---
title: 'MDVA-38799：创建暂存更新后未保存可下载的产品'
description: MDVA-38799修补程序解决了创建暂存更新后无法保存可下载产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0后，即可使用此修补程序。 修补程序ID为MDVA-38799。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799：创建暂存更新后未保存可下载的产品

MDVA-38799修补程序解决了创建暂存更新后无法保存可下载产品的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.0。 修补程序ID为MDVA-38799。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

创建暂存更新后未保存可下载的产品。 用户将收到以下错误消息： *可下载的示例与产品无关。 请验证链接并重试*.

<u>重现问题的步骤</u>：

1. 导航到 **目录** > **产品**.
1. 单击“Add Product（添加产品）”旁边的下拉菜单并选择“Downloadable Product（可下载产品）”。
   * 填写产品的名称、SKU、价格和数量。
1. 向下滚动至可下载信息页面。
1. 在示例下，单击 **添加链接**.
   * 填写标题、上传文件（文件类型无关紧要）。
1. 单击 **保存**. 您将收到以下消息： *您已保存产品*.
1. 单击 **计划新更新** 页面顶部的。
   * 填写更新名称以及合法的开始日期和结束日期。
1. 单击 **保存** 在暂存更新时。
1. 单击 **保存** 在产品上。

<u>预期结果</u>：

保存产品时不会出现任何错误。

<u>实际结果</u>：

您会收到以下错误消息： *可下载的示例与产品无关。 请验证链接并重试*.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
