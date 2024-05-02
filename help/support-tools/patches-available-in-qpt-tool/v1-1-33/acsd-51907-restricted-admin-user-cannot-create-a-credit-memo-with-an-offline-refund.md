---
title: “ACSD-51907：受限管理员用户无法创建离线退款的贷项通知单”
description: 应用ACSD-51907补丁以修复Adobe Commerce问题，该问题导致受限管理员用户无法创建包含离线退款的贷项通知单。
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907：受限管理员用户无法创建离线退款的贷项通知单

ACSD-51907修补程序修复了受限管理员用户无法创建具有离线退款的贷项通知单的性能问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.33。 修补程序ID为ACSD-51907。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

受限管理员用户无法创建具有离线退款的贷项通知单。

<u>重现问题的步骤</u>：

1. 创建 **客户** 默认网站上的。
1. 创建 **新网站** 具有相关项 *存储* 和 *商店视图*.
1. 将默认网站设置为新网站，清除缓存。
1. 更改客户配置： **管理员** > **存储** > **配置** > **客户** > **客户配置** > **共享客户帐户=全局**.
1. 新建管理员用户角色，并将角色范围设置为新建的网站 *（仅访问销售数据）* 在 **管理员** > **系统** > **权限**.
1. 使用此角色创建新的管理员帐户。
1. 使用在线付款方式创建新订单 *(例如Auth.net或PayPal)*.
1. 以受限管理员用户身份登录。
1. 转到 **销售** > **订购** >则 **订单查看页面**.
1. 创建发票。
1. 定位至“发票”标签。
1. 单击 **发票**.
1. 单击 **[!UICONTROL Credit Memo]**.
1. 查看 **[!UICONTROL Refund to Store Credit]** 复选框，将旁边的文本字段设置为 *1* 值。
1. 单击 **[!UICONTROL Refund Offline]** 按钮。

<u>预期结果</u>：

创建贷项通知单，并且 *1美元* 退款至商店积分。

<u>实际结果</u>：

错误信息， *需要更多权限才能查看此项目* 将显示。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
