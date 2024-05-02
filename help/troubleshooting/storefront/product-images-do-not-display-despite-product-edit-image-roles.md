---
title: 尽管具有“产品编辑”图像角色，仍不显示产品图像
description: 本文修复了尽管在“产品编辑”页面上设置了图像角色，但是店面中仍未显示产品图像的问题。
exl-id: 456baa5a-fa16-4bc1-9d6c-54106fae58ca
feature: Cache, Products, Roles/Permissions, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# 尽管具有“产品编辑”图像角色，仍不显示产品图像

本文修复了尽管在“产品编辑”页面上设置了图像角色，但是店面中仍未显示产品图像的问题。

**原因：** 在具有多个商店的Adobe Commerce实例上，某些产品图像可能具有 `no_selection` 图像角色属性的值 `image`， `small_image`， `thumbnail`， `swatch`. 此类 `no_selection` 当产品图像角色设置在全局、所有商店范围而不是特定商店的范围时(换句话说，在 **所有商店视图** 而不是特定 **商店视图**)。 要了解情况是否如此，请从 **原因** 部分。

**解决方案：** 删除行 `no_selection` 使用以下“解决方案”部分中的SQL脚本创建此类图像的值。

## 受影响的版本

* Adobe Commerce内部部署2.X.X
* 云基础架构上的Adobe Commerce 2.X.X

## 问题

尽管已在“管理员”面板的“产品”页面上正确设置了图像角色（“基本”、“小型”、“缩略图”、“色板”），但产品图像可能不会显示在店面上。

当您使用以下方式查看产品页面时 **商店视图** 设置为 **所有商店视图**，图片上的角色已设置 **图像详细信息** 屏幕。

![all_store_views.png](assets/all_store_views.png)

![image_roles.png](assets/image_roles.png)

但是，在店面，图像不显示；当您检查特定商店级别的产品页面(切换 **商店视图**)，则图像已存在，但未设置角色。

![image_roles_not_set.png](assets/image_roles_not_set.png)

## 原因

在多商店Adobe Commerce实例（具有多个商店）中，某些产品图像可能具有 `no_selection` 属性值 `image`， `small_image`， `thumbnail`， `swatch` （这些属性对应于图像角色）。 此类 `no_selection` 当产品图像角色设置在全局、所有商店范围而不是特定商店的范围时(换句话说，在 **所有商店视图** 而不是特定 **商店视图**)。

从技术上讲：打开 `store_id=0` (保留Adobe Commerce实例中所有商店的全局设置)，则可能会设置产品图像角色：这表示属性 `image`， `small_image`， `thumbnail`， `swatch` 具有有效值（图像的路径）。 同时，在 `store_id=1` （这是特定的存储表示形式），这些属性的值是 `no_selection`.

### 如何验证这是您的问题

执行此SQL查询：

```sql
SELECT `cpev_s`.*, `cpev_0`.`value` AS `store_value` FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

如果查询返回如下结果，您将处理本文中记录的问题：

```sql
+----------+--------------+----------+--------+--------------+----------------------------+
| value_id | attribute_id | store_id | row_id | value        | store_value                |
+----------+--------------+----------+--------+--------------+----------------------------+
|    67722 |           87 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67723 |           88 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67724 |           89 |        1 |    481 | no_selection | /3/5/355sss1_main.jpg      |
|    67814 |           87 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6769 |           87 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67815 |           88 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6770 |           88 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|    67816 |           89 |        1 |    503 | no_selection | /s/k/skb2031_main.jpg      |
|     6771 |           89 |        2 |    503 | no_selection | /s/k/skb2031_main.jpg      |
+----------+--------------+----------+--------+--------------+----------------------------+
9 rows in set (0.06 sec)
```

### 为什么会出现这种情况？

如果Adobe Commerce应用程序有多个存储，则它可能不会在特定存储与全局存储设置之间同步数据。

值 `store_id=1` 具有比默认（全局）存储更高的优先级(`store_id=0`)。 因此，应用程序可以忽略全局映像设置并使用存储范围配置(`no_selection` （对于图像角色属性）。

## 解决方案 {#solution}

删除具有以下特征的属性： `no_selection` 使用此SQL脚本的值：

```
DELETE `cpev_s`.* FROM `catalog_product_entity_varchar` `cpev_s` JOIN `eav_attribute` `ea` ON `cpev_s`.`attribute_id` = `ea`.`attribute_id` LEFT JOIN `catalog_product_entity_varchar` `cpev_0` ON `cpev_0`.`row_id` = `cpev_s`.`row_id` AND `cpev_0`.`attribute_id` = `cpev_s`.`attribute_id` AND `cpev_0`.`store_id` = 0 WHERE `cpev_s`.`value` = 'no_selection' AND `ea`.`attribute_code` IN ('image', 'small_image', 'thumbnail') AND `cpev_s`.`store_id` > 0 AND `cpev_s`.`value` != `cpev_0`.`value` AND `cpev_s`.`value` = 'no_selection';
```

移除这些属性后，将设置特定商店的角色，并在店面中显示图像。

## 其他详细信息

如果在Adobe Commerce实例中启用了全页缓存，您将无法立即查看修复结果。

要显示更改，请使用 **缓存管理** 管理面板的菜单。

## 更多信息

### 存储和范围

[存储和存储范围](/docs/commerce-admin/stores-sales/site-store/stores.html) 在我们的用户指南中

### 图像

[上传产品图像](/docs/commerce-admin/catalog/products/digital-assets/product-image.html#upload-an-image) 在我们的用户指南中

### 缓存

* [缓存管理](/docs/commerce-admin/systems/tools/cache-management.html) (在我们的“User Admin System Guide（用户管理系统指南）”中)。
* [管理缓存](/docs/commerce-operations/configuration-guide/cli/manage-cache.html) 在我们的开发人员文档中