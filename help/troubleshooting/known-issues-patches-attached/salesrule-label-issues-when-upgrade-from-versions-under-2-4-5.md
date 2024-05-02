---
title: ’[!UICONTROL salesRule] 从版本&lt； 2.4.5升级时出现标签问题
description: 应用补丁以处理**[!UICONTROL salesRule]**复从Adobe Commerce版本&lt； 2.4.5升级时出现的问题。
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# **[!UICONTROL salesRule]** 从低于2.4.5的版本升级时出现标签问题

此 **[!UICONTROL salesRule]** Adobe Commerce中引入了标签暂存功能 [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html). 当您从Adobe Commerce &lt; 2.4.5升级到任何版本>= 2.4.5时，此更改可能会导致问题。升级后，可能会 **[!UICONTROL salesRule]** 标签不匹配。 要解决此问题，应在升级到较新的Adobe Commerce版本后立即应用修补程序。

## 受影响的产品和版本

云基础架构上的Adobe Commerce &lt; 2.4.5

## Patch

使用以下附加的修补程序：

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## 如何应用修补程序

1. 请按照中的步骤操作 [执行升级](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html) 在Commerce指南中。
1. 请在安装之前应用附加的修补程序 **[!UICONTROL Update metadata]** 阶段。
(您还可以在完成以下操作后应用修补程序： **[!UICONTROL Update metadata]** 阶段，但您需要运行 `bin/magento setup:upgrade` 再一次)。
1. 继续执行中的其余步骤 [执行升级](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
