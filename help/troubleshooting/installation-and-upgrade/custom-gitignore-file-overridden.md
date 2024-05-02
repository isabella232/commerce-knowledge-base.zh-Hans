---
title: Composer install命令覆盖.gitignore文件、Adobe Commerce
description: 本文为当Adobe Commerce上的编辑器在cloud infrastructure 2.4.2-p1和2.3.7上覆盖跟踪的“.gitignore”文件提供了一个解决方案。
exl-id: b0604bae-d630-4292-88d7-6945db30fcf4
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Composer install命令覆盖.gitignore文件、Adobe Commerce

本文为跟踪何时发送数据提供了解决方案 `.gitignore` 在Cloud Infrastructure 2.4.2-p1和2.3.7上，文件被Adobe Commerce上的编辑器覆盖。

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.4.2-p1和2.3.7。

## 问题

`.gitignore` 运行composer install命令时文件被覆盖。

<u>重现问题的步骤</u>：


1. 为工作区创建一个空目录。
1. 在根目录中运行此命令：

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition:2.4.2-p1.
   ```

   \#或2.3.7

1. 然后运行以下命令：
   1. `echo "/this/line/should/stay" >> .gitignore`
   1. `git init`
   1. `git add * && git add .*`
   1. `git commit -m "Init"` #提交到存储库的文件
   1. `rm -rf vendor/*`
   1. `composer install`
   1. `git diff`

      ```git
      diff --git a/.gitignore b/.gitignore
      index c144521..7092a56 100644
      --- a/.gitignore
      +++ b/.gitignore
      @@ -70,4 +70,3 @@ atlassian*
      /generated/*
      !/generated/.htaccess
      .DS_Store
      -/this/line/should/stay
      ```

<u>预期结果</u>：

`.gitignore` 不会被编辑器覆盖。

<u>实际结果</u>：

`.gitignore` 被每次编辑器安装运行覆盖。

## 解决方案

保持您的自定义 `.gitignore file` 您需要在 `magento-deploy-ignore` 部分。

```git
{
...
"extra": {
    "magento-deploy-ignore": {
        "*": [
            "/.gitignore"
        ]
    }
    ...
}
```


## 相关阅读

* [跟踪的.gitignore文件已由编辑器覆盖！](https://github.com/magento/magento2/issues/32888) 在Magento2 GitHub中。
