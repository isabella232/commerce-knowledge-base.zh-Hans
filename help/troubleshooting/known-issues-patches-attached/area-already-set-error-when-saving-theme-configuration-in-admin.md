---
title: '在Admin中保存主题配置时出现“区域已设置”错误'
description: 本文为云基础架构2.2.4上已知的Adobe Commerce提供一个修补程序，该问题与在Commerce管理员中尝试设置默认存储视图的主题时出现*“区域已设置”*错误消息相关。
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 在Admin中保存主题配置时出现“区域已设置”错误

本文为云基础架构2.2.4中已知的Adobe Commerce提供一个修补程序，该修补程序与获取 *“区域已设置”* 尝试在Commerce管理员中设置默认商店视图的主题时出现错误消息。

## 问题

您获得“ *保存此配置时出错：区域已设置* 尝试为默认存储视图设置主题时显示“ ”错误消息。

<u>重现问题的步骤</u>：

1. 登录到Commerce管理员。
1. 导航到 **内容** > **设计** > **配置**.
1. 将配置范围设置为 *默认存储视图*.
1. 更改 **应用的主题** 下拉菜单。 例如，从 *Luma* 到 *空白。*
1. 单击 **保存配置**.

<u>预期结果</u>：所选主题应用于默认商店视图。

<u>实际结果</u> ：未应用主题，因此 *“保存此配置时出错：区域已设置”* 将显示错误消息。

## Patch

该修补程序已附加到本文。 要下载它，请单击以下链接或向下滚动到文章末尾，然后单击附加的文件：

[下载MDVA-11106\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.2.4

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce 2.0.X
* 云基础架构上的Adobe Commerce 2.1.X
* 云基础架构上的Adobe Commerce 2.2.0 - 2.2.5
* Adobe Commerce内部部署2.0.X
* Adobe Commerce内部部署2.1.X
* Adobe Commerce内部部署2.2.0 - 2.2.5

## 如何应用修补程序

有关说明，请参阅 [如何应用Adobe提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我们的支持知识库中。

## 附加文件
