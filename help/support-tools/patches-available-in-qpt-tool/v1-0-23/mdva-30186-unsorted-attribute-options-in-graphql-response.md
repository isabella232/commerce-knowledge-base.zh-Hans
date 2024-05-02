---
title: 'MDVA-30186：GraphQL响应中的属性选项未排序'
description: MDVA-30186修补程序解决了GraphQL响应中未对属性选项进行排序的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23后，即可使用此修补程序。 修补程序ID为MDVA-30186。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: 7b2aef16-5012-4206-9444-e0b765f0c0c9
feature: Attributes, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-30186：GraphQL响应中的属性选项未排序

MDVA-30186修补程序解决了GraphQL响应中未对属性选项进行排序的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.23。 修补程序ID为MDVA-30186。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.3.4和2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.3.5-p2、2.4.0 - 2.4.0-p1和2.4.2 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 将任意三个选项添加到现有颜色属性。
1. 创建六个带选项的简单产品(示例： *选项1*：1个产品， *选项2*：2个产品， *选项3*：3个产品)。
1. 创建一个类别并分配上面创建的所有产品。
1. 现在，使用您的类别ID发出以下GraphQL请求：

   <pre><code class="language-graphql">
    {
      products(
        filter: { category_id: { eq: "3" } }
        pageSize: 200
        currentPage: 1
        sort: { name: ASC }
      ) {
        aggregations {
          attribute_code
          count
          label
          options {
            count
            label
            value
          }
        }
        items {
          name
          sku
          url_key
        }
      }
    }
    </code></pre>

1. 现在，在“管理员”的“属性编辑”页面中更改属性选项的排序顺序。
1. 再次发出上述GraphQL请求，并观察颜色属性选项。

<u>预期结果</u>：

属性选项按照管理员设置的顺序排序。

<u>实际结果</u>：

属性选项始终根据关联的产品数排序。


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
