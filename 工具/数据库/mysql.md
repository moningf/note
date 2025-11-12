# SQL命令
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
CREATE TABLE 表名 (
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
![[file-20251004163757267.png]]

![[file-20251004165129612.png]]

# 函数
## 字符串函数
1. CONCAT(S1,S2,S3,...,Sn)    ---字符串拼接
2. LOWER(S1)                           ---转化为小写
3. UPPER(S1)                            ---转化为大写
4. LPAD(str,n,pad)                    ---左填充,用字符串pad对str左边进行填充,达到n个字符串长度
5. RPAD(str,n,pad)                    ---右填充,用字符串pad对str右边进行填充,达到n个字符串长度
6. TRIM(str)                               ---去掉字符串头部和尾部的空格
7. SUBSTRING(str,start,len)     ---返回从字符串str从start位置起的len个长度的字符串

## 数值函数

## 日期函数
## 流程函数


# 约束
![[file-20251029195253310.png]]

![[file-20251029201146314.png]]

![[file-20251029201407701.png]]


## 多表查询
![[file-20251029203319708.png]]

## 事务隔离级别


