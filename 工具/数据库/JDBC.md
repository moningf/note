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
驱动管理类
1. 注册驱动
2. 获取数据库连接
## Connection

## Statement

## ResultSet

## PreparedStatement

# 数据库连接池
 