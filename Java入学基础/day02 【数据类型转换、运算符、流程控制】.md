# day02 【数据类型转换、运算符、流程控制】

## 今日内容

- 数据类型转换
- 运算符
- 数据输入
- 流程控制

## 教学目标

- [ ] 能够知道类型转换的格式和顺序

- [ ] 能够说出常见的运算符有哪几种

  算术运算符，赋值运算符，关系运算符，逻辑运算符，三元运算符

- [ ] 能够知道除法和取余的区别

- [ ] 能够完成字符和字符串的加法

- [ ] 能够知道&&和&的区别

- [ ] 能够使用三元运算符完成获取两个数中较大值

- [ ] 能够使用键盘录入数据并完成两个数据求和

  Scanner

- [ ] 能够使用if语句完成获取两个数中较大值

- [ ] 能够使用if语句完成根据分数输出对应级别
# 第一章 数据类型转换

在java中，不同的数据需要保存在不同的空间中，而开辟空间的时候，需要通过不同的类型关键字来定义当前这个空间是什么类型的空间。

开辟的空间如果和保存的数据类型不一致，那么就很容易导致程序出现错误。

这时我们就需要使用数据类型的转换技术，完成数据的保存工作。

数据类型的转换，可以分为两种：

1）隐式类型转换（自动类型转换）自动类型提升

2）强制类型转换

## 1.1 隐式类型转换

隐式类型转换：在程序中，空间保存的数据类型不一致的时候，java内部会自动的帮助我们转换。

要能够自动转换，必须遵守Java中的自动转换的规则：

可以把小空间中的数据给大空间中保存。

byte 空间中的数据， 可以自动的转成 short int long float double

但是不能把double 保存在 byte 、int 、 short 、long 等空间。

### 案例代码

```java
/*
	+:是一个运算符，做加法运算的。
	我们在做运算的时候，一般要求参与运算的数据类型必须一致。
	
	类型转换：
		隐式转换
		强制转换
		
	隐式转换	
		byte,short,char -- int -- long -- float -- double
*/
public class TypeCastDemo {
	public static void main(String[] args) {
		//定义两个int类型的变量
		int a = 3;
		int b = 4;
		int c = a + b;
		System.out.println(c);
		
		//定义一个byte类型,定义一个int类型
		byte bb = 2;
		int cc = 5;
		System.out.println(bb + cc);
		
		//我能不能不直接输出，用一个变量接收呢?
		//用变量接收，这个变量应该有类型
		//可能损失精度
		//byte dd = bb + cc;
		int dd = bb + cc;
		System.out.println(dd);
	}
}
```

说明：`byte` 类型内存占有1个字节，在和`int` 类型运算时会提升为`int`类型 ，自动补充3个字节，因此计算后的结果还是`int` 类型。 

同样道理，当一个`int` 类型变量和一个`double` 变量运算时，`int` 类型将会自动提升为`double` 类型进行运算。

```java
public static void main(String[] args) {
    int i = 1;
    double d = 2.5;
    //int类型和double类型运算，结果是double类型
    //int类型会提升为double类型
    double e = d+i;
    System.out.println(e);
}
```
### 转换规则

范围小的类型向范围大的类型提升，`byte、short、char` 运算时直接提升为`int` 。

```java
byte、short、char-->int-->long-->float-->double
```

## 1.2 强制转换	

将`1.5` 赋值到`int` 类型变量会发生什么？产生编译失败，肯定无法赋值。

```java
int i = 1.5; // 错误
```

`double` 类型内存8个字节，`int` 类型内存4个字节。`1.5` 是`double` 类型，取值范围大于`int` 。可以理解为`double` 是8升的水壶，`int` 是4升的水壶，不能把大水壶中的水直接放进小水壶去。

想要赋值成功，只有通过强制类型转换，将`double` 类型强制转换成`int` 类型才能赋值。

注意：

强制类型转换：将`取值范围大的类型`强制转换成`取值范围小的类型`。它一般都会有数据的丢失。不建议强制转换。

格式：

