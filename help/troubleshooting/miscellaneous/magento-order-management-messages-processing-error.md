---
title: Adobe Commerce的Magento Order Management系统(OMS)处理错误
description: 当您在运行“bin/magento oms”的CLI中遇到“getMode()”错误时，本文提供了此问题的解决方案:messages:Adobe Commerce的Magento Order Management系统(OMS)中的process`。
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Adobe Commerce的Magento Order Management系统(OMS)处理错误

本文提供了当您收到 `getMode()` 运行CLI时出错 `bin/magento oms:messages:process` 在Adobe Commerce的Magento Order Management系统(OMS)中。

## 受影响的产品和版本

使用MCOM连接器3.1.1和3.2.0版时，会出现此错误。在MCOM Connector 3.3.0中可解决此问题。它不是特定于MDC或MOM版本。

## 问题

在CLI中运行以下命令时：

`bin/magento oms:messages:process`

CLI中输出类似于以下内容的错误消息：

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## 原因

当连接器尝试处理时，会发生这种情况 `magento.inventory.source_management` 消息。 连接器尝试处理这些消息，就好像它们是 `magento.inventory.source_stock_management.update` 需要模式值的消息。 因为在 `magento.inventory.source_mangement` 消息时，出现错误。

## 解决方案

要解决此问题，请在CLI中运行以下SQL语句，该语句将删除 `mcom_api_messages` 表：

`delete from mcom_api_messages;`

## 相关阅读

请参阅OMS文档 [OMS连接器设置教程](https://omsdocs.magento.com/en/integration/connector/setup-tutorial/).
