---
title: 'MDVA-38827：客户通过电子邮件收到订单发运错误'
description: “MDVA-38827修补程序修复了客户收到包含以下错误消息的订单发送电子邮件问题：*很抱歉，生成此内容时出错*。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.0后，即可使用此修补程序。 修补程序ID为MDVA-38827。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。”
exl-id: f2e5aeab-7d46-46be-9631-c3a863d9bf52
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-38827：客户通过电子邮件收到订单发运错误

MDVA-38827修补程序修复了客户收到包含以下错误消息的订单发运电子邮件的问题： *很抱歉，生成此内容时出错*. 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.1.0。 修补程序ID为MDVA-38827。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果选择了发运的“通过电子邮件通知客户”选项，客户将收到一封包含以下错误消息的电子邮件： *很抱歉，生成此内容时出错*.

<u>重现问题的步骤</u>：

1. 转到 **营销** > **通信** > **电子邮件模板** 并选择 **添加新模板**.
   * 选择 **Magento销售额** > **新建装运**.
   * 单击 **加载模板**.
   * 添加模板名称（例如，核心发运模板）并单击 **保存**.
1. 转到 **存储** >设置> **配置** > **销售** > **销售电子邮件**：
   * 启用 **装运注释**.
   * 选择 **核心配送模板** (请参阅“Shipment Comment Email Template”和“Shipment Comment Email Template for Guest”中的“Add a template name”部分（步骤1）。
1. 下订单。 转到“管理”面板> **销售** > **订购**，单击 **视图**，然后发送订单。
1. 订单状态将从“待处理”更改为“正在处理”。
1. 单击 **装运** 左侧边栏菜单上，然后单击 **视图** 查看订单。
1. 在中添加评论 **评论文本** 以下 **装运历史记录** 并选中复选框 **通过电子邮件通知客户**.
1. 单击 **提交评论**.

<u>预期结果</u>：

生成包含装运注释的销售电子邮件。

<u>实际结果</u>：

电子邮件中收到以下错误消息： *很抱歉，生成此内容时出错。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
