



[TOC]

# JAVA基础



## 基本数据类型

> ***java提供了八种基本类型***
>
> ***六种数字类型（四个整数型，两个浮点型）***
>
> ***一种字符类型***
>
> ***一种布尔型***

------

**byte**：byte数据类型是8位、有符号的，以二进制补码表示的整数

**short**：short数据类型是16位、有符号的以二进制补码表示的整数

**int**：int数据类型是32位、有符号表示的二进制补码表示的整数

**long**：long数据类型是64位、有符号以二进制补码表示的整数

**float**：float数据类型是单精度、32位、符合IEEE 754标准的浮点数

**double**：double数据类型是双精度、64位、符合ieee 754标准的浮点数

**boolean**：Boolean数据类型表示一位的信息

**char**：char类型是一个单一的16位Unicode字符

```java
public class Test{
    static boolean bool;
    static byte by;
    static char ch;
    static double d;
    static float f;
    static int i;
    static long l;
    static short sh;
    static String str;

    public static void main(String[] args){
        System.out.println("Bool: "+bool);
        System.out.println("Byte: "+by);
        System.out.println("Character: "+ch);
        System.out.println("Double: "+d);
        System.out.println("Float: "+f);
        System.out.println("Integer: "+i);
        System.out.println("Long: "+l);
        System.out.println("Short: "+sh);
        System.out.println("String: "+str);
    }
}

```

## Character方法

|      方法      |                  描述                  |
| :------------: | :------------------------------------: |
|   isLetter()   |             是否是一个字母             |
|   isDigit()    |             是否是一个字符             |
| isWhitespace() |           是否是一个空白字符           |
| isUpperCase()  |             是否是大写字母             |
| isLowerCase()  |             是否是小写字母             |
| toUpperCase()  |            指定字母大写形式            |
| toLowerCase()  |            指定字母小写形式            |
|   toString()   | 返回字符的字符串形式，字符串长度仅为 1 |

## String方法

```java
public class Test{
    public static void main(String args[]){
        StringBuffer sBuffer = new StringBuffer("abcdefg");
        sBuffer.append("123");
        sBuffer.append("456");
        sBuffer.append("789");
        System.out.println(sBuffer);
    }
}

// 输出结果：abcdefg123456789
```

## 数组

**声明数组变量**

```java
dataType[] arrayRefVar;   // 首选的方法
或
dataType arrayRefVar[];  // 效果相同，但不是首选方法
```

```java
public class TestArray{
    public static void main(String[] args) {
        // int size = 10;
        double[] myList = new double[10];    // 定义数组
        myList[0] = 1.0;
        myList[1] = 2.0;
        myList[2] = 3.0;
        myList[3] = 4.0;
        myList[4] = 5.0;
        myList[5] = 6.0;
        myList[6] = 7.0;
        myList[7] = 8.0;
        myList[8] = 9.0;
        myList[9] = 10.0;

        for(double i:myList){
            System.out.println(i);
        }
    }
}
```

```java
public class TestArray{
    public static void main(String[] args) {
        int[] mylist = {1,2,3,4,5,6,7,8,9,0};

        // 打印所有元素，也可以用加强型循环
        for(int i=0;i<mylist.length;i++){
            System.out.println(mylist[i]);
        }
        
        //查找最大元素
        int max = mylist[0];
        for(int i=0;i<mylist.length;i++){
            if(mylist[i]>max){
                max=mylist[i];
            }
        }
        System.out.println("Max is "+max);
    }
}
```

## Scanner类

```java
// next()
import java.util.Scanner;

public class ScannerDemo{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("next方式接收：");
        // 判断是否有输入
        if(scan.hasNext()){
            String str1 = scan.next();
            System.out.println("输入的数据为："+str1);
        }
        scan.close();
    }
}
```

```java
// nextLine()
import java.util.Scanner;
 
public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        // 从键盘接收数据
 
        // nextLine方式接收字符串
        System.out.println("nextLine方式接收：");
        // 判断是否还有输入
        if (scan.hasNextLine()) {
            String str2 = scan.nextLine();
            System.out.println("输入的数据为：" + str2);
        }
        scan.close();
    }
}
```

## 循环

while循环

```java
while( 布尔表达式 ) {
  //循环内容
}
```

```java
// 九九乘法表
public class Test{
   public static void main(String[] args) {
    
    int i = 1;
    while (i<10) {
        int j = 1;
        while(j<i+1){
            System.out.printf("%dx%d=%d  ", i,j,i*j);
            j++;
        }
        i++;
        System.out.println("\n");
    }
   }
}
```

