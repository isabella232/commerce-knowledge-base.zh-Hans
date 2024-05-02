---
title: “ACSD-51845：无法通过异步批量更新具有层价格和不同属性集的后续产品 [!DNL API]"
description: 应用ACSD-51845修补程序以修复Adobe Commerce问题，该问题导致无法通过异步批量更新具有层价格和其他属性集的后续产品 [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845：无法通过异步批量更新具有层价格和不同属性集的后续产品 [!DNL API]

ACSD-51845修补程序修复了无法通过异步批量更新具有层价格和不同属性集的后续产品的问题 [!DNL REST API]. 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.35。 修补程序ID为ACSD-51845。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过异步批量更新具有层价格和不同属性集的后续产品失败 [!DNL REST API].

<u>重现问题的步骤</u>：

1. 配置 [!DNL RabbitMQ].
1. 创建两个属性集。
1. 创建两个 **简单产品**，将每个产品分配给不同的属性集。
1. 添加 **客户组价格** 每个产品的。
1. 在同一批更新两个产品 [!DNL API] 更新。
1. 确保 `bin/magento queue:consumers:start async.operations.all` 命令正在运行。
1. 检查批量 [!DNL API] 状态。

<u>预期结果</u>：

服务执行成功。

<u>实际结果</u>：

系统返回错误消息： *无法保存产品。 请重试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
