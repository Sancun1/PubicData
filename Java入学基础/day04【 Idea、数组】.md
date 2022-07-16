

# day04【 Idea、数组】

## 今日内容

- 集成开发工具IDEA
- 数组及内存图
- 数组的常见问题
- 数组的练习

## 教学目标

- [ ] 能够使用IDEA完成HelloWorld案例
- [ ] 能够知道IDEA的项目结构
- [ ] 能够使用IDEA完成工程的打开
- [ ] 能够知道数组的定义格式
- [ ] 能够使用三种方式完成数组元素的初始化
- [ ] 能够知道数组在内存中的初始化过程
- [ ] 能够完成数组的遍历操作
- [ ] 能够完成数组的获取最值操作

# 第一章 开发工具IntelliJ IDEA 

## 1.1 开发工具概述

DEA 全称IntelliJ IDEA，是[java语言](https://baike.baidu.com/item/java%E8%AF%AD%E8%A8%80)开发的集成环境，由Java语言编写。IntelliJ在业界被公认为最好的java开发工具之一，尤其在智能代码助手、代码自动提示、重构、[J2EE](https://baike.baidu.com/item/J2EE)支持、[Ant](https://baike.baidu.com/item/Ant/16001870)、[JUnit](https://baike.baidu.com/item/JUnit)、[CVS](https://baike.baidu.com/item/CVS)整合、代码审查、 创新的[GUI设计](https://baike.baidu.com/item/GUI%E8%AE%BE%E8%AE%A1)等方面的功能可以说是超常的。IDEA是JetBrains公司的产品，这家公司总部位于[捷克共和国](https://baike.baidu.com/item/%E6%8D%B7%E5%85%8B%E5%85%B1%E5%92%8C%E5%9B%BD)的首都[布拉格](https://baike.baidu.com/item/%E5%B8%83%E6%8B%89%E6%A0%BC/632)，开发人员以严谨著称的东欧[程序员](https://baike.baidu.com/item/%E7%A8%8B%E5%BA%8F%E5%91%98/62748)为主。

由于IDEA是由Java语言编写的。所以，需要有JRE运行环境并配置好环境变量。它可以极大地提升我们的开发效率。可以自动编译，检查错误。在公司中，使用的就是IDEA进行开发。IDEA是一个专门针对Java的集成开发工具(IDE)，由Java语言编写。所以，需要有JRE运行环境并配置好环境变量。它可以极大地提升我们的开发效率。可以自动编译，检查错误。在公司中，使用的就是IDEA进行开发。

## 1.2 IDEA软件安装

此软件集成了32位和64位，双击`ideaIU-2017.3.2.exe` 进入安装。

1. 欢迎界面

![](img/idea1.jpg)

2. 选择安装路径

![](img/idea2.jpg)

3. 配置安装选项

![](img/idea3.jpg)

4. 开始菜单

![](img/idea4.jpg)

5. 安装完毕

![](img/idea5.jpg)

IDEA开发工具安装完成

## 1.3 IDEA首次驱动

1. 选择不导入任何设置，点击`OK` 

![](img/idea6.jpg)

2. 选择 `Create New Project` 

![](img/idea7.jpg)

3. 点击`new` 按钮，配置安装的`JDK9` 版本

![](img/idea8.jpg)

选择`  JDK9` 目录，点击确定

![](img/idea9.jpg)

![](img/idea50.bmp)

4. 不使用模板

![](img/idea11.jpg)

5. 为工程起名字 `day04` ，并存储到`F:\ideawork\jichuban\heima49\day04` 目录下，如果F盘没有这个目录，会自动创建。

   > 首次新建项目时，默认的Project Location路径有问题，如 `c:\\xxx`，正确写法为`c:\xxx`。更改后不会再出现此类问题。

![](img/idea51.bmp)

6. 打开一个每日一帖对话框，勾掉每次启动显示，点击`close` 

![](img/idea13.jpg)

7. IDEA的工作界面，我们的项目day04已经创建好了，然后就会跳转到如下界面：

   ![](img/idea52.bmp)

   **注意：**

   如果再新建项目，点击`File->new->Project` 

   

## 1.4 创建包和类

1. 展开创建的工程，在源代码目录`src` 上，鼠标右键，选择`new->package` ，键入包名`com.itheima.demo` ，点击确定。

![](img/idea53.bmp)

右键点击`com.itheima.demo` ，选择 `Show in Explorer` ，会发现创建包的目录结构。

![](img/idea54.bmp)

​	可见`com.itheima.demo` ，表示创建了多级的文件夹。

> 小贴士：所谓包，就是文件夹，用来对类文件进行管理。



2. 在创建好的包上，鼠标右键，选择 `new->class`  创建类，键入类名。

![](img/idea55.bmp)



3. 在代码编辑区，键入主方法，并输出`HelloWorld` 。

![](img/idea56.bmp)

注意：如果写完输出语句之后，在字符串之前会多点东西，如：x: 。这里不用理会，是idea工具编译的时候做一个显示，和我们书写的代码没有关系，对代码没有任何影响。显示这里有个变量，变量值是多少啊等。

4.运行程序，在代码编辑区鼠标右键，选择`Run HelloWorld` 即可，或在菜单中选择`Run->Run HelloWorld ` 。

![](img/idea20.jpg)

## 1.5 字体和主题设置

### 字体设置

IDEA工具的默认字体非常小，代码编辑器和控制台的输出字体都需要进行调整。

* 点击菜单栏上的`File->Settings->Editor->Font`修改字体。

![](img/idea21.jpg)

![](img/idea22.jpg)

### 主题设置

idea背景默认是白色，如果感觉刺眼，我们可以修改背景颜色。

具体做法：File->Settings->Appearance & Behavior->Appearance->右边选择Theme

然后在这里选择适合自己的风格。

![](img/主题设置.jpg)

## 1.6 IDEA的项目目录

- 我们创建的项目，在d:\ideawork目录的demo下
  - `.idea` 目录和我们开发无关，是IDEA工具自己使用的
  - out目录是存储编译后的.class文件
  - `src` 目录是存储我们编写的.java源文件

  ![](img/创建好的项目目录.jpg)

## 1.7 IDEA常用快捷键

| 快捷键              | 功能                  |
| ---------------- | ------------------- |
| `Alt+Enter`      | 导入包，自动修正代码          |
| `Ctrl+Y`         | 删除光标所在行             |
| `Ctrl+D`         | 复制光标所在行的内容，插入光标位置下面 |
| `Ctrl+Alt+L`     | 格式化代码               |
| `Ctrl+/`         | 单行注释                |
| `Ctrl+Shift+/`   | 选中代码注释，多行注释，再按取消注释  |
| `Alt+Shift+上下箭头` | 移动当前代码行             |

## 1.8 IDEA修改快捷键

在IDEA工具中，`Ctrl+空格`的快捷键，可以帮助我们补全代码，但是这个快捷键和Windows中的输入法切换快捷键冲突，需要修改IDEA中的快捷键。

`File->Settings->keymap->Main menu->code->Completion->Basic`

![](img/idea25.jpg)

双击`Basic->remove->Ctrl+空格`

![](img/idea26.jpg)

再次双击`Basic->Add Keyboard->键入 Alt+/->点击OK`

![](img/idea28.jpg)

## 1.9 IDEA导入和关闭项目

关闭IDEA中已经存在的项目，`File->Close Project`

![](img/idea29.jpg)

`File->Close Project `这时IDEA回到了刚启动界面，点击项目上的`X`，IDEA中就没有这个项目了

![](img/idea31.jpg)

- **导入或者打开一个项目**

在IDEA的启动界面上，点击`OPEN` ，选择项目目录即可

![](img/导入项目.jpg)

![](img/idea32.jpg)

> 小贴士：
>
> 课后若想通过IDEA同时开启多个项目，在idea里面选择File--Open

![](img/idea打开多个项目.jpg)

在弹出框中选择要打开的项目：

![](img/idea打开多个项目1.jpg)

点击OK以后会弹出如下框：

![](img/idea33.jpg)

选择New Window 即可.

## 1.10 IDEA的文件编码设置

对于IDEA的使用，我们要求编码都是使用统一的编码UTF-8.接下来我们按照如下方式修改即可。

File----->Settings...

![](img/IDEA编码设置1.jpg)

Editor--->File Encodings

![](img/idea编码设置2.jpg)

# 第二章 数组定义和访问

## 2.1 数组概念

在Java中有常量数据，而一般情况下，常量数据都需要保存在变量空间中。

假设有100 这个数据需要在程序中先存储起来：

int a = 100；

假设有100，200 这个数据需要在程序中先存储起来：

int a = 100;

int b = 200;

问题继续升级，有大量的整数需要保存，怎么解决？

第一种解决方案：有多少个数据，就开辟多少个空间，把每个值保存到空间中。

这种解决方案，最后肯定可以把所有的数据保存起来，但是程序书写十分麻烦。常量数据最后肯定需要保存在变量空间中，在前面学习的变量，每个变量空间中在特定的时候，只能保存一个值。无法一次性保存多个数据。

 

Java中给我们提供另外一种方案：

一次性可以开辟出一组空间，然后这些空间中可以保存多个数据。而我们把这一组空间统称为数组。

那么数组到底是什么呢?有什么特点呢?

数组：数组表示的一串**连续**的存储空间。每个空间中都可以保存一个数据。当我们需要操作的时候，不要去面对单个空间，而直接面对这个整体的连续的存储区域。

注意：

​	1）数组既可以存储基本数据类型，也可以存储引用数据类型。

​	2）数组就是存储数据长度固定的容器，保证多个数据的数据类型要一致。



## 2.2 数组的定义

### 方式一

- **格式：**

```java
 数组存储的数据类型[] 数组名字 = new 数组存储的数据类型[长度];
```

- 数组定义格式详解：
  - 数组存储的数据类型： 创建的数组容器可以存储什么数据类型。
  - [] : 表示数组。
  - 数组名字：为定义的数组起个变量名，满足标识符规范，可以使用名字操作数组。
  - new：关键字，创建数组使用的关键字。
  - 数组存储的数据类型： 创建的数组容器可以存储什么数据类型。
  - [长度]：数组的长度，表示数组容器中可以存储多少个元素。
  - **注意：数组有定长特性，长度一旦指定，不可更改。**
    - 和水杯道理相同，买了一个2升的水杯，总容量就是2升，不能多也不能少。
- 举例：

定义可以存储4个整数的数组容器，代码如下：

```java
int[] arr = new int[4];
```

在内存中一次开辟4个连续的空间，每个空间都是int类型，并且这些空间中保存的数据也必须是int类型。

![](img/数组引入内存图解1.bmp)

## 2.3 数组的访问

![数组的访问](assets/数组的访问.png)

- **索引：** 每一个存储到数组的元素，都会自动的拥有一个编号，从0开始，这个自动编号称为**数组索引(index)**，可以通过数组的索引访问到数组中的元素。
- **格式：**

```java
数组名[索引]
```

- **数组的长度属性：** 每个数组都具有长度，而且是固定的，Java中赋予了数组的一个属性，可以获取到数组的长度，语句为：`数组名.length` ，属性length的执行结果是数组的长度，int类型结果。由次可以推断出，数组的最大索引值为`数组名.length-1`。

```java
public static void main(String[] args) {
  	int[] arr = new int[]{1,2,3,4,5};
  	//打印数组的属性，输出结果是5
  	System.out.println(arr.length);
}

```

- **索引访问数组中的元素：**
  - 数组名[索引]=数值，为数组中的元素赋值
  - 变量=数组名[索引]，获取出数组中的元素

```java
public static void main(String[] args) {
    //定义存储int类型数组，赋值元素1，2，3，4，5
    int[] arr = {1,2,3,4,5};
    //为0索引元素赋值为6
    arr[0] = 6;
    //获取数组0索引上的元素
    int i = arr[0];
    System.out.println(i);
    //直接输出数组0索引元素
    System.out.println(arr[0]);
}

```

# 第三章 数组原理内存图

## 3.1 内存概述

内存是计算机中的重要原件，临时存储区域，作用是运行程序。我们编写的程序是存放在硬盘中的，在硬盘中的程序是不会运行的，必须放进内存中才能运行，运行完毕后会清空内存。

Java虚拟机要运行程序，必须要对内存进行空间的分配和管理。

![JVM内存模型](assets/JVM内存模型.jpg)

## 3.2 Java虚拟机的内存划分

为了提高运算效率，就对空间进行了不同区域的划分，因为每一片区域都有特定的处理数据方式和内存管理方式。

- JVM的内存划分：

  | 区域名称   | 作用                                                       |
  | ---------- | ---------------------------------------------------------- |
  | 寄存器     | 给CPU使用，和我们开发无关。                                |
  | 本地方法栈 | JVM在使用操作系统功能的时候使用，和我们开发无关。          |
  | 方法区     | 存储可以运行的class文件。                                  |
  | 堆内存     | 存储对象或者数组，new来创建的，都存储在堆内存。            |
  | 方法栈     | 方法运行时使用的内存，比如main方法运行，进入方法栈中执行。 |

补充：

**栈内存**：栈内存主要是用来运行函数的，在函数中定义的所有变量，都会在这个内存开辟空间。

在栈内存中定义的变量，不初始化，是不能直接使用的。

注意：所有的函数(方法)都必须在栈内存中运行。

而jvm只会运行处于栈内存顶部的函数。

函数被加载到栈内存的动作，称为函数的压栈（入栈）。

函数执行完之后就会从栈中消失（函数的弹栈，或者叫做出栈）

 

**堆内存**：在程序中使用new 关键字创建出来的所有东西，都会保存在堆内存中。

堆内存中开辟的空间，不赋值，都会有默认的初始化数据。

整数：默认是0

小数 默认0.0.

boolean 默认是false

char 默认是 ‘\u0000’

引用数据类型默认值是 null

**方法区**：JVM在加载class文件的时候，所有的class文件就要加载在这个内存中。(先了解，后面会详细讲解)

## 3.3 数组在内存中的存储

### 一个数组内存图

```java
public static void main(String[] args) {
  	int[] arr = new int[3];
  	System.out.println(arr);//[I@5f150435
}

```

以上方法执行，输出的结果是[I@5f150435，这个是什么呢？是数组在内存中的地址。new出来的内容，都是在堆内存中存储的，而方法中的变量arr保存的是数组的地址。

**输出arr[0]，就会输出arr保存的内存地址中数组中0索引上的元素**

![1554194176373](assets/1554194176373.png)

### 两个数组内存图

```java
public static void main(String[] args) {
    int[] arr = new int[3];
    int[] arr2 = new int[2];
    System.out.println(arr);
    System.out.println(arr2);
}

```

![1554194227515](assets/1554194227515.png) 

### 两个变量指向一个数组

```java
public static void main(String[] args) {
    // 定义数组，存储3个元素
    int[] arr = new int[3];
    //数组索引进行赋值
    arr[0] = 5;
    arr[1] = 6;
    arr[2] = 7;
    //输出3个索引上的元素值
    System.out.println(arr[0]);
    System.out.println(arr[1]);
    System.out.println(arr[2]);
    //定义数组变量arr2，将arr的地址赋值给arr2
    int[] arr2 = arr;
    arr2[1] = 9;
    System.out.println(arr[1]);
}

```

 ![1554194263213](assets/1554194263213.png)

# 第四章 数组操作的常见问题

## 4.1 数组越界异常

观察一下代码，运行后会出现什么结果。

```java
public static void main(String[] args) {
    int[] arr = {1,2,3};
    System.out.println(arr[3]);
}

```

创建数组，赋值3个元素，数组的索引就是0，1，2，没有3索引，因此我们不能访问数组中不存在的索引，程序运行后，将会抛出 `ArrayIndexOutOfBoundsException`  数组越界异常。在开发中，数组的越界异常是**不能出现**的，一旦出现了，就必须要修改我们编写的代码。

![](img/ArrayIndexOutOfBoundsException.jpg)

## 4.2 数组空指针异常

观察一下代码，运行后会出现什么结果。

```java
public static void main(String[] args) {
    int[] arr = {1,2,3};
    arr = null;
    System.out.println(arr[0]);
｝
    
```

`arr = null`这行代码，意味着变量arr将不会在保存数组的内存地址，也就不允许再操作数组了，因此运行的时候会抛出`NullPointerException` 空指针异常。在开发中，数组的越界异常是**不能出现**的，一旦出现了，就必须要修改我们编写的代码。

![](img/NullPointerException.jpg)

**空指针异常在内存图中的表现**

![1554194318490](assets/1554194318490.png)

# 第五章 数组练习

## 5.1 数组遍历【重点】

- **数组遍历：** 就是将数组中的每个元素分别获取出来，就是遍历。遍历也是数组操作中的基石。

```java
public static void main(String[] args) {
    int[] arr = { 11, 22, 33, 44, 55 };
    System.out.println(arr[0]);
    System.out.println(arr[1]);
    System.out.println(arr[2]);
    System.out.println(arr[3]);
    System.out.println(arr[4]);
}

```

以上代码是可以将数组中每个元素全部遍历出来，但是如果数组元素非常多，这种写法肯定不行，因此我们需要改造成循环的写法。数组的索引是`0`到`lenght-1` ，可以作为循环的条件出现。 

```java
public static void main(String[] args) {
    int[] arr = { 11, 22, 33, 44, 55 };
    for (int i = 0; i < arr.length; i++) {
      System.out.println(arr[i]);
    }
}

```

数组遍历升级：要求将数组中的每个数据之间用逗号隔开。例如：1,2,3,4,5

```java
/*
	遍历数组
*/
class ArrayTest 
{
	public static void main(String[] args) 
	{
		//定义数组
		int[] arr={ 1, 2, 3, 4, 5 };
		//将数组arr中的数据打印到屏幕上
		//由于数组的下标有序的增加，使用循环提供数组的下标
		/*for (int i=0;i<arr.length ;i++)
		{
			System.out.println(arr[i]);
			
		}*/
		for (int i=0;i<arr.length ;i++ )
		{
			//这里需要加一个判断语句，如果数据是最后一位，就不需要打印逗号
			if (i==arr.length-1)
			{
				//说明数组的下标是整个数组中最后一个下标
				System.out.println(arr[i]);
			}else{
				//说明数组的下标不是最后一个下标
				System.out.print(arr[i]+",");
			}
		}
		
	}
}
```



## 5.2 数组获取最大值元素

- **最大值获取：**从数组的所有元素中找出最大值。
- **实现思路：**
  - 定义变量，保存数组0索引上的元素
  - 遍历数组，获取出数组中的每个元素
  - 将遍历到的元素和保存数组0索引上值的变量进行比较
  - 如果数组元素的值大于了变量的值，变量记录住新的值
  - 数组循环遍历结束，变量保存的就是数组中的最大值

![1554194362209](assets/1554194362209.png)

```java
public static void main(String[] args) {
    int[] arr = { 5, 15, 2000, 10000, 100, 4000 };
    //定义变量，保存数组中0索引的元素
    int max = arr[0];
    //遍历数组，取出每个元素
    for (int i = 0; i < arr.length; i++) {
      //遍历到的元素和变量max比较
      //如果数组元素大于max
      if (arr[i] > max) {
        //max记录住大值
        max = arr[i];
      }
    }
    System.out.println("数组最大值是： " + max);
}

```

