# 命令
## DDL(Data Definition language)
数据定义语言
### 数据库:
```sql
SHOW DATABASES;

CREATE DATABASE (IF NOT EXISTS) 数据库名称;

DROP DATABASE (IF NOT EXISTS) 数据库;

SELECT DATABASE(); --查看现在使用的数据库

USE 数据库名称;
```
### 表:
```sql
--创建
CREAT TABLE 表名 (
	字段一 数据类型,
	字段二 数据类型
);

--查询
SHOW TABLES;
DESC 表名;

--修改
ALTER TABLE 表名 RENAME TO 新表名;
ALTER TABLE 表名 ADD 列名 新列名;
ALTER TABLE 表名 MODIFY 列名 新数据结构;
ALTER TABLE 表名 CHANGE 列名 新列名;
ALTER TABLE 表名 DROP 列名;

--删除
DROP TABLE (IF EXISTS) 表名;

```

## DML(Data Manipulation Language)
数据操作语言
```SQL
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

UPDATE table_name SET column1=value1,column2=value2,... [WHERE 条件];

DELETE FROM table_name FROM table_name [WHERE 条件];
```

## DQl(Data Query Language)
数据查询语言
![[屏幕截图_20250924_132715.png]]
## DCL(Data Control Language)
数据控制语言
