---
title: 将折旧的Google图像图表替换为图像图表
description: 大多数Adobe Commerce版本当前都使用[Google Image Charts](https://developers.google.com/chart/image/)在Admin功能板中呈现静态图表。 自2019年3月14日起，Google将停止支持Google图像图表。 要解决此问题，我们提供补丁以使用[Image-Charts](https://www.image-charts.com/)免费服务替换Google图像图表。
exl-id: f86f0bb9-8a03-471d-8696-1eba4b8acbd1
feature: Cache, Compliance
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# 将折旧的Google图像图表替换为图像图表

当前使用的大多数Adobe Commerce版本和版本 [Google图像图表](https://developers.google.com/chart/image/) 以在Admin功能板中呈现静态图表。 自2019年3月14日起，Google将停止支持Google图像图表。 为了解决此问题，我们提供了补丁以替换Google图像图表 [图像图表](https://www.image-charts.com/) 免费服务。

## 受影响的版本

* Adobe Commerce 1.X，所有版本
* Adobe Commerce 2.X，所有版本

>[!NOTE]
>
>Adobe Commerce内部部署1.14.4.1、Magento Open Source1.9.4.1、Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.2将包含此图表更新。 升级到这些版本将继续支持图像图表，而不添加其他补丁程序。

## 问题

Google已于2019年3月14日停止支持Google图像图表。 Adobe Commerce 1.X和Adobe Commerce 2.2.X所有版本的用户将无法查看静态图表，除非他们下载并应用补丁程序，将Google图像图表替换为图像图表解决方案。 显示的图表将通过图像图表免费帐户服务与具有的Google图像图表具有相同的设计和功能 [GDPR](https://www.image-charts.com/data-processing-addendum.html) 合规性隐私政策。 有关其他选项，请参阅 [图像图表](https://www.image-charts.com/).

## 解决方案

要在Commerce管理员中查看静态图表，请下载并应用Adobe Commerce提供的修补程序。 无需其他配置。

### Adobe Commerce内部部署

1. 保存 [已连接MAGETOW-98833\_composer\_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch.zip) 修补并将其上传到Adobe Commerce根目录。
1. 运行以下SSH命令，并用实际修补程序名称替换了修补程序名称：

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch
   ```

   如果上述命令不起作用，请尝试使用 `-p2` 而不是 `-p1`.)

1. 要反映更改，请在下的管理员中刷新缓存 **系统** > **缓存管理**.

### 云基础架构上的Adobe Commerce

对于Cloud Markets，修补程序将包含在最近的ECE-tools更新中。

### Magento2开放源代码

1. 转到 [https://magento.com/tech-resources/download\#download2291](https://magento.com/tech-resources/download#download2291).
1. 在 **选择您的格式** 下拉列表，选择编辑器版本，然后单击 **下载**.
1. 将修补程序上传到Adobe Commerce根目录。
1. 运行以下SSH命令，并用实际修补程序名称替换了修补程序名称：

   ```git
   patch -p1 < MAGETWO-98833_composer_patch-2019-04-15-04-37-48.patch
   ```

   (如果上述命令不起作用，请尝试使用 `-p2` 而不是 `-p1`.)

1. 要反映更改，请在下的管理员中刷新缓存 **系统** > **缓存管理**.

### Adobe Commerce 1内部部署

按照以下步骤下载并应用修补程序：

1. 保存 [附加MPERF-10509-EE-2019-03-13-06-32-19.diff](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff.zip) 修补并将其上传到Adobe Commerce根目录。
1. 运行以下SSH命令：

   ```git
   patch -p1 < MPERF-10509-EE-2019-03-13-06-32-19.diff
   ```

   (如果上述命令不起作用，请尝试使用 `-p2` 而不是 `-p1`.)

1. 要反映更改，请在下的管理员中刷新缓存 **系统** > **缓存管理**.

### Magento1开放源代码

按照以下步骤下载并应用修补程序：

1. 单击 [**此链接**](https://magento.com/tech-resources/download#download2283) 查找“管理面板图表补丁程序”。
1. 选择

   ```git
   MPERF-10509.diff
   ```

   从 **选择您的格式** 下拉列表，然后单击“Download（下载）”。

1. 将文件上传到Adobe Commerce根目录。
1. 运行以下SSH命令：

   ```git
   patch -p1 < MPERF-10509.diff
   ```

   (如果上述命令不起作用，请尝试使用 `-p2` 而不是 `-p1`.)

1. 要反映更改，请在下的管理员中刷新缓存 **系统** > **缓存管理**.

## 附加文件

[下载MAGETOW-98833_composer_patch-2019-04-15-04-38-57.patch](assets/MAGETWO-98833_composer_patch-2019-04-15-04-38-57.patch)

[下载MPERF-10509-EE-2019-03-13-06-32-19.diffh](assets/MPERF-10509-EE-2019-03-13-06-32-19.diff)
