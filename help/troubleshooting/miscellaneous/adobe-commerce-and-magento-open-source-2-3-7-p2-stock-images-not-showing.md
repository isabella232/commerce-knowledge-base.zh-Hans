---
title: 不显示图库图像，Adobe Commerce和Magento Open Source2.3.7-p2
description: 本文为上传到文件系统目录“pub/media”或“pub/media/catalog”的Adobe库图像未显示在Media Gallery UI中的问题提供了解决方案。 这是因为图像位于允许的媒体集目录之外。 对于这些要显示的图像，商家需要删除文件系统上的图像，然后重新上传到允许的媒体集目录中。
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 不显示图库图像，Adobe Commerce和Magento Open Source2.3.7-p2

本文为将Adobe库图像上传到文件系统目录的问题提供了一个解决方案 `pub/media` 或 `pub/media/catalog` 不在媒体集UI中显示。 这是因为图像位于允许的媒体集目录之外。 对于这些要显示的图像，商家需要删除文件系统上的图像，然后重新上传到允许的媒体集目录中。

## 受影响的产品和版本

* Adobe Commerce和Magento Open Source2.3.7-p2


## 问题

商家可以将Adobe Stock图像上传到媒体集中的存储根，但这些图像未出现在UI中，并且看起来好像未上传一样。 这是因为系统注意到图像已上传到文件系统，尽管它在媒体集UI中不可用。 这意味着，一旦商家将图像上传到 `pub/media` 或 `pub/media/catalog`中，用户无法使用该图像，除非将其直接在文件系统中删除。

<u>重现问题的步骤</u>

1. 使用有效的API密钥启用Adobe Stock。
1. 打开媒体集(**目录** > **类别** > **内容** 部分>单击 **从图库中选择**)。
1. 单击 **搜索Adobe Stock**.
1. 选择图像。 单击 **保存预览**. 请注意，您可能必须重置Adobe Stock网格才能显示图像。

<u>预期结果</u>：

此时将显示图像。

<u>实际结果</u>：

显示一条错误消息： *找不到图像。 我们在媒体集中找不到此图像。*

## 原因

可以通过Adobe Stock将图像上传到媒体集存储根。

## 解决方案

选择介质集存储根的任何子目录(不包括 **存储根** > **目录**)，然后上传Adobe Stock图像。
从删除上传的Adobe Stock图像 `pub/media` 和 `pub/media/catalog` Adobe Commerce文件系统中的文件夹，并将图像上传到任何允许的媒体集存储根子目录中(不包括 **存储根** > **目录**)。

## 相关阅读

* [媒体存储](https://docs.magento.com/user-guide/v2.3/cms/media-storage.html) 在我们的用户指南中。
