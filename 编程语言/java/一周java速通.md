## one day

### 目标：学习基本语法（条件语句和循环语句）

#### Scanner
next   扫描一行输入，遇到空格和换行符才结束扫描
nextline  扫描一行输入, 遇到换行符才结束扫描
这两个都是String类型

nextInt 扫描一行输入, 得到一个Int类型值

写了一个计算器类
```java
import java.nio.channels.ScatteringByteChannel;
import java.util.Scanner;
public class Calculator {
    public static void main(String[] args) {
        int a,b;
        double sum=0;
        char op=0;
        Scanner sc = new Scanner(System.in);
//        a = sc.nextInt();
//        op = sc.next().charAt(0);
//        b = sc.nextInt();
        String input = sc.nextLine().replaceAll(" ","");
        int opindex=0;
        for(int i = 0; i < input.length(); i++){
            char ch = input.charAt(i);
            if("+-*/".indexOf(ch) != -1){
                op = ch;
                opindex = i;
                break;
            }}
        String left = input.substring(0, opindex);
        String right = input.substring(opindex + 1);

        double num1 = Double.parseDouble(left);     //此处导入了新的包实现字符串转换为数字
        double num2 = Double.parseDouble(right);


        switch (op) {
            case '+':sum = num1 + num2;break;
            case '-':sum = num1 - num2;break;
            case '*':sum = num1 * num2;break;
            case '/':sum = num1 / num2;break;
               // try{sum = num1 / num2;}
               // catch (ArithmeticException e){System.out.println("Division by zero,add the num2 again");
               // num2 = sc.nextInt();
               // sum = num1 / num2;
               // }catch(){System.out.println("Division by zero,add the num2 again");
               //     num2 = sc.nextInt();
               //     sum = num1 / num2;}
               //break;
        }
        System.out.println(sum);
    }
}

```

问题:
使用double类型做除法时不会抛出异常，java会返回Infinity,因此需要显示的判断除数是否为零


写了一个猜大小的类，用到了whlie和for以及break和continue的标签
```java
import java.util.Scanner;

public class bigorsmall {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int guass = 100;
        int yournum;

        first:for (int i = 0; i < 3; i++) {
            second:while(true) {
                yournum = sc.nextInt();
                if (yournum > guass) {
                    System.out.println("it's too big");
                    continue first;
                } else if (yournum == guass) {
                    System.out.println("good!!!!");
                    break;
                } else {
                    System.out.println("it's too small");
                    continue second;
                }
                System.out.println("hello");        //"不可到达的代码"是Java编译器报出的一个编译时错误，表示程序中存在永远不会被执行的代码。这是Java语言设计中的一项重要安全检查，目的是帮助开发者避免逻辑错误。
            }
        }
    }
}


```


## two day

### 目标： 学习数组，类与对象，接口和抽象类

#### 数组
- 写一个数组，以及遍历的类
```java
public class arr {
    public static void main(String[] args) {
        int[]a;
        int b[];
        a = new int[10];
        b = new int[10];


        for(int i=0;i<10;i++){
            a[i]=i+1;
        }
        for(int i=0;i<a.length;i++){
            System.out.println(a[i]+" ");
        }
        for(int i=0;i<10;i++){
            b[i]=i+1;
        }
        
        for(int num:b){
            System.out.println(num+"\t");
        }
        System.out.println(" ");
        System.out.println("第一行\n第二行\t带制表符");
        System.out.println("他说：\"你好，世界！\"");
        System.out.println("文件路径：C:\\Program Files\\Java");
        System.out.println("123\b456"); // 显示为"12456"（删除了3）

        System.out.println("\u03A9"); // 输出：Ω
        System.out.println("\123");   // 输出：S (八进制123=83='S')

    }
}

```
遍历数组的两种方式，以及转义字符的应用
同时认识到print（不会自动换行）和println（会自动换行）的区别


写一个二维数组及遍历的类

--通过增强型for循环和普通循环实现遍历二维数组
```java
public class doublearr {
    public static void main(String[] args) {
        int[][] a = new int[10][10];
        System.out.println(a.length);
        System.out.println(a[1].length);
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                a[i][j] = i*10+j+1;
            }
        }
        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < a[i].length; j++) {
                System.out.print(a[i][j]+"\t");
            }
            System.out.println();
        }


        for(int[]temp:a){
            for(int num:temp){
                System.out.print(num+"\t");
            }
            System.out.println();
        }

    }
}

```
#### 类与对象
写一个学生类，记录学生的姓名，性别，成绩
```java
class students{
    String name;
    int age;
    int score;
}
public class Student {
    public static void main(String[] args) {
    students s = new students();
    s.name = "John";
    s.age = 20;
    s.score = 50;
    }
}

```





1. 写一个 `Animal` 类

- 属性：`name`
    
- 方法：`eat()`
    
子类 `Cat`、`Dog` 继承 `Animal`

- 自己加一个新方法（如 `meow()` 或 `bark()`）
	  
- 重写 `eat()` 方法

