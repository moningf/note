---
tags:
  - java
---
## 多线程
### 三种实现方式
1. 
通过继承Thread类,重写run()方法即可
可以通过调用该类的start方法来启动线程

2. 
通过实现Runable接口重写run()方法,然后通过Thread(Runable)构造函数,构造Thread类
调用该类的start方法即可

3. 
1 通过实现Callable<>接口,重写call()方法,
2 通过FutureTask类来接收实现Callable的类
3 然后通过Thread(Runable)构造方法,构造Thread类
4 通过 FutureTask类中的get方法即可获取结果
该方法其实是因为FutureTask类实现了RunnableFuture<  V>接口,该接口又继承了Runable和Future接口

### Thread的常用方法
![[image.png]]

### 线程生命周期
![[image.png]]

### 同步(synchronized)
同步代码块: 注意:类对象对应的一把锁,如果定义的类对象不唯一,则锁无效
```java
synchronized(类对象){
需要上锁的代码
}
```
同步方法:
```java
(synchronized) public (synchronized) void func(){   //这两个位置都可以
需要上锁的方法
}
```
注意锁对象不能自己指定
静态方法:锁对象为该类的字节码对象
非静态方法:锁对象为调用者的类对象

### Lock锁
Lock锁是提供的手动上锁的方法
Lock是接口,不能实例化,所以要使用它的实现类ReenTrantLock

```java
Lock l = new ReenTrantLock();
l.lock();   //上锁
l.unlock();   //解锁
```

同时有问题的是在死循环中上锁,在结束时会导致带着锁离开
```java
while(true){
l.lock();   //上锁
---
锁上的逻辑
---
l.unlock();   //解锁
}
```
在此期间,跳出循环的逻辑是写在锁上的逻辑上的,会导致跳出时,锁未解锁
```java
while(true){
l.lock();   //上锁

try{
		---
		锁上的逻辑
		---
	}
catch(){

		}
finally{
l.unlock();   //解锁
}

}
```
这样就实现了上锁必解锁

### 等待唤醒机制(生产者与消费者)

- 消费者发现队列空 → 调用 wait() → 释放锁。
    
- 生产者获得锁 → 放入数据 → notifyAll() → 唤醒消费者。
    
- 当前生产者退出同步块 → 释放锁。
    
- 被唤醒的消费者获得锁 → 继续消费。

 生产者:
```java
while(true){
	synchronized(lock){      //上锁
	while(生产为非空) lock.wait();  //等待
	||生产||
	lock.notifyAll();
	}
}
```

消费者:
```java
while(true){
	synchronized(lock){      //上锁
	while(生产为空) lock.wait();  //等待
	||消费||
	lock.notifyAll();
	}
}
```

如果要加入结束条件,需要在上锁之后,等待之前加入判断,防止他直接等待,导致代码一直无法结束


通过阻塞队列书写:
![[image-1.png]]

 