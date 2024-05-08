---
title: 设置新项目的核对清单 [!DNL domain]
description: 这是一份清单，说明如何设置新的 [!DNL domain] 云基础架构上的Adobe Commerce中的。
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# 设置新项目的核对清单 [!DNL domain]

这是一份清单，说明如何设置新的 [!DNL domain] 云基础架构上的Adobe Commerce中的。 无论您是尝试仅添加新域还是使用新域替换当前域，它均适用。

## 受影响的产品和版本

云基础架构上的Adobe Commerce， [所有受支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 如何设置新域

### 第1步 — 这是否适用于 [!DNL Integration, Staging]，或 [!DNL Production environment]？

* **[!DNL Integration]**： [!DNL Custom domains] 不受支持。 必须改用此方法： [设置多个网站或商店：配置本地安装](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) 在我们的用户指南中。
* **[!DNL Staging]**：转到 **步骤2**.
* **[!DNL Production]**：转到 **步骤3**.

### 第2步 —  [!DNL Staging environment]：您是否启用 [!DNL Pro] 或 [!DNL Starter]？

* **[!DNL Pro]**： **提交请求** 将域添加到 [!DNL Fastly, Nginx]，并配置 [!DNL SSL certificate] (以及 [!DNL Sendgrid domain]（如有必要）。 一旦完成配置， [更新 [!DNL DNS] 配置 [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>您可以添加新的 [!DNL domain] 到 [!DNL Fastly] 您自己，只需在 [!DNL Admin] 在 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** 如所示 [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) 在我们的用户指南中。
>
>如果您无法添加域，可能是由于以下原因之一：
>
>1. 您正在将域迁移到云环境，在您自己的环境中进行了配置 [!DNL Fastly] 服务。 在这种情况下，提交请求并请求委派域。
>1. 您正在将域从Starter迁移到Pro。 在这种情况下，请提出进一步援助请求。

* **[!DNL Starter]**： [!DNL Custom domains] 暂存环境上不支持。

### 步骤3 - [!DNL Production environment]：您是否启用 [!DNL Pro] 或 [!DNL Starter]？

* **[!DNL Pro]**： **提交请求** 将域添加到 [!DNL Fastly, Nginx]，并配置 [!DNL SSL certificate] (作为 [!DNL Sendgrid domain]（如有必要）。 配置完毕后，请继续 **步骤4**.

>[!NOTE]
>
>您可以添加新的 [!DNL domain] 到 [!DNL Fastly] 您自己，只需在 [!DNL Admin] 在 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) 在我们的用户指南中。
>
>
>如果您无法添加域，可能是由于以下原因之一：
>
>1. 您正在将域从内部部署迁移到云环境，该环境已在您自己的环境中配置 [!DNL Fastly] 服务。 在这种情况下，提交请求并请求委派域。
>1. 您正在将域从Starter迁移到Pro。 在这种情况下，请提出进一步援助请求。

* **[!DNL Starter]**：添加 [!DNL domain] 至您的项目 **[!DNL Domains]** 选项卡，然后 **提交请求** 以提供 **[!DNL ACME Challenge Key]** 对于 [!DNL SSL certificate].

### 第4步 — 是 [!DNL domain] 直播？

* **是**： [更新 [!DNL DNS] 配置 [!UICONTROL production] 设置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **否**： [更新 [!DNL DNS] 配置 [!UICONTROL development] 设置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## 相关阅读

* [设置多个网站或商店：新增 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) 在我们的用户指南中。
