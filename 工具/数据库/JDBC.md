java DataBase connectivity
**java语言操作数据库**
![[屏幕截图_20250924_134642.png]]
# JDBC快速入门
```java
 //1. 注册驱动
 Class.forName("com.mysql.jdbc.Driver");
 //2. 获取连接
 Connection conn = DriverManager.getConnection(url,username,password);
 //3.定义SQL语句
 String sql = "update ...";
 //4. 获取执行sql对象
 Statement stmt = conn.createStatement();
 //5. 执行sql对象
 stmt.executeUpdate(sql);
 //6.处理返回结果
 //7. 释放资源
 stmt.close();
 conn.close();
```

# JDBC API详解
## DriverManager
>[API](https://docs.oracle.com/en/java/javase/17/docs/api/java.sql/java/sql/DriverManager.html)
  
驱动管理类
1. 注册驱动
2. 获取数据库连接
## Connection
1. 获取执行SQL的对象
2. 管理事务
![[file-20251029190622198.png]]
![[file-20251029190630871.png]]


## Statement
![[file-20251030202424249.png]]

## ResultSet
![[file-20251030203725877.png]]

## PreparedStatement
![[file-20251030214736611.png]]
# 数据库连接池
 ![[file-20251031145141574.png]]
