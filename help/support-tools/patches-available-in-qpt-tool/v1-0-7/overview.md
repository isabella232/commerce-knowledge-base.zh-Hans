---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.0.7`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.7。
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7概述

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.0.7。

QPT v1.0.7包含以下修补程序：

1. **MDVA-29148**：修复了通过API调用（的产品自定义属性）创建产品时的问题。 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如多选）如果有效负载中未提供值，则该类型不使用其默认值。
1. **MDVA-29389**：修复了高级报表的问题，其中 `analytics_collect_data` cronjob说： *必须在host参数（如localhost：3306）中配置端口*.
1. **MDVA-30594**：修复了在配置FPT时签出期间无法保存带多个地址的订单的问题。
1. **MDVA-30782**：修复了在不考虑购物车规则的情况下显示动态块的问题。
1. **MDVA-30815**：修复了当您更改搜索结果页面上应显示多少搜索结果时的问题。
1. **MDVA-30837**：为免运费计算添加配置选项，以便用户能够配置最低订单金额，从而根据小计（或总计）获得免运费。
1. **MDVA-30945**：修复了在更新购物车时收到致命错误消息的问题 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.
1. **MDVA-30972**：修复了自定义订单状态更改为的问题 *正在处理* 在使用WebApi创建部分装运后。
1. **MDVA-31007**：修复了自定义地址属性未正确显示在我的帐户区域和后端的订单详细信息页面中的问题。
1. **MDVA-31021**：修复了中存在的性能问题 `module-catalog-import-export/Model/Import/Product/Option.php`. 如果中有超过~10万个记录 `catalog_product_option` 表，对带有单个产品的新CSV进行验证需要的时间少于10秒。
1. **MDVA-31224**：提高的性能 `catalog_product_price` 对捆绑产品执行重新索引操作。
1. **MDVA-31282**：修复了出现双重授权的问题。 [!DNL Paypal PayFlow Pro] 在Adobe Commerce中。 双重授权还会产生绕过的效果 [!DNL PayFlow Pro's] 欺诈过滤器和翻倍的交易费用。
1. **MDVA-31343**：修复了已删除主体类的问题 `page-layout-category-full-width` 在计划类别时。

使用左侧的菜单导航到特定的修补程序页面。
