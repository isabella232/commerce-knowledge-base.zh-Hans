---
title: 在沙盒脚本中BootstrapAdobe Commerce 2
description: '要在示例沙盒脚本中初始化Adobe Commerce 2应用程序，请从Adobe Commerce根目录执行以下脚本：'
exl-id: a6acb30a-5175-42c6-8de3-e80c9ae8dac1
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# 在沙盒脚本中BootstrapAdobe Commerce 2

要在示例沙盒脚本中初始化Adobe Commerce 2应用程序，请从Adobe Commerce根目录执行以下脚本：

```php
<?php

error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', 1);

require __DIR__ . '/app/bootstrap.php';
$bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
$objectManager = $bootstrap->getObjectManager();

//$model = $objectManager->get('Vendor\Module\Some\Model');
```
