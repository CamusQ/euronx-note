# JDBC
## 连接MySQL
* 导入jar

* 添加代码
```java
  //新版驱动名称
  String driver = "com.mysql.cj.jdbc.Driver";	
  //手动设置时区，编码，SSL
  String URL = "jdbc:mysql://localhost:3306/student?" 
  + "serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8&useSSL=false";
```

## 使用jdbc连接SQL Server 2008
* 打开telnet

在控制面板的程序和功能中打开windows功能

![](pictures/jdbc/打开telnet.PNG )

勾选全部telnet客户端

![](../pictures/jdbc/urx.png)

* 打开端口