需要转成的数据类型 变量名 = ( 需要转成的数据类型 )( 被转的数据 );

 比较而言，自动转换是Java自动执行的，而强制转换需要我们自己手动执行。

```java
///////////////////////强制类型转换/////////////////////////////////
double d=3.14;
//int i=d;//报错
int i=(int)d;
System.out.println(i);
```

int i4 = (int )dd + 3.14; 报错。------》int i=(int)(dd+3.14);编译成功。

同样道理，当一个`short`类型与`1`相加，我们知道会类型提升，但是还想给结果赋值给short类型变量，就需要强制转换。

```java
public static void main(String[] args) {
     //short类型变量，内存中2个字节
     short s = 1;
     /*
       出现编译失败
       s和1做运算的时候，1是int类型，s会被提升为int类型
       s+1后的结果是int类型，将结果在赋值会short类型时发生错误
       short内存2个字节，int类型4个字节
       必须将int强制转成short才能完成赋值
     */
     s = s + 1；//编译失败
     s = (short)(s+1);//编译成功
}
```



## 1.3 ASCII编码表

```java
public static void main(String[] args) {
  //字符类型变量
  char c = 'a';
  int i = 1;
  //字符类型和int类型计算
  System.out.println(c+i);//输出结果是98
}
```

在计算机的内部都是二进制的0、1数据，如何让计算机可以直接识别人类文字的问题呢？就产生出了编码表的概念。

* **编码表**：就是将人类的文字和一个十进制数进行对应起来组成一张表格。

* **存储字符时**：需要查找ASCII码表,找到字符对应的数字,将数字转换为二进制数存放到计算机中

* **使用字符时**：将对应的二进制数转换为十进制 找到ASCII表中对应的字符 显示出来
  人们就规定：

  |  字符  |  数值  |
  | :--: | :--: |
  |  0   |  48  |
  |  9   |  57  |
  |  A   |  65  |
  |  Z   |  90  |
  |  a   |  97  |
  |  z   | 122  |

  将所有的英文字母，数字，符号都和一个数值对应，就产生了世界上第一张编码表ASCII（ American Standard Code for Information Interchange 美国标准信息交换码）。

  ![1554969754816](assets/1554969754816.png)


> 小贴士：
> 在char类型和int类型计算的过程中，char类型的字符先查询编码表，得到97，再和1求和，结果为98。char类型提升为了int类型。char类型内存2个字节，int类型内存4个字节。

## 1.4 常量和变量的运算

下面的程序有问题吗？

```java
public static void main(String[] args){
  byte b1=1;
  byte b2=2;
  byte b3=1 + 2;
  byte b4=b1 + b2;
  System.out.println(b3);
  System.out.println(b4);
}
```

分析：`b3 = 1 + 2` ，`1 `和 `2 ` 是常量，为固定不变的数据，在编译的时候（编译器javac），已经确定了`1+2` 的结果并没有超过byte类型的取值范围，可以赋值给变量`b3` ，因此`b3=1 + 2`是正确的。

反之，`b4 = b1 + b2`，`b1` 和 `b2` 是变量，变量的值是可能变化的，在编译的时候，编译器javac不确定b1+b2的结果是什么，因此会将结果以int类型进行处理，所以int类型不能赋值给byte类型，因此编译失败。



# 第二章 运算符

## 2.1 算数运算符

| 算数运算符包括： |                                        |
| ---------------- | -------------------------------------- |
| `+`              | 加法运算，字符串连接运算               |
| `-`              | 减法运算                               |
| `*`              | 乘法运算                               |
| `/`              | 除法运算                               |
| `%`              | 取模或者取余数运算，两个数字相除取余数 |
| `++` 、  `--`    | 自增自减运算                           |

### 二元运算符

1）在Java中进行算术运算的时候，运算符两侧的类型一致的时候， 运算的结果必须和运算的数据类型保持一致。

举例：int  d = 4321 / 1000* 1000;

​		4321 是int类型数据

​		1000 也是int类型数据

​		他们的商 也必须是int类型 

​		4321 /1000  结果是 4  不是4.321

 

2）当算术运算两侧的类型不一致的时候，结果向大的类型保持。

