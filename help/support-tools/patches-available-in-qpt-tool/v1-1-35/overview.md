---
title: '''概述： [!DNL Quality Patches Tool] (QPT) v1.1.35`'
description: 此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.35。
feature: Tools and External Services
role: Admin
exl-id: 46228690-44ce-462f-b700-1aea6fa0eeab
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 概述： [!DNL Quality Patches Tool] (QPT) v1.1.35

此子部分详细说明了中提供的修补程序所修复的问题。 [!DNL Quality Patches Tool] (QPT) v1.1.35。

QPT v1.1.35包含以下修补程序：

1. **ACSD-51899**：修复了结账配送步骤中的默认配送地址自动填充为先前选择的店内装货地址的问题。
1. **ACSD-52041**：修复了错误消息的问题： *[错误] [!DNL Page Builder] 渲染了5秒钟，没有释放锁定*. 显示于 [!DNL Chrome] 使用保存编辑的内容时的浏览器 [!DNL Page Builder].
1. **ACSD-52095**：修复了 `manage_stock` 导出产品后，CSV文件中的值未正确设置为0。
1. **ACSD-51358**：修复了删除没有结束日期的计划更新会导致为同一实体删除其他计划更新的问题。
1. **ACSD-48070**：修复了编辑计划更新会触发异常的问题。
1. **ACSD-51890**：修复了 [!UICONTROL Submit review] 多次单击按钮，不需要 [!DNL Google] reCAPTCHA v3验证。
1. **ACSD-51984**：修复了取消选中的问题 *使用默认值和非默认产品字段值* 不会为第二个网站、商店和商店视图保存。
1. **ACSD-52398**：修复错误 *请求的数量不可用* 在尝试更新店面购物车中捆绑产品的数量时会发生这种情况。
1. **ACSD-52786**：修复了从给定SKU开始将目录规则条件SKU应用于所有产品的问题。
1. **ACSD-52921**：修复了在购物车中有缺货的可配置产品时从GraphQL请求购物车详细信息时发生内部错误的问题。
1. **ACSD-51683**：修复了使用GraphQL时无法将可自定义选项添加到购物车的问题。
1. **ACSD-52133**：修复了在升级后无法保存客户帐户的问题。
1. **ACSD-52202**：修复了在订单履行时，非默认库存更改为0数量时，默认库存的可销售数量错误地更改为0的问题。
1. **ACSD-51265**：修复了的问题 `catalog_product_price` 当系统中捆绑的产品过多时，重新索引性能。
1. **ACSD-52831**：修复了以下情况下客户无法下达可转让报价单的问题 [!DNL Google reCAPTCHA v3 Invisible] 已启用。
1. **ACSD-51845**：修复了无法通过异步批量REST API更新具有层价格和不同属性集的后续产品的问题。
1. **ACSD-52815**：修复了非默认来源的quantity字段输入最多支持6位数的问题，默认库存最多支持8位。
1. **ACSD-51149**：修复了以下问题： [!UICONTROL Scheduled ImportExport] 已启用 [!UICONTROL Catalog Permissions] 使索引器失效，然后由cron缓存刷新。
1. **ACSD-50815**：修复了简单产品的小数数量无法用于新捆绑产品选项的问题。
1. **ACSD-52399**：修复了可销售数量为0的可配置产品选项显示的问题 *有货* 在产品页面上。

使用左侧的菜单导航到特定的修补程序页面。
