---
title: 导入同名产品的CSV产品信息失败
description: 本文提供了一个已知的Adobe Commerce 2.2.3问题的修补程序，该问题与尝试导入包含产品信息的“.csv”文件（如果存在具有相同名称的产品）时出现错误有关。
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 导入同名产品的CSV产品信息失败

针对在尝试导入时出现的与获取错误相关的已知Adobe Commerce 2.2.3问题，本文提供了一个修补程序 `.csv` 包含产品信息的文件（如果存在具有相同名称的产品）。

## 问题

当 `.csv` 导入了包含产品信息的文件，并且存在具有相同名称的产品，则在“检查数据”步骤中会收到以下错误： *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. 导入期间重写产品的URL会导致此问题，即使导入的产品中没有产品URL列 `.csv` 文件。

<u>重现问题的步骤</u>：

1. 在Commerce管理员中创建两个具有相同名称的可配置产品。
1. 创建 `.csv` 文件，用于导入这些产品的数据，例如，包含以下列： `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. 转到 **系统** > **数据传输** > **导入** 并选择 `.csv` 文件。
1. 单击 **检查数据**.

<u>预期结果</u>：

没有发现问题；您可以导入 `.csv` 文件成功。

<u>实际结果</u>：

将显示以下错误消息： *“已为SKU为%sku%的项目生成URL密钥XYZ”*&#x200B;时，无法导入文件。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[下载MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* Adobe Commerce内部部署2.2.3

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce从2.2.0到2.2.7和2.3.0
* 从2.2.0到2.2.2、从2.2.4到2.2.7以及2.3.0的Adobe Commerce内部部署

## 如何应用修补程序

请参阅 [如何应用Adobe Commerce提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 在我们的支持知识库中获取说明。

## 有用的链接

[在云基础架构上将自定义修补程序应用到Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## 附加文件
