---
title: 'MDVA-39163：新注册的来宾会话中的产品用户无法使用配送方式'
description: MDVA-39163修补程序解决了在注册新用户且购物车中的产品来自来宾会话时配送方式不可用的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-39163。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163：新注册的来宾会话产品用户无法使用配送方式

MDVA-39163修补程序解决了在注册新用户且购物车中的产品来自来宾会话时配送方式不可用的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.9。 修补程序ID为MDVA-39163。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

注册新用户后，配送方式不可用，购物车中的产品来自访客会话。

<u>重现问题的步骤</u>：

1. 转到 **管理员** > **商店** > **配置** > **销售** > **投放方法**. 仅启用 **统一费率** 配送方式，并禁用其他所有方式。
1. 在 **统一费率** 配送方式，选择 **特定** 国家/地区选项可在 **发运至适用的国家/地区** 设置并从列表中选择一个国家（例如，美国）。
1. 转到 **管理员** > **商店** > **配置** > **客户** > **客户配置** 并设置 **需要电子邮件确认** 到 _是_.
1. 在中创建新电子邮件模板 **管理员** > **营销** > **电子邮件模板** 和加载 `Footer (magento/luma)` 模板并将模板内容替换为CMS块。

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. 转到 **管理员** > **内容** > **设计** > **配置** 并选择与前端网站相关的主题。 将“页脚模板”设置为创建的新电子邮件模板。
1. 转到前端并将产品添加到购物车。
1. 创建客户；您将收到一封确认电子邮件地址的电子邮件。 单击验证链接。 您将登录到网站。
1. 转到 **我的帐户** 并添加地址。 将地址国家/地区设置为您之前在管理员配置中设置的装运国家/地区。
1. 去结帐。

<u>预期结果</u>：

发运方法可用，因为客户有一个与发运国家/地区兼容的地址。

<u>实际结果</u>：

配送方式不可用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
