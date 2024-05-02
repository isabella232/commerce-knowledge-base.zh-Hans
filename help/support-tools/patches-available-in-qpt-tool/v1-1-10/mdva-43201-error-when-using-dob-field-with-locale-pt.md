---
title: 'MDVA-43201：使用具有区域设置PT的DOB字段时出错'
description: MDVA-43201修补程序解决了在客户注册表中使用葡萄牙语言环境的DOB客户属性时出现错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10后，即可使用此修补程序。 修补程序ID为MDVA-43201。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201：使用具有区域设置PT的DOB字段时出错

MDVA-43201修补程序解决了在客户注册表中使用葡萄牙语言环境的DOB客户属性时出现错误的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.10。 修补程序ID为MDVA-43201。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在将DOB客户属性添加到葡萄牙语言环境的客户注册表单时，该表单会给出错误 *传递给iterator_to_array()的参数1必须实现接口可遍历，给定null*.

<u>先决条件</u>：

已安装B2B模块。

<u>重现问题的步骤</u>：

1. 转到管理员> **商店** > **配置** > **常规** > **区域设置选项**，将区域设置设置为 **葡萄牙语（葡萄牙）** 并单击 **保存**.
1. 重新索引并清除缓存。
1. 转到 **商店** > **属性** > **客户**.
1. 打开DOB客户属性和集 **在店面显示** 到 **是**.
1. 从中选择全部 **要使用的表单**.
1. 保存属性。
1. 转到前端的“创建新帐户”页面。

<u>预期结果</u>：

葡萄牙商店的客户注册表在添加DOB属性时没有给出错误。

<u>实际结果</u>：

葡萄牙商店的客户注册表单在添加DOB属性时出错。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