do...while

```java
public class Test{
    public static void main(String[] args) {
        int i=0;
        int j=1;
        do{
            System.out.println(j);
            j+=2;
            i++;
        }while(i<11);
    }
}
```

for循环

```java
public class Test{
    public static void main(String[] args){
        for(int i=1;i<10;i++){
            for(int j=1;j<i+1;j++){
                System.out.printf("%dx%d=%d  ", j,i,j*i);
            }
            System.out.println("\n");
        }
    }
}
```

java增强for循环

```java
public class Test{
    public static void main(String[] args) {
        int [] numbers = {10,20,30,40,50};

        for(int x:numbers){
            System.out.println(x);
        }
        String [] names = {"a","b","c","d","e"};
        for(String name:names){
            System.out.println(name);
        }
    }
}
```

关键字：break，continue



## 判断语句

if .... else if .... else

## switch

```java
switch(expression){
    case value :
       //语句
       break; //可选
    case value :
       //语句
       break; //可选
    //你可以有任意数量的case语句
    default : //可选
       //语句
}
```

## 异常处理

```java
try {  
    // 尝试执行的代码块  
    // 可能会抛出异常的代码  
} catch (ExceptionType1 e) {  
    // 处理第一种类型异常的代码  
} catch (ExceptionType2 e) {  
    // 处理第二种类型异常的代码  
} finally {  
    // 无论是否发生异常，都会执行的代码块  
    // 通常用于资源释放，如关闭文件流等  
}
```

**通用捕获块**

```java
try {  
    // 你的代码  
} catch (Exception e) {  
    // 处理异常  
    e.printStackTrace(); // 打印堆栈跟踪信息，有助于调试  
    // 或者进行其他错误处理操作  
}
```

**抛出异常**

```java
if (someCondition) {  
    throw new Exception("这里发生了某种异常");  
}

public void someMethod() throws ExceptionType {  
    // 方法体，可能抛出ExceptionType类型的异常  
}
```

**自定义异常**

```java
public class MyCustomException extends Exception {  
    public MyCustomException(String message) {  
        super(message);  
    }  
}  
  
// 使用自定义异常  
if (someCondition) {  
    throw new MyCustomException("这里发生了自定义的异常");  
}
```

实例

```java
public class ExceptionExample {  
    public static void main(String[] args) {  
        String numberStr = "123"; // 这是一个有效的整数字符串  
        // 尝试更改numberStr的值为"abc"来看看会发生什么  
  
        try {  
            // 尝试将字符串转换为整数  
            int number = Integer.parseInt(numberStr);  
            System.out.println("转换成功，数字为: " + number);  
  
            // 这里可以放置更多可能抛出异常的代码  
            // ...  
  
        } catch (NumberFormatException e) {  
            // 如果Integer.parseInt()抛出了NumberFormatException，则执行这里的代码  
            System.out.println("发生NumberFormatException: " + e.getMessage());  
            // 可以在这里处理错误，比如给用户一个友好的提示  
            // ...  
  
        } catch (Exception e) {  
            // 这个catch块是可选的，用于捕获除NumberFormatException之外的其他异常  
            // 但在这个例子中，我们不需要它，因为Integer.parseInt()只可能抛出NumberFormatException  
            // 如果添加了其他可能抛出其他类型异常的代码，那么这个catch块就很有用了  
            System.out.println("发生了一个未知的异常: " + e.getMessage());  
            // ...  
  
        } finally {  
            // 无论是否发生异常，finally块中的代码都会被执行  
            // 这通常用于释放资源，比如关闭文件、数据库连接等  
            // 在这个例子中，我们不需要做这些事情，但演示了finally的用法  
            System.out.println("程序继续执行...");  
            // ...  
  
        }  
  
        // 注意：finally块之后（如果有的话）的代码将继续执行，除非在try或catch块中使用了System.exit()等方法提前退出程序  
    }  
}
```



# 面向对象

## **1、继承：**

### **extends关键字**

在 Java 中，类的继承是单一继承，也就是说，一个子类只能拥有一个父类，所以 extends 只能继承一个类。

