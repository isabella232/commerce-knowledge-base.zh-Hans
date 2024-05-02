---
title: 'ACSD-50794：无法通过GraphQL从客户订单中删除礼品包装'
description: 应用ACSD-50794修补程序以修复Adobe Commerce问题，该问题导致用户无法通过GraphQL从客户订单中删除礼品包装。
exl-id: 4983910c-9ea0-451e-a2b6-81485184bbce
feature: Gift, GraphQL, Orders
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-50794：无法通过GraphQL从客户订单中删除礼品包装

ACSD-50794修补程序修复了用户无法通过GraphQL从客户订单中删除礼品包装的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.32。 修补程序ID为ACSD-50794。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户无法通过GraphQL从客户订单中删除礼品包装。

<u>重现问题的步骤</u>：

1. 从前端创建客户。
1. 创建一个简单的产品。
1. 启用 *[!UICONTROL Gift Messages]* 通过转到 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** 并设置 *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. 创建 *[!UICONTROL Gift Wrapping]* 通过转到 **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. 获取客户令牌。
1. 创建一个空购物车customerCart。
   * 将产品添加到购物车： `addProductsToCart` 变异
   * 设置帐单地址： `setBillingAddressOnCart` 变异
   * 设置送货地址： `setShippingAddressesOnCart` 变异
   * 设置配送方式： `setShippingMethodsOnCart` 变异
   * 设置付款方式： `setPaymentMethodOnCart` 突变(checkmo)
1. 现在查看礼品包装 *Uid* 使用此购物车查询：

   <pre><code class="language-GraphQL">
    {
      cart(cart_id: "{{CART_ID}}") {
        available_gift_wrappings{
            uid
        }
    }
    }
    </code></pre>

1. 使用设置礼品包装 `setGiftOptionsOnCart`.
1. 检查购物车：购物车查询。
1. 使用以下方式取消设置礼品包装 `setGiftOptionsOnCart` （将值设置为null）。
1. 再次检查购物车：购物车查询。
1. 下单： `placeOrder` 突变。
1. 运行客户查询：客户。

   <pre><code class="language-graphql">
    query {
      customer {
        firstname
        middlename
        lastname
        suffix
        email
        orders {
            items {
                order_date
                gift_wrapping {
                    design
                    uid
                }
            }
        }
        addresses {
          firstname
          middlename
          lastname
          street
          city
          region {
            region_code
            region
          }
          postcode
          country_code
          telephone
        }
      }
    }
    </code></pre>

<u>预期结果</u>：

一旦用户设置了礼品包装并取消设置，客户查询将返回空值。

<u>实际结果</u>：

客户查询仍会按应用情况返回礼品包装。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
