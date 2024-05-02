---
title: 'MDVA-39605： Redis缓存TTL（过期日期）的值错误'
description: MDVA-39605修补程序解决了Redis缓存TTL（过期日期）具有错误值的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-39605。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 667fcacd5b6cbf56a5fd919d0683ad6a0f979fca
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605： Redis缓存TTL（过期日期）的值错误

MDVA-39605修补程序解决了Redis缓存TTL（过期日期）具有错误值的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.13。 修补程序ID为MDVA-39605。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Redis缓存TTL（过期日期）的值错误。

<u>重现问题的步骤</u>：

为了测试此修复，请刷新缓存并在店面中打开可配置产品。 然后打开终端（控制台）并按照以下步骤操作：

1. 运行以下命令： `redis-cli`.
1. 运行 `KEYS "*PRICE"` (结果中应该只有一个键，例如， `zc:ti:e54_PRICE`)。 复制密钥。
1. 运行 `SMEMBERS` 后跟上一步中的键(例如， `SMEMBERS zc:ti:e54_PRICE`)。 从结果复制任何密钥(例如，e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421)。
1. 运行 `KEYS "*<key>"` 使用上一步骤中的键名称获取完整的键名称(例如， `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`)。 结果中应当只有一个键(例如， `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`)。 如您所见，全键名称只是前缀为&#39;&#39;的键名称`zc:k:`“。 现在复制完整密钥名称。
1. 运行 `HGETALL` ，然后是步骤4中的全键名称以检查该值。 该值应包含相关可配置产品的关联产品的序列化数据。
1. 运行 `TTL` ，然后是步骤4中的完整密钥名称，以检查密钥是否过期。 结果应不同于以 **-1** 和 **-2** 并且应该约为2592000（30天）。 尽管代码中设置的过期时间为一年，但Adobe Commerce中使用的Redis库的最大硬过期限制为2592000秒。

<u>预期结果</u>：

到期限制为2592000秒

<u>实际结果</u>：

到期限制设置为 **-1** 或 **-2**.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
