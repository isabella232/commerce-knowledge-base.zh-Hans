---
title: 在云基础架构上的Adobe Commerce上更改管理员URL
description: 默认情况下，[Commerce管理员](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) URL设置为*&lt；domain\_name&gt；/admin*。 本文介绍如何更改URL。
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 在云基础架构上的Adobe Commerce上更改管理员URL

默认情况下， [Commerce管理员](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) URL设置为 *&lt;domain _name=&quot;&quot;>/admin*. 本文介绍如何更改URL。

## 方法1：使用“管理员”进行更改

请阅读以下步骤： [使用自定义管理员URL >更改管理员](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) 在我们的用户指南中。

## 方法2：添加ADMIN\_URL环境变量

### 集成环境

从 [云控制台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)，添加新的变量：

**名称：** 管理员\_URL **值：** 新建管理员URL

* 有关详细步骤，请参阅 [添加环境变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) 在我们的开发人员文档中。
* 另请参阅 [环境变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) 在我们的开发人员文档中。

### 当暂存和生产在Cloud Console中不可用时

[提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 请求为您的暂存或生产环境添加ADMIN\_URL变量。

如果可以从Cloud Console访问暂存和生产环境，请添加环境变量，如中所述 *集成环境* 部分。

### 使用Cloud CLI添加变量

您可以使用以下Cloud CLI命令（对于main）添加ADMIN\_URL变量：

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

有关更多详细说明，请参阅 [更改管理员URL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) 《Commerce on Cloud Infrastructure指南》的管理变量主题中的。

请注意，使用Cloud CLI更改ADMIN\_URL变量会触发环境的重新部署。 变量在默认情况下是可继承的；要阻止继承，请使用Cloud CLI命令选项来指示您不希望子环境继承变量值。 请参阅 [可见性](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) 《Commerce on Cloud Infrastructure指南》变量级别中的主题。