举例：double  d = 4321 / 1000.0* 1000;

#### 代码案例

```java
package com.itheima_01;
public class Demo {
	public static void main(String[] args) {
		// 定义两个变量
		int a = 3;
		int b = 4;

		System.out.println(a + b);
		System.out.println(a - b);
		System.out.println(a * b);
		System.out.println(a / b);

		System.out.println(4321 / 1000 * 1000);//4000
		System.out.println(4321 / 1000.0 * 1000);//4321.0
	}
}
```

### 一元运算符

| 符号 | 作用 | 说明        |
| ---- | ---- | ----------- |
| ++   | 自增 | 变量的值加1 |
| --   | 自减 | 变量的值减1 |

- `++`  **运算，变量自己增长1**。反之，`--` 运算，变量自己减少1，用法与`++` 一致。

  ++或者--既可以放在变量的后面，也可以放在变量的前面。

  表现形式：

  ++或者--在变量的右侧，举例：i++，j--；

  ++或者--在变量的左侧，举例：++i，--j；

  - 独立运算：

    - 变量在独立运算时，`前++`和`后++`没有区别 。
    - 变量`前++`   ：例如 `++i` 。
    - 变量`后++`   ：例如 `i++` 。

  - 和其他运算符混合运算：

    如果++或者--在变量的后面(右侧)，先拿变量参与操作，后变量做++或者--；

    如果++或者--在变量的前面(左侧)，先变量做++或者--，后拿变量参与操作；

    ​

    - 变量`前++` ：变量a自己加1，将加1后的结果赋值给b，也就是说a先计算。a和b的结果都是2。

    ```java
    public static void main(String[] args) {
        int a = 1;
        int b = ++a;
        System.out.println(a);//计算结果是2
        System.out.println(b);//计算结果是2
    }
    ```

    - 变量`后++` ：变量a先把自己的值1，赋值给变量b，此时变量b的值就是1，变量a自己再加1。a的结果是2，b的结果是1。

    ```java
    public static void main(String[] args) {
        int a = 1;
        int b = a++;
        System.out.println(a);//计算结果是2
        System.out.println(b);//计算结果是1
    }
    ```



- `+` 符号在字符串中的操作：
  - `+` 符号在遇到字符串的时候，表示**连接、拼接**的含义。
  - "a"+"b"的结果是“ab”，连接含义

```java
public static void main(String[] args){
        // 定义变量
		int a = 10;
		int b = 20;
        // 字符串参与加法操作
		System.out.println("hello" + a);//hello10
         // "hello"+10,然后再和b进行拼接
		System.out.println("hello" + a + b);//hello1020 
         //30hello
		System.out.println(a + b + "hello");
}
```



**补充：**

- 运算符和表达式
  - 运算符：对常量或者变量进行操作的符号
  - 表达式：用运算符把常量或者变量连接起来符合java语法的式子就可以称为表达式。

- 不同运算符连接的表达式体现的是不同类型的表达式。

- 举例说明：
  - +：是运算符，并且是算术运算符。
  - a + b：是表达式，由于+是算术运算符，所以这个表达式叫算术表达式。



## 2.2 赋值运算符

| 符号 | 作用       | 说明                  |
| ---- | ---------- | --------------------- |
| `=`  | 赋值       | a=10，将10赋值给变量a |
| `+=` | 加后赋值   | a+=b，将a+b的值给a    |
| `-=` | 减后赋值   | a-=b，将a-b的值给a    |
| `*=` | 乘后赋值   | a*=b，将a×b的值给a    |
| `/=` | 除后赋值   | a/=b，将a÷b的商给a    |
| `%=` | 取余后赋值 | a%=b，将a÷b的余数给a  |

- 赋值运算符，就是将符号右边的值，赋给左边的变量。
  - +=:a+=20;等于a = (a的数据类型)(a + 20);

