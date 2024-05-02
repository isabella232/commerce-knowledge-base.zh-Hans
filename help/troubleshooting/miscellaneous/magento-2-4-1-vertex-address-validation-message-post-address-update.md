---
title: Adobe Commerce 2.4.1顶点地址验证消息地址更新
description: 本文介绍了一个已知的Adobe Commerce 2.4.1问题，其中在使用与帐单地址不同的送货地址时，在付款步骤中无法验证顶点地址。 Adobe Commerce 2.4.2中计划修复此问题。
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Adobe Commerce 2.4.1顶点地址验证消息地址更新

本文介绍了一个已知的Adobe Commerce 2.4.1问题，其中在使用与帐单地址不同的送货地址时，在付款步骤中无法验证顶点地址。 Adobe Commerce 2.4.2中计划修复此问题。

## 受影响的产品和版本

* 启用了顶点集成的Adobe Commerce内部部署2.4.1
* 云基础架构2.4.1上的Adobe Commerce启用了顶点集成

## 问题

先决条件：

启用 **顶点地址清理**. 有关步骤，请参阅 [配置店面地址清理](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.html) 在我们的用户指南中。

<u>重现问题的步骤：</u>

1. 创建帐户并登录。
1. 通过单击将项目添加到购物车 **添加到购物车**. 单击“购物车”图标，然后单击 **继续操作直到进入结账流程**.
1. 在“ ”中输入有效地址 **配送地址** 字段。
1. 选中下的任一选项 **配送方式**. 然后单击 **下一个**.
1. 如果“地址验证”建议不同的地址信息，请单击 **更新地址** 并单击 **下一个**.
1. 取消选中 **我的帐单地址和送货地址相同** 复选框。

<u>第一个方案：</u>

请遵循 [超过六个步骤](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) 然后：

1. 输入新的有效帐单地址。
1. 单击 **更新** 按钮。 它将显示如下消息/建议： *地址无效。* 下面将介绍地址建议，如下所示： *邮政编码：XXXXX- XXXX Street ：XXX City Street XXX*
1. 单击 **更新** 按钮(请勿单击 **更新地址** 按钮中（例如，顶点地址建议）。
1. 单击 **编辑** 更新帐单地址的按钮。
1. 从地址下拉列表中选择地址。
1. 单击 **更新** 按钮。

<u>预期结果：</u>

旧的验证消息/建议消息被删除。

<u>实际结果：</u>

验证消息/建议 *“未找到有效的地址邮政编码：XXXXX-XXXX Street ： XXX City Street XXX”* 消息为 **NOT** 已删除。 如果您在表单中输入的地址无效，也会出现同样的问题。

<u>第二种情况：</u>

请遵循 [超过六个步骤](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth) 然后：

1. 使用有效地址填写地址表单。
1. 单击 **更新** 按钮。 它将显示如下消息/建议： *地址无效。* 下面将介绍地址建议，如下所示： *邮政编码：XXXXX-XXXX Street ：XXX City Street XXX*.
1. 单击 **更新** 按钮(请勿单击 **更新地址** 按钮的顶点（地址建议）。
1. 查看 ***我的帐单地址和送货地址相同*** 下拉菜单。

<u>预期结果：</u>

旧的验证消息/建议消息被删除。

<u>实际结果：</u>

验证消息/建议 *“未找到有效的地址邮政编码：XXXXX-XXXX Street XXX City street XXX”* 消息为 **NOT** 已删除。 如果您在表单中输入的地址无效，也会出现同样的问题。

## 我们的支持知识库中的相关阅读：

[Adobe Commerce 2.3.6、2.4.0-p1和2.4.1已知问题：启用帐户后无法登录dotdigital](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
