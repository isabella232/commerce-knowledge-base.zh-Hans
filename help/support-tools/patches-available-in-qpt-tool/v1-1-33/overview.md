---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.33`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.33。
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 概述： [!DNL Quality Patches Tool] (QPT) v1.1.33

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.33。

QPT v1.1.33包含以下修补程序：

1. **ACSD-50478**：针对数据库转储包含触发器和分隔符SQL命令的情况修复数据库回退命令。
1. **ACSD-50512**：修复了错误： *可下载的链接与产品无关。 请验证链接并重试。*  在更新可下载产品暂存更新的开始日期时，会发生这种情况。
1. **ACSD-50949**：修复了中的价格过滤器问题 [!UICONTROL Advanced Search] 与SKU过滤器一起使用时，不会返回正确的结果。
1. **ACSD-51645**：修复了保存新文件时引发的错误 [!UICONTROL Cart Price Rule] 如果扩展 `Magento_OfflineShipping` 已禁用。
1. **ACSD-50895**：修复了以下问题： [!DNL Google Analytics] 3 GTM标记未触发，如果 [!DNL Google Analytics] 4 GTM未配置。
1. **ACSD-51102**：修复了在计划更新启用目录规则时，应用于大量产品的目录规则未正确编制索引的问题。
1. **ACSD-50368**：修复了客户的问题。 `group_id` 通过异步REST API或异步批量REST API创建客户时，忽略该参数。
1. **ACSD-51497**：修复了客户无法按对目录页面进行排序的问题 [!UICONTROL Custom Attribute] 下拉列表类型的。
1. **ACSD-51408**：修复了订单项目状态错误设置为的问题 [!UICONTROL Backordered].
1. **ACSD-51735**：修复了订单项目状态错误设置为的问题 [!UICONTROL Ordered] 当产品库存为 *0*.
1. **ACSD-51792**：修复了以下情况下页面没有展示事件的问题： [!DNL Google Tag Manager] 4已启用。
1. **ACSD-51471**：修复了以下问题：对于使用简单产品的捆绑产品，管理员用户无法保存其本身具有计划更新的计划更新。
1. **ACSD-51700**：修复了在管理员的可下载产品编辑页面上切换商店视图时发生的错误。
1. **ACSD-51120**：修复了包含通过暂存更新更新更新的CMS块的CMS页面未清除GraphQLGET缓存的问题。
1. **ACSD-51240**：修复了通过公司注册表单进行注册时上传的文件缺失的问题。
1. **ACSD-51907**：修复了受限管理员用户无法创建具有离线退款的贷项通知单的问题。
1. **ACSD-52148**：修复了 [!UICONTROL Google V3 reCAPTCHA Admin] 登录偶尔会失败。
1. **ACSD-51431**：修复了即使在更改日志中没有新条目时索引器状态也正常工作的问题。
1. **ACSD-51892**：修复了在部署期间配置文件加载多次的性能问题。

使用左侧的菜单导航到特定的修补程序页面。