```java
public static void main(String[] args){
        // 把10赋值给int类型的变量a
		int a = 10;

		// += 把左边和右边的数据进行运算，最后赋值给左边。左边的只能是变量
		a += 10;// 相当于a = a + 10
		System.out.println("a:" + a);
		System.out.println("----------------------");

		byte s = 10;
		// s += 20; // 相当于 s = s + 20;
		s = (byte) (s + 20);
		System.out.println("s:" + s);
}
```

分析： `s += 20` 逻辑上看作是`s = s + 20` 计算结果被提升为int类型，再向byte类型赋值时发生错误，因为不能将取值范围大的类型赋值到取值范围小的类型。但是，`s=s+20进行两次运算`，`+=` 是一个运算符，只运算一次，并带有强制转换的特点，也就是说`s += 20` 就是`s = (byte)(s + 20)`，因此程序没有问题编译通过，运行结果是30.



## 2.4 关系运算符

关系运算符有6种关系，分别为小于、小于等于、大于、等于、大于等于、不等于。

| 符号  | 说明                                                    |
| ----- | ------------------------------------------------------- |
| `==`  | a==b，判断a和b的值是否相等，成立为true，不成立为false   |
| `>`   | a>b，判断a是否大于b，成立为true，不成立为false          |
| `>=`  | a>=b，判断a是否大于或者等于b，成立为true，不成立为false |
| `<`   | a<b，判断a是否小于b，成立为true，不成立为false          |
| `<=`  | a<=b，判断a是否小于或者等于b，成立为true，不成立为false |
| `！=` | a!=b，判断a和b的值是否不相等，成立为true，不成立为false |

* 比较运算符，是两个数据之间进行比较的运算，运算结果都是布尔值`true`或者`false` 。

```java
public static void main(String[] args) {
    System.out.println(1==1);//true
    System.out.println(1<2);//true
    System.out.println(3>4);//false
    System.out.println(3<=4);//true
    System.out.println(3>=4);//false
    System.out.println(3!=4);//true
}
```
## 2.5 逻辑运算符

| 逻辑运算符包括： |                                                              |
| ---------------- | ------------------------------------------------------------ |
| `&&`  短路双与   | 1. 两边都是true，结果是true  2. 一边是false，结果是false    短路特点：符号左边是false，右边不再运算，效率比单与高**3.一假即假** |
| &   短路单与     | 1. 两边都是true，结果是true  2. 一边是false，结果是false    短路特点：符号左边是false，右边依然会运算，效率比双与低**3.一假即假** |
| \|\| 短路双或    | 1. 两边都是false，结果是false  2. 一边是true，结果是true   短路特点：符号左边是true，右边不再运算，效率比单或高**3.一真即真** |
| \|  短路单或     | 1. 两边都是false，结果是false  2. 一边是true，结果是true   短路特点：符号左边是true，右边依然会运算，效率比双或低**3.一真即真** |
| `！`   取反      | 1. ! true 结果是false  2. ! false结果是true                  |

- 逻辑运算符，是用来连接两个布尔类型结果的运算符，运算结果都是布尔值`true`或者`false`

```java
public static void main(String[] args)  {
    System.out.println(true && true);//true
    System.out.println(true && false);//false
    System.out.println(false && true);//false，右边不计算
  
    System.out.println(false || false);//falase
    System.out.println(false || true);//true
    System.out.println(true || false);//true，右边不计算
  
    System.out.println(!false);//true
}
```
## 2.6 三元运算符

* 三元运算符格式：

  ```
  数据类型 变量名 = 布尔类型表达式？真值结果1：结果2
  ```

- 三元运算符计算方式：
  - 布尔类型表达式结果是true，三元运算符整体结果为结果1，赋值给变量。
  - 布尔类型表达式结果是false，三元运算符整体结果为结果2，赋值给变量。
  - 三元运算符要求必须有一个结果，在结果1或者结果2中。开发中一般用来比较数值大小。

  ```java
  public static void main(String[] args) {
      int a = 200；
      int b = 100；
      int max = (a>b ? a : b);//max赋值为 a，b中较大的值
      System.out.println(max);//200
      int min = (a<b ? a : b);//min赋值为 a，b中较小的值
      System.out.println(min);//100
  }
  ```

  

