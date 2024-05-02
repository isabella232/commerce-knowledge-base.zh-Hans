---
title: 'MDVA-34948：网站速度减慢'
description: MDVA-34948 Adobe Commerce修补程序修复了网站速度减慢的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1后，即可使用此修补程序。 修补程序ID为MDVA-34948。 请注意，Adobe Commerce版本2.4.1中已修复此问题。
exl-id: ba5417b3-a71c-4f1b-877b-4e7206f86660
feature: Observability, Configuration
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# MDVA-34948：网站速度减慢


## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce内部部署和Adobe Commerce在云基础架构中2.3.6-2.3.6-p1、2.4.0-2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

网站运行速度变慢，从而阻碍了运营。

<u>重现问题的步骤</u>：

1. 运行 `show processlist` 在MySQL中。
1. 检查是否存在多个查询，例如：

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>预期结果</u>：

`GET_LOCK` 应该立即执行。

<u>实际结果</u>：

多个 `GET_LOCK` 每个查询最多卡住10秒。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
