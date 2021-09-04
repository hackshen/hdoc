#### 安装

- 打开Terminal输入 --> `brew install mysql`

- 启动MySQL服务 --> `mysql.server start`

- 初始化MySQL配置: --> `mysql_secure_installation`

    ```bash
    hackshen@shen  :~ comet$ mysql_secure_installation

    Securing the MySQL server deployment.

    Connecting to MySQL using a blank password.

    VALIDATE PASSWORD PLUGIN can be used to test passwords
    and improve security. It checks the strength of password
    and allows the users to set only those passwords which are
    secure enough. Would you like to setup VALIDATE PASSWORD plugin?

    Press y|Y for Yes, any other key for No: N   // 这个选yes的话密码长度就必须要设置为8位以上，但我只想要6位的
    Please set the password for root here.

    New password:            　// 设置密码

    Re-enter new password:     // 再一次确认密码
    By default, a MySQL installation has an anonymous user,
    allowing anyone to log into MySQL without having to have
    a user account created for them. This is intended only for
    testing, and to make the installation go a bit smoother.
    You should remove them before moving into a production
    environment.

    Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y    // 移除不用密码的那个账户
    Success.


    Normally, root should only be allowed to connect from
    'localhost'. This ensures that someone cannot guess at
    the root password from the network.

    Disallow root login remotely? (Press y|Y for Yes, any other key for No) : n　　//不接受root远程登录账号

     ... skipping.
    By default, MySQL comes with a database named 'test' that
    anyone can access. This is also intended only for testing,
    and should be removed before moving into a production
    environment.


    Remove test database and access to it? (Press y|Y for Yes, any other key for No) : y　　//删除text数据库
     - Dropping test database...
    Success.

     - Removing privileges on test database...
    Success.

    Reloading the privilege tables will ensure that all changes
    made so far will take effect immediately.

    Reload privilege tables now? (Press y|Y for Yes, any other key for No) : y
    Success.

    All done!
    ```

#### MySQL忘记密码卸载
- `brew remove mysql`

- `launchctl unload -w ~/Library/LaunchAgents/com.mysql.mysqld.plist`

- `rm ~/Library/LaunchAgents/com.mysql.mysqld.plist`

- `sudo rm -rf /usr/local/var/mysql`