- 三元运算符案例
  - 需求1：动物园里有两只老虎，已知两只老虎的体重分别为180kg、200kg，请用程序实现判断两只老虎的体重是否相同。

  ```java
  public class OperatorTest01 {
      public static void main(String[] args) {
          //1：定义两个变量用于保存老虎的体重，单位为kg，这里仅仅体现数值即可。
          int weight1 = 180;
          int weight2 = 200;
          //2：用三元运算符实现老虎体重的判断，体重相同，返回true，否则，返回false。
          boolean b = weight1 == weight2 ? true : false;
          //3：输出结果
          System.out.println("b:" + b);
      }
  }
  ```

  - 需求2：一座寺庙里住着三个和尚，已知他们的身高分别为150cm、210cm、165cm，请用程序实现获取这三个和尚的最高身高。

  ```java
  public class OperatorTest02 {
      public static void main(String[] args) {
          //1：定义三个变量用于保存和尚的身高，单位为cm，这里仅仅体现数值即可。
          int height1 = 150;
          int height2 = 210;
          int height3 = 165;
          //2：用三元运算符获取前两个和尚的较高身高值，并用临时身高变量保存起来。
          int tempHeight = height1 > height2 ? height1 : height2;
          //3：用三元运算符获取临时身高值和第三个和尚身高较高值，并用最大身高变量保存。
          int maxHeight = tempHeight > height3 ? tempHeight : height3;
          //4：输出结果
          System.out.println("maxHeight:" + maxHeight);
      }
  }
  ```


​	

# 第三章 数据输入

我们目前在写程序的时候，数据值都是固定的，但是实际开发中，数据值肯定是变化的，所以，把数据改进为键盘录入，提高程序的灵活性。

那么在java语言中，怎样实现呢？

我们可以通过 Scanner 类来获取用户的输入。

## 3.1 Scanner类的使用步骤

### 导包

使用import关键字导包，位置放到class定义的上面

格式：

```java
import 包名.类名;
```

举例：

```java
java.util.Scanner;
```

### 创建对象


格式：

```java
数据类型  变量名  =  new 数据类型(参数列表);
```

举例：

```java
Scanner sc = new Scanner(System.in);
```

### 调用方法接收数据
格式：

```java  
变量名.方法名();
```

举例：

```java
int i = sc.nextInt(); // 接收一个键盘录入的整数
```

### 示例

获取键盘录入的整数

```java
import java.util.Scanner;
public class ScannerDemo {
	public static void main(String[] args) {
		//创建对象
		Scanner sc = new Scanner(System.in);
		
		//接收数据
		int x = sc.nextInt();
		
		//输出数据
		System.out.println("x:" + x);
	}
}
```

## 3.2 Scanner类练习

在获取三个和尚中的最高身高案例中，身高数据如果由键盘录入，该怎样实现呢？

```java
import java.util.Scanner;
public class ScannerTest {
    public static void main(String[] args) {
        //身高未知，采用键盘录入实现。首先导包，然后创建对象。
        Scanner sc = new Scanner(System.in);
        //键盘录入三个身高分别赋值给三个变量。
        System.out.println("请输入第一个和尚的身高：");
        int height1 = sc.nextInt();
        System.out.println("请输入第二个和尚的身高：");
        int height2 = sc.nextInt();
        System.out.println("请输入第三个和尚的身高：");
        int height3 = sc.nextInt();
        //用三元运算符获取前两个和尚的较高身高值，并用临时身高变量保存起来。
        int tempHeight = height1 > height2 ? height1 : height2;
        //用三元运算符获取临时身高值和第三个和尚身高较高值，并用最大身高变量保存。
        int maxHeight = tempHeight > height3 ? tempHeight : height3;
        //输出结果。
        System.out.println("这三个和尚中身高最高的是：" + maxHeight +"cm");
    }
}
```



# 第四章 流程控制

## 4.1 概述

在一个程序执行的过程中，各条语句的执行顺序对程序的结果是有直接影响的。也就是说，程序的流程对运行结果有直接的影响。所以，我们必须清楚每条语句的执行流程。而且，很多时候我们要通过控制语句的执行顺序来实现我们要完成的功能。

