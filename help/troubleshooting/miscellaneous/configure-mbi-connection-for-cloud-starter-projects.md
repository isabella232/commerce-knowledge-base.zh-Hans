---
title: 为现有Adobe Commerce Starter项目配置Cloud Intelligence连接
description: 本文提供一种解决方案，可用于为现有Adobe Commerce Starter项目配置Cloud Intelligence连接。
feature: Commerce Intelligence
role: Developer
exl-id: 56f6ad64-729d-4e3a-93a9-da1b91bc5c1d
source-git-commit: b75328202952bf4c8f57ddc538b5c9e4318b2001
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# 为现有Adobe Commerce Starter项目配置Cloud Intelligence连接

>[!NOTE]
>
>Adobe Commerce Intelligence以前称为Magento Business Intelligence(MBI)。

本文提供一种解决方案，可用于为现有Adobe Commerce Starter项目配置Cloud Intelligence连接。

## 受影响的产品和版本

Adobe Commerce on cloud starter（所有版本）

## 问题

要为现有Commerce Starter项目配置Cloud Intelligence连接。

>[!NOTE]
>
>Adobe不再支持新的Cloud Starter订阅，但是如果您现有一个Starter项目，则需要按照下方给出的步骤配置连接。

## 解决方案

要激活适用于Cloud Starter项目的Commerce Intelligence，请创建Commerce Intelligence帐户，创建SSH密钥，最后连接到Adobe Commerce数据库。

请按照以下步骤操作：