```Java
// main主函数
public class Main{
    public static void main(String[] args) {
        // 类名 实例名 = 创建的对象
        // 类名 实例名 = new 类名(构造函数的参数)
        Dog brean = new Dog("brean", 0);
        Cat mimi = new Cat("mimi", 1);
        Animal a = new Dog("1", 0);

        brean.eat();
        brean.sleep();
        brean.introduction();
        
        System.out.println("\n");

        mimi.eat();
        mimi.sleep();
        mimi.introduction();

        System.out.println("\n");

        a.eat();
        a.sleep();
        a.introduction();
    }
}

// 公共父类
class Animal{
    private String name;  // 成员变量
    private int id;
    
    public Animal(String name,int id){
        this.name = name;
        this.id = id;
    }
    public void eat(){
        System.out.println(name+"吃");
    }
    public void sleep(){
        System.out.println(name+"睡");
    }
    public void introduction(){
        System.out.println("id 是: "+id+" name 是："+name);
    }
}
// 子类1
class Dog extends Animal{
    public Dog(String name,int id){
        super(name,id); // 调用父类
    }
}
// 子类2
class Cat extends Animal{
    public Cat(String name,int id){
        super(name,id);
    }
}
```

### **implements关键字：**

使用 implements 关键字可以变相的使java具有多继承的特性，使用范围为类继承接口的情况，可以同时继承多个接口（接口跟接口之间采用逗号分隔）。

```Java

// 测试类  
public class Main {  
    public static void main(String[] args) {  
        Dog myDog = new Dog("旺财", 5);  
        myDog.eat();  
        myDog.sleep();  
        System.out.println("狗的年龄是：" + myDog.getAge());  
    }  
}

class Animal {  
    private String name;  
    private int age;  
  
    public Animal(String name, int age) {  
        this.name = name;  
        this.age = age;  
    }  
  
    public void sleep() {  
        System.out.println(name + "睡");  
    }  
  
    public int getAge() { 
        return age;  
    }  
  
    public String getName() {
        return name;  
    }  
}  
  
// 定义一个接口来表示犬科动物特有的行为  
interface CanoideaBehavior {  
    void eat();  
}  
  
// 犬类继承自 Animal 并实现 CanoideaBehavior 接口  
class Dog extends Animal implements CanoideaBehavior {  
    public Dog(String name, int age) {  
        super(name, age); // 调用父类的构造函数  
    }  
  
    @Override  
    public void eat() {  
        System.out.println(getName() + "吃"); // 使用从 Animal 继承的 getName() 方法  
    }  
}  
```

### **super 与 this 关键字**

super关键字：我们可以通过super关键字来实现对父类成员的访问，用来引用当前对象的父类。

this关键字：指向自己的引用。

```Java
public class Test{
    public static void main(String[] args){
        
        Animal a = new Animal();
        a.eat();
        
        Dog d = new Dog();
        d.eat();
        d.eatTest();
    }
}
class Animal{
    void eat(){
        System.out.println("Animal eat");
    }
}
class Dog extends Animal{
    void eat(){
        System.out.println("Dog eat");
    }
    void eatTest(){
        this.eat();       // 调用自己的方法
        super.eat();     // 调用父类的方法
    }
}
```

单继承：

class B  -> class A

```java
public class A{
    ......
}
public class B extends A{
    ......
}
```

多重继承：

class C -> class B -> class A

```java
public class A{
    ......
}
public class B extends A{
    ......
}
public class C extends B{
    ......
}
```

不同类继承同一个类：

class B -> class A <- class C

```java
public class A{
    ......
}
public class B extends A{
    ......
}
public class C extends A{
    ......
}
```

## **overloading(重载)：**

```java
// bark是一个实例方法不能通过类名来调用。
// 实例方法也称非静态（static）方法。
class TestDog{
    public static void main(String[] args) {
        TestDog abc = new TestDog();   // 创建TestDog的一个实例
        abc.bark();
        abc.bark(5);
    }
// 创建一个实例方法（非静态方法）
    public void bark(){
        System.out.println("woof");
    }
// 创建另一个名称一样的实例方法（非静态方法）
    public void bark(int num){
        for(int i=0;i<num;i++){
            System.out.println("woofffff");
        }
    }
}
```

## **overriding(重写)：**

```java
/*
尽管 TestDog 是 Hound 的父类，但Java允许您将一个子类的对象（在这个例子中是 Hound）赋值给一个父类类型的变量
*/
public class Main{
    public static void main(String[] args) {
        TestDog a = new TestDog();
        TestDog b = new Hound();
        // Hound b = new Hound();
        a.bark();
        b.bark();
        // b.sniff();
    }
}

class TestDog{
    public void bark(){
        System.out.println("woof");
    }
}
class Hound extends TestDog{
    public void sniff(){
        System.out.println("sniff");
    }
    public void bark(){
        System.out.println("bowl");
    }
}
```