## 4.2 分类

- 顺序结构
- 分支结构(if, switch)
- 循环结构(for, while, do…while)

## 4.3 顺序结构

程序的执行顺序：

书写的.java文件，称为Java的源代码（源程序）。

源代码需要使用JDK 中提供的 javac 命令进行编译。在dos窗口中输入的javac 源文件名.java 这时是在启动编译器，然后让编译器去检查当前的源代码有没有语法错误。没有语法错误，就会生成class文件。

然后我们在dos窗口中输入java class文件名 这时会启动JVM。启动JVM之后，JVM会在我们的内存中划分出空间，来运行当前的Java程序。JVM会先把硬盘上的class文件加载到内存划分好的空间中。JVM开始在当前这个class文件中找main方法运行。然后开始运行main方法。

在main方法中：开始执行main方法中的代码，从上往下逐行执行。在执行的过程中，JVM遇到不同的关键字，需要做不同的事情。程序是按照顺序结构在执行。程序中大多数的代码都是这样执行的。

在一个程序执行的过程中，各条语句的执行顺序对程序的结果是有直接影响的。所以，我们必须清楚每条语句的执行流程。而且，很多时候我们要通过控制语句的执行顺序来实现我们要完成的功能。

```java
public static void main(String[] args){
    //顺序执行，根据编写的顺序，从上到下运行
    System.out.println(1);
    System.out.println(2);
    System.out.println(3);
}
```

## 4.3 分支结构之if语句

程序在执行的过程中，需要加入一些条件，然后根据条件的真假，确定应该执行哪些代码，不应该执行哪些代码， 要完成这个需求，就必须使用Java中的判断结构。

### **if语句第一种格式：** if

```java
if(关系表达式)｛
  	语句体;
｝
//其它语句
```

- **执行流程**

  (1) 首先计算关系表达式的值

  (2) 如果关系表达式的值为true就执行语句体

  (3) 如果关系表达式的值为false就不执行语句体

  (4) 继续执行后面的其他语句

  ![](img/if.jpg)

- 需求：任意给出一个整数，请用程序实现判断该整数是奇数还是偶数，并在控制台输出该整数是奇数还是偶数。

- 分析:

  ①为了体现任意给出一个整数，采用键盘录入一个数据
  ②判断整数是偶数还是奇数要分两种情况进行判断，使用if结构
  ③判断是否偶数需要使用取余运算符实现该功能 number % 2 == 0
  ④根据判定情况，在控制台输出对应的内容

- 代码实现

```java
public static void main(String[] args){
    //为了体现任意给出一个整数，采用键盘录入一个数据。(导包，创建对象，接收数据)
    Scanner sc = new Scanner(System.in);
    System.out.println("请输入一个整数：");
    int number = sc.nextInt();
   
    //变量使用if判断
    if (number % 2 == 0){
      	System.out.println(number+"是偶数");
    }
   
    if(number % 2 == 1){
      	System.out.println(number+"是奇数");
    }
    System.out.println("结束");
｝
```

执行流程如下所示：

![](img/判断一个整数是偶数还是奇数.jpg)

### if语句第二种格式： if...else

```java
if(关系表达式) { 
  	语句体1;
} else {
  	语句体2;
}
//其它语句
```

- 执行流程

  (1) 首先计算关系表达式的值

  (2) 如果关系表达式的值为true就执行语句体1

  (3) 如果关系表达式的值为false就执行语句体2

  (4) 继续执行后面的其他语句

  ![](img/ifelse.jpg)

注意：如果if成立了，执行完if后面的语句之后，直接跳过else，不会执行else后面大括号中的内容，而是往下继续执行。

案例：比较两个数的大小。

```java
class IfElseDemo 
{
	public static void main(String[] args) 
	{
		//if else  举例
		
		int a = 3;
		int b = 6;
		//假设不考虑 a 和 b 相等的情况

		if( a > b )
		{
			System.out.println("a大于b");
		}
		else
		{
			System.out.println("b大于a");
		}

		System.out.println("Hello World!");
	}
}
```