在 `main` 方法里：

- 创建一个 `Dog` 和一个 `Cat` 对象
    
- 分别调用 `eat()` 和特有方法，验证继承效果
```java
class animal{
    String name;
    void eat() {
        System.out.println("eat");
    }
    animal(String name)
    {
        this.name=name;
    }
}
public class dog extends animal{
void bark(){
    System.out.println("bark");
}
dog(String name){
    super(name);
}
//重写eat方法，若不重写则默认执行父类的eat
    void eat() {
        System.out.println(name + " eats dog food.");
    }

    public static void main(String[] args) {
        dog d = new dog("alice");//也可以通过animal父类进行实例化
        //animal a = new dog("tom");
        d.bark();
        d.eat();
        System.out.println(d.name);
    }
}

```




写一个接口 `Flyable`，有一个方法 `fly()`； 写一个类 `Bird` 实现这个接口。
```java
public interface flyable {
     void fly();         //默认为public abstract
}

```
```java
public class bird implements flyable{
    public void fly()           //抽象方法必须重写
    {
        System.out.println("flying");
    }
    public static void main(String[] args) {
        bird a = new bird();
        a.fly();
    }
}

```

写一个抽象类 `Animal`，有一个抽象方法 `makeSound()`，然后子类 `Dog` 和 `Cat` 实现这个方法。
```java
abstract class  amin{
    String name;
    void makesound(){
        System.out.println("makesound");
    }
    abstract void sound();

    amin(String name){
        this.name=name;
    }
}
public class cat extends amin{
    void sound(){
        System.out.println("miaow");
    }
    cat(String name){
        super(name);
    }

    public static void main(String[] args) {
        cat a=new cat("kitty");
        a.makesound();
        a.sound();
    }
}

```




## Third day

### 昨日内容加强

#### 数组
- **动态输入数组内容（Scanner）**
	目前有五种实现
	1. 使用Scanner动态输入数组
	2. 使用BufferedReader动态输入数组(适合大量输入数据)
	3. 动态输入字符串数组
	4. 动态调整数组大小（模拟Arraylist)
	5. 使用Arraylist实现真正的动态数组
first
```java
import java.util.Scanner;
public class array {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] arr = new int[10];
        for (int i = 0; i < 10; i++) {
            arr[i] = sc.nextInt();
        }

        for (int i = 0; i < 10; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

second
```java

```


- **求数组最大值、平均值、反转数组**
    
- **写一个打印九九乘法表的小练习**

#### 类与对象

- 你可以给 `students` 类加个构造方法，练习下构造器的使用。
    
- 把类放在单独文件里编译试试（感受下多文件项目的结构）
```java
class students{
    String name;
    int age;
    int score;

    students(String name, int age, int score){
        System.out.println("second");
        this.name = name;
        this.age = age;
        this.score = score;
    }
    students(){
        System.out.println("first");
    }
}
public class Student {
    public static void main(String[] args) {
        students s = new students();
        s.name = "John";
        s.age = 20;
        s.score = 50;
        students s1 = new students("moningf",18,100);
    }
}
```

#### 继承和方法重写

- 可以练练 **多态**：用 `Animal d = new Dog("alice");` 看看效果
    
- 再增加一个 `Cat` 类，练习用数组 `Animal[]` 来存放多个子类对象，练习遍历和调用

**发现当用数组存放子类时，子类只有在初始化之后才能调用方法，即使已经通过数组分配了内存**
```java
class animal {
    animal(String animal_name) {
        this.name = animal_name;
    }
    String name;
    void eat() {
        System.out.println("eat");
    }
    void sleep() {
        System.out.println("sleep");
    }
}

class dog extends animal {
    void eat() {
        System.out.println("eatbond");
    }
    dog(String animal_name) {
        super(animal_name);
    }
}

class cat extends animal {
    void eat() {
        System.out.println("eatfish");
    }
    cat(String animal_name) {
        super(animal_name);
    }
}

public class animaltest {
    public static void main(String[] args) {
        animal a = new dog("diandian");
        animal b = new cat("kitty");
        a.eat();
        a.sleep();
        b.eat();
        b.sleep();

        animal[] arr = new dog[10];
        arr[0] = new dog("dog");
        arr[0].sleep();
    }
}
```

#### 接口 & 抽象类部分

- 多写几个实现接口的类，例如 `Plane`、`Superman`
    
- 将抽象类 + 接口结合使用：抽象类 `Animal` 实现 `Movable` 接口，然后子类继承它
```java
public interface moveable {
    void move();
}

//抽象父类+接口
//必须实现接口的方法
abstract class anim implements moveable {
    String animal_name;
    public abstract void move();
    abstract void eat();
    anim(String animal_name){
        this.animal_name = animal_name;
    }
}
//三个文件

public class human extends anim{
    public human(String animal_name){
        super(animal_name);
    }

    public void move(){
        System.out.println("Human move");
    }
	    //必须重写抽象类中的所有方法，否则自身也必须是抽象类
    public void eat(){
        System.out.println("Human eat");
    }


