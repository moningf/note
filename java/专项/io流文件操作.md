## Stream分类
1. 以流的方向分类
- 输入流
- 输出流
1. 以操作文件类型分类
- 字节流(所有的文件) inputStream outputStream
- 字符流(纯文本文件) Reader Writer
以上四个类都是抽象类

他们的子类
inputStream-> FileinputStream
outStream-> FileoutStream


#字节输入流
# 字节输出流
## file.write()
```java
FileoutputStream file = new FileputStream("address"); //就是该行格式化的文件
//在address中,windows和linux的路径有区别,linux下为'/',windows中为转义字符'\\'
file.write();
file.close();
```

```java
void file.write(byte b);  
void file.write(byte[] b);
void file.write(byte[] b, int off ,int len); //off为起始索引,len为长度
```

细节:
1. 创建字节输出流对象
	1. 参数是字符串表示的路径或者File对象都是可以的
	2. 如果文件不存在会创建一个新的文件,但是要保证父级路径存在
	3. 如果文件存在则会清空文件
2. 写数据
	1. write方法为整形,但是实际上写到本地文件中是整数在ASCII上对应的字符
	2. 97 --> a 
3. 释放资源


### 如何做到换行写和续写
#### 换行写
再写一个换行符即可
```java
file.write(\r\n) //window
file.write(\n)   //linux
file.write(\r)   //mac
```

windows 上也可以只写\r或\n,java底层会自动补全

#### 续写
```java
FileoutputStream file = new FileputStream("address",boolen); //后面传入ture时就能打开续写,默认为false
```

 
# 字节输入流

## file.read()

```java
FileInputStream file = new FileInputStream("address");
int b = file.read();
System.out.println((char)b);
```

细节:

	一次只会读取一个字符的ASCII值
	如果读不到了就会返回-1
	如果文件不存在,直接报错


# 文件拷贝的方法
1. 使用FileOutStream和FileInputStream,并通过file.read(byte[])和file.write(byte[])来完成


# io流中的不同jdk版本捕获异常的方法

```java
try{
	FileOutStream file = new FileOutStream("a.txt");
	file.write(97);
	} catch (IOException e){
	e.printStackTrace()	;
	}
	finally{
	file.close;    //filnally语句一定会被执行,除非jvm虚拟机关闭
	}
```

jdk7
```java
	try (FileInputStream fis =new FileInputStream(address);
	FileOutputStream fos = new FileOutputStream(address) ){
	int len;
	byte[] bytes = new byte[1024*1024*5];
	while((len = fis.read(bytes) != -1){
		fos.write(bytes,0,len);
	}
	}
		catch(IOException e){
	 e.printStackTrace();
	}
```

jdk9

```java
FileInputStream fis =new FileInputStream(address);
	FileOutputStream fos = new FileOutputStream(address);
	try (fis,fos){
	int len;
	byte[] bytes = new byte[1024*1024*5];
	while((len = fis.read(bytes) != -1){
		fos.write(bytes,0,len);
	}
	}
		catch(IOException e){
	 e.printStackTrace();
	}

```

实际开发中会直接throws抛出异常,后期会统一管理异常



