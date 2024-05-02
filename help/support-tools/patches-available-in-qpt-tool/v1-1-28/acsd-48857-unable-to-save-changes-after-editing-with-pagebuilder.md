---
title: '''ACSD-48857：编辑后无法保存更改 [!DNL Page Builder]’'
description: Adobe Commerce应用ACSD-48857修补程序以修复以下问题：用户在使用进行编辑后无法保存更改 [!DNL Page Builder].
exl-id: c95b354d-8954-4e9c-9e92-8a64f62f0a68
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857：使用编辑后无法保存更改 [!DNL Page Builder]

ACSD-48857修补程序修复了用户在编辑之后无法保存更改的问题 [!DNL Page Builder]. 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.28。 修补程序ID为ACSD-48857。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户在使用编辑后无法保存更改 [!DNL Page Builder].

<u>重现问题的步骤</u>

1. 登录到Admin网站。
1. 导航到 **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** 创建空的CMS页面。
1. 运行此SQL脚本以设置以下内容 **[!UICONTROL Content]** 字段值：

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. 返回到 **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** 在Admin.
1. 编辑您的页面。
1. 转到 **[!UICONTROL Content]** 选项卡。
1. 单击 **[!UICONTROL Save]**.

<u>预期结果</u>

HTML内容清理已实施。 这将删除 [!DNL Page Builder] 文本编辑器生成的内容中的保留HTML属性。

<u>实际结果</u>

页面保持未保存状态，加载器继续旋转。 在控制台中，生成以下错误：

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