注意：这里不考虑 a 和 b 相等的情况

执行过程如下图所示：

![](img/ifelse比较两个数大小.jpg)

注意：else 的语句执行时间是if判断的条件不成立时。else不需要书写条件。

在程序中只要有else，必然上方有if条件，但是有if条件，就不一定有else 了。



### if语句第三种格式： if...else if ...else

当在程序中有多个条件的时候，每个if只能列出其中的一种可能条件，这时在else中就会隐含其他的所有条件，对剩余的条件，还要进行更加具体的细化，这时可以在else 后面继续使用if，区分出其他的各种情况。

```java
if (关系表达式1) {
  	语句体1;
} else if (关系表达式2) {
  	语句体2;
}
...
}else if (关系表达式n) {
 	语句体n;
} else {
  	语句体n+1;
}
//其它语句
```

- **执行流程**

  (1) 首先计算关系表达式1的值,判断其结果是true还是false

  (2) 如果是true就执行语句体1

  (3) 如果是false就继续计算关系表达式2,判断其结果是true还是false

  (4) 如果是true就执行语句体2

  (5) 如果是false就继续计算关系表达式…,判断其结果是true还是false

  (6) …

  (7) 如果没有任何关系表达式为true，就执行语句体n+1


![](img/ifelseif.jpg)

- 键盘录入一个星期数(1,2,...7)，输出对应的星期一，星期二，...星期日

  输入  1      输出	星期一
  输入  2      输出	星期二
  输入  3      输出	星期三
  输入  4      输出	星期四
  输入  5      输出	星期五
  输入  6      输出	星期六
  输入  7      输出	星期日

  输入  其它数字   输出      数字有误

```java
public static void main(String[] args) {
    System.out.println("开始");
    // 需求：键盘录入一个星期数(1,2,...7)，输出对应的星期一，星期二，...星期日
    Scanner sc = new Scanner(System.in);
    System.out.println("请输入一个星期数(1­7)：");
    int week = sc.nextInt();
    if(week == 1) {
    	System.out.println("星期一");
    } else if(week == 2) {
    	System.out.println("星期二");
    } else if(week == 3) {
    	System.out.println("星期三");
    } else if(week == 4) {
    	System.out.println("星期四");
    } else if(week == 5) {
    	System.out.println("星期五");
    } else if(week == 6) {
    	System.out.println("星期六");
    } else {
    	System.out.println("星期日");
    }
    System.out.println("结束");
}
```

- if...else if ...else案例

  - 需求: 小明快要期末考试了，小明爸爸对他说，会根据他不同的考试成绩，送他不同的礼物，假如你可以控制小明的得分，请用程序实现小明到底该获得什么样的礼物，并在控制台输出。

  - 奖励规则:

    	95~100		山地自行车一辆
    90~94		游乐场玩一次
    80~89		变形金刚玩具一个
    80以下		胖揍一顿

  - 分析: 

    	(1) 小明的考试成绩未知，可以使用键盘录入的方式获取值

    (2) 由于奖励种类较多，属于多种判断，采用if...else...if格式实现

    (3) 为每种判断设置对应的条件

    (4) 为每种判断设置对应的奖励

  - 代码实现

  ```java
  public static void main(String[] args) {
      //小明的考试成绩未知，可以使用键盘录入的方式获取值
      Scanner sc = new Scanner(System.in);
      System.out.println("请输入一个分数：");
      int score = sc.nextInt();
      //由于奖励种类较多，属于多种判断，采用if...else...if格式实现
      //为每种判断设置对应的条件
      //为每种判断设置对应的奖励
      //数据测试：正确数据，边界数据，错误数据
      if(score>100 || score<0) {
      	System.out.println("你输入的分数有误");
      } else if(score>=95 && score<=100) {
      	System.out.println("山地自行车一辆");
      } else if(score>=90 && score<=94) {
      	System.out.println("游乐场玩一次");
      } else if(score>=80 && score<=89) {
      	System.out.println("变形金刚玩具一个");
      } else {
      	System.out.println("胖揍一顿");
      }
  }
  ```