    public static void main(String[] args) {
        anim a = new human("moningf");
        a.move();
        a.eat();
    }
}

```

### 今日study

目标：
	实战类 + 多态练习 + 静态/包 的使用

### 实战建议一：设计一个雇员系统（Employee System）

- 抽象类 `Employee`：包含 name、salary，抽象方法 `work()`
    
- 子类：`Manager`（多一个 bonus）、`Coder`
    
- 接口 `IPayable`，有方法 `getPay()`：计算实发工资
    

练习点：

- 抽象类 + 接口结合使用
    
- 方法重写
    
- 多态数组 `Employee[] emps = new Employee[2];`

```java
//第一个文件
public interface IPayable {
    void getpay();
}

//第二个文件
abstract class Employee implements IPayable{
    String name;
    int salary;
    public abstract void work();
    void sleep(){
        System.out.println("sleep");
    }

    @Override
    public void getpay() {
        System.out.println("your pay is 1000");
    }
}

//第三个文件
class Manager extends Employee {
    public void work() {
        System.out.println("Manager work");
    }
}
class Coder extends Employee {
    public void work() {
        System.out.println("Coder work");
    }
}


public class Worker {
    public static void main(String[] args) {
        Employee emp = new Manager();
        emp.work();
        emp.getpay();
        emp.sleep();
        Employee emp2 = new Coder();
        emp2.work();
        emp2.getpay();
        emp2.sleep();

    }
}
```

总结：
抽象类可以写方法实现，但是抽象方法不能写，接口的方法也不能写实现，同时接口中的变量默认修饰符为public static final,并且需要在定义时就要初始化，可以认为是常量.

### 实战建议二：练习多态和向上转型

**向上转型（Upcasting）**：子类转父类（自动进行，安全）
通过向上转型，类型为父类，那么它不能访问子类特有的方法，只能访问父类已经有的方法，同时如果子类覆写了该方法，则调用子类的方法，体现了多态意图
```java
Animal a1 = new Dog("Buddy");
Animal a2 = new Cat("Kitty");

a1.eat();  // Dog 的 eat()
a2.eat();  // Cat 的 eat()
```

理解 `instanceof` 和类型转换（向下转型）
特点：可以使用子类特有的方法
1. **显式转换**：必须使用强制类型转换语法 `(子类类型)`
    
2. **有风险**：可能抛出 `ClassCastException`
    
3. **需要类型检查**：通常应先使用 `instanceof` 进行检查
```java
 animal a1 = new Dog();    // 向上转型隐式进行
if (a1 instanceof Dog) {  // 对象 instanceof 类型
    Dog d = (Dog) a1;     // ai为dog类型的,d为a1的引用，并没有开辟新的空间，只是改变了标识，让编译器认为d为dog类型
    d.bark();
}
```


### 📦 实战建议三：了解 static / 包结构 / import 使用
```java
public class MyMath {
    public static int add(int a, int b) {
        return a + b;
    }
}
```
调用：
```java
int sum = MyMath.add(1, 2);
```


## fourth day

今日目标:
java集合框架,异常处理机制
### 一. java集合框架

|        |                                    |
| ------ | ---------------------------------- |
| `List` | 有序、可重复，如 `ArrayList`, `LinkedList` |
|        |                                    |

|       |                               |
| ----- | ----------------------------- |
| `Set` | 无序、不重复，如 `HashSet`, `TreeSet` |

|       |                            |
| ----- | -------------------------- |
| `Map` | 键值对，如 `HashMap`, `TreeMap` |

#### 🔹 常见类

- `ArrayList`：底层是数组，访问快，增删慢。
    
- `LinkedList`：链表结构，访问慢，增删快。
    
- `HashSet`：基于哈希表，不允许重复。
    
- `HashMap`：存储键值对，键唯一。
    

#### 🔹 方法掌握

- `add()`、`get()`、`remove()`、`contains()`、`size()` 等
    
- `Map` 的 `put()`、`get()`、`keySet()`、`values()`、`entrySet()`


### 二. 异常处理机制
#### 异常分类

- **编译时异常**：必须处理，如 `IOException`
    
- **运行时异常**：不一定处理，如 `NullPointerException`
    

#### 🔹 关键字
```java
try {
    // 可能抛异常的代码
} catch (ExceptionType e) {
    // 异常处理e.printStackTrace();
} finally {
    // 无论是否异常，都会执行（释放资源）
}
```

自定义异常
```java
class MyException extends Exception {
    public MyException(String message) {
        super(message);
    } 
}
```


实战练习
1. **学生管理系统**里加点数据结构的应用，比如用 `HashMap<Integer, Student>` 存学生信息。
  
2. 写个简单的程序练习：

 - 模拟一个购物车系统，使用 `List` 存物品。
  
 - 给商品价格计算加个 try-catch，处理非法输入异常。

```java

```



多线程基础(线程&并发)
[[线程|笔记]]
java文件操作(io流)
[[io流文件操作|笔记]]
