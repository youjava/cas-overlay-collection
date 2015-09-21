在cas-overlay基础上, 根据文档配置的支持oauth 2.0协议的服务端。
cas文档：http://jasig.github.io/cas/4.0.x/index.html
cas构建基础：https://github.com/lansheng228/cas-overlay
构建命令：mvn clean package
将生成的war包，放到/var/lib/tomcat7/webapps/下， 重启tomcat。

在mysql数据库上新建方案cas,在cas上建立表cas_user, 并插入测试数据.
create table cas_user(
    id int(4) not null primary key auto_increment,
    username char(20) not null,
    password char(255) not null,
    enable bool default true);

insert into cas_user values(1,'tom',md5('tom'), true),(2,'jim',md5('jim'), true), (3,'simba', md5('simba'), true);

根据实际情况配置deployerConfigContext.xml中的mysql管理员用户名和密码。

访问https://localhost:8443/cas，进入登录界面，输入测试的用户名和密码，登录成功。
