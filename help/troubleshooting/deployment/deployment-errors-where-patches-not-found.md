---
title: 未找到修补程序的部署错误
description: “本文为您遇到错误*未找到下一个修补程序的问题提供了解决方案：MDVA-XXXXX、ACSD-XXXXX。 请检查‘状态’命令是否可用于当前Magento版本*。”
exl-id: 5a2fd35a-892a-48af-a41f-f275297b3e2e
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 未找到修补程序的部署错误

本文为升级实例时出现的部署失败且在部署日志中看到错误的问题提供了解决方案： *未找到以下修补程序： MDVA-XXXXX、ACSD-XXXXX。 请检查这些修补程序的“状态”命令是否可用于当前Magento版本*.

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce， [所有受支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).


## 问题

升级Adobe Commerce时遇到错误： *未找到下一个修补程序*.

## 原因

以前为旧版本应用的修补程序不适用于或不再适用于新版本。

## 解决方案

1. 检查您的 `.magento.env.yaml` 文件位于QUALITY_PATCH部分下，例如

   ```yaml
   QUALITY_PATCHES:
    - MDVA-XXXXX
    - ACSD-XXXXX
   ```

1. 在中查找修补程序ID [质量补丁发行说明](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) 要检查每个报表包是否都可以应用于要升级到的新Adobe Commerce版本。
1. 如果该修补程序不适用于要升级到的新版Adobe Commerce，请从以下位置删除修补程序ID `.magento.env.yaml` 文件。
1. 查看错误指示的所有修补程序ID后，推送更改并重新部署。

## 相关阅读

* [应用修补程序](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=en#apply-a-patch-in-a-local-environment) 《Commerce on Cloud Infrastructure指南》中的。