## **多态：**

多态是同一个行为具有多个不同表现形式或形态的能力。

多态就是同一个接口，使用不同的实例而执行不同操作

```java

public class Test{
    public static void show(Animal a){
        a.eat();
        // 类型判断
        if (a instanceof Cat){   // 猫做的事
            Cat c = (Cat)a;
            c.work();
        }else if (a instanceof Dog){   // 狗做的事
            Dog c = (Dog)a;
            c.work();
        }
    }
    public static void main(String[] args) {
        show(new Cat());
        show(new Dog());

        Animal a = new Cat();
        a.eat();public class Test{
    public static void show(Animal a){
        a.eat();
        // 类型判断
        if (a instanceof Cat){   // 猫做的事
            Cat c = (Cat)a;  // 指定了类型转换的目标类型
            c.work();
        }else if (a instanceof Dog){   // 狗做的事
            Dog c = (Dog)a;
            c.work();
        }
    }
    public static void main(String[] args) {
        show(new Cat());
        show(new Dog());

        Animal a = new Cat();
        a.eat();
        Cat c = (Cat)a;
        c.work();
    }
}

// 抽象类，不能被实例化
abstract class Animal{
    abstract void eat();
}

class Cat extends Animal{
    public void eat(){
        System.out.println("吃鱼");
    }
    public void work(){
        System.out.println("抓老鼠");
    }
}

class Dog extends Animal{
    public void eat(){
        System.out.println("吃骨头");
    }
    public void work(){
        System.out.println("看家");
    }
}
        Cat c = (Cat)a;
        c.work();
    }
}

// 抽象类，不能被实例化
abstract class Animal{
    abstract void eat();
}

class Cat extends Animal{
    public void eat(){
        System.out.println("吃鱼");
    }
    public void work(){
        System.out.println("抓老鼠");
    }
}

class Dog extends Animal{
    public void eat(){
        System.out.println("吃骨头");
    }
    public void work(){
        System.out.println("看家");
    }
}
```

show()方法里面：

Cat c = (Cat)a;

“我想将`a`（它目前被声明为`Animal`类型，但实际上可能是一个`Cat`对象的引用）转换为`Cat`类型，并将转换后的结果赋值给新声明的`Cat`类型变量`c`。”

instanceof 

`instanceof` 是 Java 中的一个二元操作符，用于测试左边的对象是否是右边类或接口的实例。如果左边的对象是右边类或接口的实例，或者右边类是左边对象类的父类（包括父类的父类，一直到`Object`类），则表达式的结果为 `true`；否则，结果为 `false`。

( 对象  instanceof  类 )

( 对象  instanceof  接口 )

### 虚函数：

虚函数的存在是为了多态。

Java 中其实没有虚函数的概念，它的普通函数就相当于 C++ 的虚函数，动态绑定是Java的默认行为。如果 Java 中不希望某个函数具有虚函数特性，可以加上 final 关键字变成非虚函数。

## JAVA抽象类

在 Java 语言中使用 abstract class 来定义抽象类。

```java
// 定义一个抽象类
abstract class Animal{
    // 定义一个抽象方法eat
    abstract void eat();

    // 定义一个非抽象方法sleep
    void sleep(){
        System.out.println("Animal is sleep");
    }
}
// 子类实现
// Dog 类继承Animal类，并且实现eat方法
class Dog extends Animal{
    @Override
    void eat(){
        System.out.println("Dog is eat");
    }
}
// Cat类也继承Animal类，并且实现eat放法
class Cat extends Animal{
    @Override
    void eat(){
        System.out.println("Cat is eat");
    }
}
```

## JAVA封装

在面向对象程式设计方法中，封装（英语：Encapsulation）是指一种将抽象性函式接口的实现细节部分包装、隐藏起来的方法。

封装可以被认为是一个保护屏障，防止该类的代码和数据被外部类定义的代码随机访问。

要访问该类的代码和数据，必须通过严格的接口控制。

封装最主要的功能在于我们能修改自己的实现代码，而不用修改那些调用我们代码的程序片段。

适当的封装可以让程式码更容易理解与维护，也加强了程式码的安全性。

private

## JAVA接口

接口（英文：Interface），在JAVA编程语言中是一个抽象类型，是抽象方法的集合，接口通常以interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。

接口并不是类，编写接口的方式和类很相似，但是它们属于不同的概念。类描述对象的属性和方法。接口则包含类要实现的方法。

