## 包
==包就是文件夹.用来管理各种不同功能的Java类,方便后期代码维护==

- 包名的规则:
		公司域名反写+包的作用(需要全部英文小写,见名知意)

- 全类名:
`package com.moningf.myclass`

- 使用其他包的规则:
	- 使用同一个包中的类时,不需要导包
	- 使用java.lang包中的类时,不需要导包
	- 其他情况都需要导包
	- 如果同时使用两个包中的同名类,需要用全类名



## final
1. 方法:表明该方法为最终方法,不能被重写
2. 类:表明该类是最终类,不能被继承
3. 变量:叫做常量,只能被赋值一次(可以不在定义时赋值)

### 常量的命名规则
- 单个单词:全部大写
- 多个单词:全部大写,单词之间用下划线隔开

细节:
final修饰的变量是基本类型:那么变量储存的数据值不能发生改变
final修饰的变量是引用类型:记录的地址值不能改变,内部的属性可变

==字符串为private,final修饰,因此不能修改地址值,并且在外部无法修改字符串内容== 


## 权限修饰符

- 权限修饰符:是用来控制一个成员能够被访问的范围的
- 可以修饰变量成员,方法,构造方法,内部类

### 分类
- private
- 空着不写
- protected
- public

1. 在同一个类中:都可以访问
2. 在同一个包中:只有private的不能访问
3. 不同包下的子类:只有public和protected的可以访问
4. 在不同包下的无关类:只有public可以访问















