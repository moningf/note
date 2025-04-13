语法:
```java
switch(表达式) {
	case 值1:
		语句体;
		break;
	
	case 值2:
		语句体;
		break;
	
	case 值3:
		语句体;
		break;
	...
	defalut:
		 语句体;
		 break;
}
```

在jdk12之后优化了switch语句
```java
switch(语句体){
	case 1 -> {
		语句体;
	}
	case 2,3-> {             //case里面可以写多个要匹配的值,(上一个写法也行)
		语句体;
	}
	case 4 -> 语句体;        //括号可以省略
	
	default -> {
		语句体;
	}
}
```
注意:
如果没有break,那么case就会继续执行,导致case穿透,知道遇到break才会结束