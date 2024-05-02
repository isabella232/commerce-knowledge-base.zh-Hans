---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.37`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.37。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4ccdba38-8171-4cc4-b8ef-d2c53dec0b47
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 概述： [!DNL Quality Patches Tool] (QPT) v1.1.37

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.37。

QPT v1.1.37包含以下修补程序：

1. **ACSD-52613**：修复了缓存和索引刷新的问题，即使未对进行更新也是如此 `Inventory_source` 个项目（按rest API）。
1. **ACSD-51884**：修复了运行调整大小命令后，产品图像缓存路径不正确的问题。
1. **ACSD-53628**：修复了CSV销售订单报表显示错误特殊字符的问题。
1. **ACSD-49843**：修复了使用在线付款方法对订购项目自动开票后，产品下载链接不可用的问题。 *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* 设置已启用。
1. **ACSD-53148**：修复了GraphQL中有关将同一可配置产品添加到购物车的两个并行请求导致购物车上有两个具有相同产品SKU的单独项目的问题。
1. **ACSD-47054**：修复了预览重新索引为所有存储区运行重新索引，从而导致速度缓慢的问题。
1. **ACSD-52606**：修复了错误消息的问题 *您的订单未准备好取货* 在用户单击时显示 **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**：修复了将图像替换为具有相同名称的其他图像后，未在前端更新图像的问题。
1. **ACSD-53728**：修复了产品EAV索引器完成时间较长的问题。
1. **ACSD-53979**：修复了在欢迎消息包含单引号时主页发生的JS问题。
1. **ACSD-52143**：修复了产品导入后删除自定义选项的问题。
1. **ACSD-53750**：修复了 *管道断开或连接关闭* 多线程运行期间出错 `catalog_product_price` 重新索引。

使用左侧的菜单导航到特定的修补程序页面。
