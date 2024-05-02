---
title: 'MDVA-32694修补程序：将产品添加到报价时出现问题'
description: MDVA-32694修补程序解决了无法在管理员中将有效产品添加到非默认网站上创建的可转让报价的问题。
exl-id: 964abbbd-c8b1-4645-a393-7283f52e94ff
feature: Products, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-32694修补程序：将产品添加到报价时出现问题

MDVA-32694修补程序解决了无法在管理员中将有效产品添加到非默认网站上创建的可转让报价的问题。

此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.14。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构2.3.2上的Adobe Commerce （带B2B版本1.2）

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.3.5-p2、2.4.0、2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

使用B2B安装新的Adobe Commerce实例。

<u>重现问题的步骤</u>：

1. 转到 **存储>配置>常规> B2B功能** 并启用 **公司** 和 **B2B报价**.
1. 使用以下方式再创建2个网站 **存储** 和 **预览** (您总共应有3个网站： *基础*， *website2*， *website3*)。
1. 创建简单产品并仅将其分配给 *website3*.
1. 转到 **商店>所有商店** 并设置 *website3* 作为 **默认**.
1. 前往前端并在以下位置创建新公司： *website3*.
1. 将之前创建的产品添加到购物车中，并创建一个新的可转让报价。
1. 转到 **商店>所有商店** 并设置“*基础*”网站恢复为 **默认**.
1. 转到 **SALES > Quotes > Open created earther quotes** 并尝试向其中添加相同的产品。

<u>预期结果</u>：

管理员用户可以按预期将同一产品添加到报价中。

<u>实际结果</u>：

Admin用户无法将相同的产品添加到报价中，此时将显示以下错误消息：

```php
This product is assigned to another website.
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