除非实现接口的类是抽象类，否则该类要定义接口中的所有方法。

接口无法被实例化，但是可以被实现。一个实现接口的类，必须实现接口内所描述的所有方法，否则就必须声明为抽象类。另外，在 Java 中，接口类型可用来声明一个变量，他们可以成为一个空指针，或是被绑定在一个以此接口实现的对象。

```java
[ 可见度 ] interface 接口名称 [ extends 其他接口名 ]{
// 声明变量
// 抽象方法
}
```

```java
class MammalInt implements Animal{
    public void eat(){
        System.out.println("Mammal eats");
    }
    public void travel(){
        System.out.println("Mammal travels");
    }
    public int noOfLegs(){
        return 0;
    }
    public static void main(String args[]){
        MammalInt m = new MammalInt();
        m.eat();
        m.travel();
    }
}
// 接口
interface Animal{
    public void eat();
    public void travel();
}

```

### **接口的继承**

一个接口能继承另一个接口，和类之间的继承方式比较相似。接口的继承使用extends关键字，子接口继承父接口的方法。

```java
public interface Sports{
    public void setHomeTeam(String name);
    public void setVisitingTeam(String name);
}
public interface Football extends Sports{
    public void homeTeamScored(int points);
    public void visitingTeamScored(int points);
    public void endOfQuarter(int quarter);
}
public interface Hockey extends Sports{
    public void homeGoalScored();
    public void visitingGoalScored();
    public void endOfPeriod(int period);
    public void overtimePeriod(int ot);
}
```

### **接口多继承**

在Java中，类的多继承是不合法，但接口允许多继承。

在接口的多继承中extends关键字只需要使用一次，在其后跟着继承接口。



```java
public interface Hockey extends Sports, Event
```

## JAVA枚举

Java 枚举是一个特殊的类，一般表示一组常量，比如一年的 4 个季节，一年的 12 个月份，一个星期的 7 天，方向有东南西北等。

Java 枚举类使用 enum 关键字来定义，各个常量使用逗号 **,** 来分割。



```java
public class Test{
    public static void main(String[] args){
        Color c1 = Color.RED;
        System.out.println(c1);
    }
}

enum Color{
    RED,GREEN,BLUE;
}
```

### 内部类中使用枚举：

```java
public class Test{
    enum Color{
        RED,GREEN,BLUE;
    }
    public static void main(String[] args){
        Color c1 = Color.RED;
        System.out.println(c1);
    }
}
```

### 迭代枚举元素：

可以使用 for 语句来迭代枚举元素：

```java
public class MyClass{
    public static void main(String[] args){
        for(Color myVar:Color.values()){
            System.out.println(myVar);
        }
    }
}

enum Color{
    RED,GREEN,BLUE;
}
```

### 在switch中使用枚举类

```java
public class MyClass{
    public static void main(String[] args){
        Color myVar = Color.BLUE;
        switch (myVar) {
            case RED:
                System.out.println("红色");
                break;
            case GREEN:
                System.out.println("绿色");
                break;
            case BLUE:
                System.out.println("蓝色");
                break;
        }
    }
}

enum Color{
    RED,GREEN,BLUE
}
```

### values(), ordinal() 和 valueOf() 方法

values() 返回枚举类中所有的值。

ordinal() 方法可以找到每个枚举常量的索引，就像数组索引一样。

valueOf() 方法返回指定字符串值的枚举常量。

```java
public class Test{
    public static void main(String[] args){
        //声明了一个Color类型的数组引用,调用values()
        Color[] arr = Color.values();

        for(Color col:arr){
            System.out.println(col+" at index"+col.ordinal());
        }
        System.out.println(Color.valueOf("RED"));
    }
}
enum Color{
    RED,GREEN,BLUE;
}
```

### 枚举普通成员

```java
public class Test{
    public static void main(String[] args){
        Color c1 = Color.RED;
        System.out.println(c1);
        c1.colorInfo();
    }
}
enum Color{
    RED,GREEN,BLUE;
    private Color(){
        System.out.println("Constructor called for: "+this.toString());
    }
    public void colorInfo(){
        System.out.println("Universal Color");
    }
}
```

### JAVA包（package）

例如：

```java
package net.java.util;
public class Something{
   ...
}
```

那么它的路径应该是 **net/java/util/Something.java** 这样保存的。 package(包) 的作用是把不同的 java 程序分类保存，更方便的被其他 java 程序调用。
