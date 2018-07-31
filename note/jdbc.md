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