1. 创建您的Adobe Commerce Intelligence帐户：

   * 转到 [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
   * 导航到 **[!UICONTROL My Account]** > **[!UICONTROL My MBI Instances]**.
   * 单击 **[!UICONTROL Create Instance]**. 如果未看到此按钮，请联系您的客户成功经理或客户技术顾问。
   * 选择您的Cloud Starter订阅。 如果您只有Cloud Starter订阅，则会自动选择此设置。
   * 单击 **[!UICONTROL Continue]**.
   * 输入您的信息以创建您的帐户。

   ![创建MBI帐户](/help/troubleshooting/miscellaneous/assets/create_mbi_account.png)

   * 转到您的收件箱并验证电子邮件地址。

   ![验证电子邮件地址](/help/troubleshooting/miscellaneous/assets/verify_email_address_mbi.png)

   * 创建密码。

   ![创建密码](/help/troubleshooting/miscellaneous/assets/create_password_mbi.png)

   * 创建帐户后，您可以选择将用户添加到新帐户。 现在可以添加技术管理员以执行以下步骤。

   ![添加用户](/help/troubleshooting/miscellaneous/assets/add_users_mbi.png)

1. 输入关于您的商店的信息以设置您的首选项。

   ![添加商店信息](/help/troubleshooting/miscellaneous/assets/add_store_info_mbi.png)

   在连接数据库以进行入门培训流程中的第三步之前，您需要收集一些信息。 您将填写 *[!UICONTROL Connect your database]* 步骤9中的页面。

1. 创建专用的Commerce Intelligence用户。

   * 创建新用户 [account.adobe.com](https://account.adobe.com/).
   * 转到 [https://accounts.magento.com/customer/account/](https://accounts.magento.com/customer/account/) 以生成您的Adobe Commerce帐户。
   * 为什么是新用户？ Adobe Commerce Intelligence需要添加到项目中的用户不断获取新数据，以传输到帐户的Commerce Intelligence数据仓库。 此用户将用作该连接。 将此用户添加到项目将执行步骤4。
   * 之所以拥有专门的Commerce Intelligence用户，是为了防止无意中停用或删除添加的用户并停止Commerce Intelligence连接。

1. 将新创建的用户作为添加到项目的主环境 *投稿人*.

   ![添加用户作为参与者](/help/troubleshooting/miscellaneous/assets/contributor_user_mbi.png)

1. 获取Commerce智能SSH密钥。

   * 转到 **[!UICONTROL Connect your database]** “Commerce Intelligence”设置用户界面并向下滚动到 **[!UICONTROL Encryption settings]**.
   * 对于字段， **[!UICONTROL Encryption Type]**，选择 **[!UICONTROL SSH Tunnel]**.
   * 从下拉菜单中，您可以复制并粘贴提供的MagentoBI Essentials公钥。

   ![加密设置](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

1. 将新的MagentoBI Essentials公钥添加到在第5步中创建的Commerce Intelligence用户。

   * 转到 [accounts.magento.com/customer/account/login](https://account.magento.com/customer/account/login). 使用您为Commerce Intelligence新用户创建的帐户登录信息登录。 然后转到 **[!UICONTROL Account Settings]** 选项卡。
   * 向下滚动页面，并展开SSH密钥的下拉列表。 然后单击 **[!UICONTROL Add a public key]**.

   ![添加公钥](/help/troubleshooting/miscellaneous/assets/add_public_key_mbi.png)

   * 从上面添加MagentoMBI Essentials SSH公钥。

   ![添加SSH公钥](/help/troubleshooting/miscellaneous/assets/add_ssh_key_mbi.png)

1. 提供Business IntelligenceEssentials MySQL凭据。

   * 更新您的 `.magento/services.yaml`.

   ```
   mysql:
    type: mysql:10.0
    disk: 2048
    configuration:
        schemas:
            - main
        endpoints:
            mysql:
                default_schema: main
                privileges:
                    main: admin
            mbi:
                default_schema: main
                privileges:
                    main: ro
   ```

   * 更新您的 `.magento.app.yaml`.

   ```
   relationships:
            database: "mysql:mysql"
            mbi: "mysql:mbi"
            redis: "redis:redis"
   ```

1. 获取有关将数据库连接到Commerce Intelligence的信息。

   运行 `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 --decode | json_pp` 以获取有关连接数据库的信息。

   您应会收到与以下输出类似的信息：

   ```
   "mbi" : [
              {
                 "scheme" : "mysql",
                 "rel" : "mbi",
                 "cluster" : "vfbfui4vmfez6-master-7rqtwti",
                 "query" : {
                    "is_master" : true
                 },
                 "ip" : "169.254.169.143",
                 "path" : "main",
                 "host" : "mbi.internal",
                 "hostname" : "3m7xizydbomhnulyglx2ku4wpq.mysql.service._.magentosite.cloud",
                 "username" : "mbi",
                 "service" : "mysql",
                 "port" : 3306,
                 "password" : "[password]"
              }
           ],
   ```

1. 连接您的Adobe Commerce数据库。

   ![连接Adobe Commerce数据库](/help/troubleshooting/miscellaneous/assets/connect_magento_database_mbi.png)

   *输入*：

   * 集成名称： [选择集成的名称。]
   * 主机： `mbi.internal`
   * 端口：3306
   * 用户名：mbi
   * 密码： [步骤8的输出中提供的输入密码。]
   * 数据库名称： main
   * 表前缀： [如果没有表前缀，则保留为空]

1. 设置您的 [!UICONTROL Timezone Settings].

   ![时区设置](/help/troubleshooting/miscellaneous/assets/timezone_settings_mbi.png)

   *输入*

   * 数据库：时区：UTC
   * 所需时区： [选择要显示数据的时区。]

1. 获取有关加密设置的信息。

   * 项目UI提供SSH访问字符串。 此字符串可用于收集在设置时远程地址和用户名所需的信息 **[!UICONTROL Encryption settings]**. 选择 **[!UICONTROL SSH]** 查看您的用户名和远程地址。 之前存在的文本字符串 *@* 是您的用户名和之后的文本字符串 *@* 是您的远程地址。

   ![访问站点主体](/help/troubleshooting/miscellaneous/assets/access_site_mbi.png)

1. 输入您的信息 [!UICONTROL Encryption Settings].

   ![加密设置](/help/troubleshooting/miscellaneous/assets/encryption_type_mbi.png)

   *输入*

   * 加密类型： SSH通道
   * 远程地址：ssh.us-3.magento.cloud
   * 用户名：vfbfui4vmfez6-master-7rqtwti—mymagento
   * 端口：22

1. 单击 **[!UICONTROL Save Integration]**.
1. 您现在已成功连接到Commerce Intelligence Essentials帐户。
1. 如果您是Adobe Commerce Intelligence Pro客户，请联系您的客户成功经理或客户技术顾问来协调后续步骤。
