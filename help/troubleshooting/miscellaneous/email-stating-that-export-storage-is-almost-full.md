---
title: '电子邮件表明导出存储几乎已满'
description: 本文针对您收到一封电子邮件，指出导出存储已几乎满的问题提供了解决方案。
feature: Cloud, Storage, Media
role: Developer
source-git-commit: 8f783cb4245911bded5e9946917e2f2c3e78a705
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 电子邮件表明导出存储空间几乎已满

本文针对您收到一封电子邮件，指出导出存储已几乎满的问题提供了解决方案。

## 受影响的产品和版本

云基础架构上的Adobe Commerce（所有版本）

## 问题

您会收到一封包含以下内容的电子邮件，但无法找到 *导出* 文件夹：

*我们的监测功能检测到您的群集XXX上的“导出”存储已满大约“85%”。*
*如果需要，请检查用法、进行清理或请求升级。*
*另外，请注意，当存储达到临界阈值级别时，我们将自动尝试进行升级。*

## 原因

该电子邮件是指 **导出** 存储，指分配给文件/介质的磁盘量，而不是指定的文件夹 *导出*.

## 解决方案

您应该查看环境中的文件使用情况。 运行此命令以获取现有用法：

`df -h |grep data`

文件存储可能填充的典型位置是 *pub/media/catalog/product/cache* 或 *var/日志* 文件夹。 要确定文件使用的磁盘空间，请使用相应的路径运行此命令 */path/to/folder*：

`du -shc` */path/to/folder*

如果介质磁盘使用率在总磁盘空间中占很大比例，您可能需要考虑启用 [Fastly深度图像优化](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)，然后删除中的文件 *pub/media/catalog/product/cache* 手动删除服务器上的文件夹。

## 相关阅读

[检查专用群集](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters) 在我们的支持知识库中。