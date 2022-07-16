# day08【API、String类、StringBuilder类】

## 今日内容

*  String类
*  String类


*  StringBuilder类


## 教学目标

- [ ] 能够知道帮助文档的使用步骤
- [ ] 能够知道字符串对象通过构造方法创建和直接赋值的区别
- [ ] 能够完成用户登录案例
- [ ] 能够完成统计字符串中大写,小写,数字字符的个数
- [ ] 能够知道String和StringBuilder的区别
- [ ] 能够完成String和StringBuilder的相互转换
- [ ] 能够使用StringBuilder完成字符串的拼接
- [ ] 能够使用StringBuilder完成字符串的反转

# 第一章 API

## 1.1 概述

在学习面向对象编程思想，遇到需求时，先去找有没有解决问题的功能(函数)存在。这些解决问题的功能(函数)通常是封装在类中（功能类），使用这些功能类基本可以解决开发中大部分的问题。

问题：这些解决问题的功能类都在哪里？

      在java设计时，已经提供了很多解决问题的封装类。这些解决问题的封装类，我们统称为：API在开发中，只要去相应的包(文件夹)中去找对应的封装类就可以解决问题。

API：application programming interface。应用程序接口。我们这里通常把api简称为帮助文档。

想要使用java提供的解决各种问题的API，就需要先学会如何查阅API文档。

## 1.2 API使用步骤

1. 打开帮助文档。
2. 点击显示，找到索引，看到输入框。
3. 你要找谁？在输入框里输入，然后回车。
4. 看包。java.lang下的类不需要导包，其他需要。
5. 看类的解释和说明。
6. 学习构造方法。
7. 使用成员方法。

## 1.3 API使用练习

了解了API的使用方式，我们通过Scanner类和Random类，熟悉一下查询API，并使用类的步骤。

- 练习1：获取键盘录入的字符串

  **查看类**

  - `java.util.Scanner` ：该类需要import导入后使用。 

  **查看构造方法**

  - `public Scanner(InputStream source)` : 构造一个新的 `Scanner`，它生成的值是从指定的输入流扫描的。

  **查看成员方法**

  - ` public int nextInt() `：将输入信息的下一个标记扫描为一个 `int` 值。

- 练习1：使用Scanner类，完成接收键盘录入数据的操作，代码如下：


```java
//1. 导包
import java.util.Scanner;
public class Demo01_Scanner {
  	public static void main(String[] args) {
    	//2. 创建键盘录入数据的对象
    	Scanner sc = new Scanner(System.in);

    	//3. 接收数据
    	System.out.println("请录入一个整数：");
    	int num = sc.nextInt();

    	//4. 输出数据
    	System.out.println("您输入的整数:"+num);
  	}
}
```



- 练习2：获取一个1-33之间（包含1和33）的随机数字

  **查看类**

  - `java.util.Random` ：该类需要 import导入使后使用。 

  **查看构造方法**

  - `public Random()`：创建一个新的随机数生成器。

  **查看成员方法**

  - ` public int nextInt(int n) `：返回一个伪随机数，范围在 `0` （包括）和`指定值 n` （不包括）之间的 `int` 值。

```java
//1. 导包
import java.util.Random;
public class Demo01_Random {
  	public static void main(String[] args) {
        //2. 创建键盘录入数据的对象
        Random r = new Random();
        //3. 随机生成一个数据
        int number = r.nextInt(33)+1;
        //4. 输出数据
        System.out.println("number:"+ number);        
    }
}
```

> 备注：创建一个`Random`对象，每次调用`nextInt()`方法，都会生成一个随机数。

# 第二章 String类

## 2.1 String类概述

### 概述

在前面学习常量的时候介绍过Java中的所有常量：

整数、小数、字符、字符串、null、真假值true false 

字符串常量，它在Java中不属于基本数据类型， 而是引用类型，也称为类类型。Java中使用String这个类描述字符串这种常量数据。

API中对java.lang.String类的描述：

`java.lang.String` 类代表字符串。Java程序中所有的字符串文字（例如`"abc"` ）都可以被看作是实现此类的实例。

String描述的字符串，所有在Java程序中使用双引号引用起来的数据都是一个对象。

### 特点

1、**注意：字符串常量，它属于对象，但是它**不是像之前的对象通过new的方式在堆中开辟空间，而是存储在**字符串常量池中**。

说明：jdk1.7之前**字符串常量池**是位于**方法区**中的,而jdk1.7之后是位于堆中的。位于堆中和之前new空间不冲突，常量池是一个单独的空间。在本课程中我们在讲解的时候，依然将**字符串常量池**放到方法区中。位于哪个区域原理都差不多。对于常量池我们只是知道即可。

字符串常量池中保存的就是所有的字符串数据。只要我们书写了双引号，不管双引号中间是什么数据，这些数据都会立刻在字符串常量池中保存。并且一直存在，不会被改变。

2、字符串不变：字符串的值在创建后不能被更改。String类中描述的是所有字符串常量，一旦书写完成，它就是一个固定值，这个数据不能改变。

```java
String s3="def";
s3="efg";
System.out.println(s3);
// 内存中有"def"，"efg"两个对象，s3从指向"def"，改变指向，指向了"efg"。
```

3、因为String对象是不可变的，所以它们可以被共享。

```java
       //定义字符串对象
		String s1="abc";
		//int i=3;在栈中开辟空间名称叫做i，存值为3
		String s2="abc";
		//打印的不是内存地址名，是abc常量的值
		//System.out.println(s1);
		System.out.println(s1==s2);//这里比较的是内存地址名是否相等
```

上述特点的内存如下所示：

![](img/String类的概述内存图解.jpg)

String类中的api告诉我们字符串是常量不能被改变，这里的不能被改变意思是说在常量池中的字符串对象中的常量数据不能被改变，而指向这些字符串对象的引用变量空间中的内存地址值是可以改变的，这样可以让同一个String类型的引用变量空间指向方法区中字符串常量池中不同的字符串常量对象空间所保存的常量数据。

## 2.2 使用步骤

- 查看类

  - `java.lang.String` ：此类不需要导包。 

- 查看构造方法

  后期查阅api，看到一个类提供的构造函数，那么我们就可以知道这个类肯定给我们提供的不同构造函数都可以创建出这个类的一个对象。

  **注意：使用双引号本身就可以得到一个字符串对象。**

  **String类提供了大量的构造函数，目的是可以帮助我们将其他的数据变成字符串对象。**

  **只要使用String类的构造函数创建的对象，那么这个对象就会在堆中出现。**

  **而在创建出的字符串对象中的字符数据保存在常量池中。**

  - `public String() ` ：初始化新创建的 String对象，以使其表示空字符序列。相当于 String s="";
  - `public String(char[] value) ` ：通过该构造方法可以将参数的字符数组转换为String类的对象。
  - `public String(byte[] bytes) ` ：通过该构造方法可以将参数的字节数组转换为String类的对象。
  - 构造举例，代码如下：

```java
// 无参构造
String str = new String（）；

// 通过字符数组构造
char chars[] = {'a', 'b', 'c'};     
String str2 = new String(chars);

// 通过字节数组构造
byte bytes[] = { 97, 98, 99 };     
String str3 = new String(bytes);
```

## 2.3 常用方法

学习任何一个类的时候，先要阅读这个类的帮助文档的说明：理解当前这个类或接口到底是干什么的。

然后查看它的构造函数，看能不能创建对象。

然后去查看API，看下这个类下面有哪些方法，每个方法都有什么作用，当自己在开发中遇到某种需求后，看看这个类中的有没有提供解决问题的方法，如果有直接创建对象，使用这个方法来解决问题即可。

### 2.3.1 判断功能的方法

- `public boolean equals (Object anObject) ` ：将此字符串与指定对象进行比较。 严格比较

  说明：

  Object:是类层次结构中的根类，所有的类都直接或者间接的继承自该类。

  如果一个方法的形式参数是Object，那么这里我们就可以传递它的任意的子类对象。

- ` public boolean equalsIgnoreCase (String anotherString) ` ：将此字符串与指定对象进行比较，忽略大小写。 模糊比较

  方法演示，代码如下：

  ```java
  public class String_Demo01 {
      public static void main(String[] args) {
          // 创建字符串对象
          String s1 = "hello";
          String s2 = "hello";
          String s3 = "HELLO";
  
          // boolean equals(Object obj):比较字符串的内容是否相同
          System.out.println(s1.equals(s2)); // true
          System.out.println(s1.equals(s3)); // false
          System.out.println("-----------");
  
          //boolean equalsIgnoreCase(String str):比较字符串的内容是否相同,忽略大小写
          System.out.println(s1.equalsIgnoreCase(s2)); // true
          System.out.println(s1.equalsIgnoreCase(s3)); // true
          System.out.println("-----------");
      }
  }
  ```

> 注意：
>
> 如果想比较两个字符串相等，我们不应该使用==(恒等符号)，因为==是用来比较具体常量数值的。
>
> 而由于字符串是对象，所以我们应该使用String类中的equals函数对两个字符串进行比较，因为equals函数是用来比较两个对象是否相等。

### 2.3.2 获取功能的方法

- `public int length () ` ：返回此字符串的长度。
- `public String concat (String str)` ：将指定的字符串连接到该字符串的末尾。
- ` public char charAt (int index) ` ：返回指定索引处的 char值。
- `public int indexOf (String str) ` ：返回指定子字符串第一次出现在该字符串内的索引。
- ` public String substring (int beginIndex) ` ：返回一个子字符串，从beginIndex开始截取字符串到字符串结尾。
- ` public String substring (int beginIndex, int endIndex) ` ：返回一个子字符串，从beginIndex到endIndex截取字符串。含beginIndex，不含endIndex。

方法演示，代码如下：

```java
public class String_Demo02 {
    public static void main(String[] args) {
        //创建字符串对象
        String s = "helloworld";

        // int length():获取字符串的长度，其实也就是字符个数
        System.out.println(s.length());
        System.out.println("--------");

        // String concat (String str):将将指定的字符串连接到该字符串的末尾.
        String s = "helloworld";
        String s2 = s.concat("**hello itheima");
        System.out.println(s2);// helloworld**hello itheima

        // char charAt(int index):获取指定索引处的字符
        System.out.println(s.charAt(0));
        System.out.println(s.charAt(1));
        System.out.println("--------");

        // int indexOf(String str):获取str在字符串对象中第一次出现的索引,没有返回-1
        System.out.println(s.indexOf("l"));
        System.out.println(s.indexOf("owo"));
        System.out.println(s.indexOf("ak"));
        System.out.println("--------");

        // String substring(int start):从start开始截取字符串到字符串结尾
        System.out.println(s.substring(0));
        System.out.println(s.substring(5));
        System.out.println("--------");

        // String substring(int start,int end):从start到end截取字符串。含start，不含end。
        System.out.println(s.substring(0, s.length()));
        System.out.println(s.substring(3,8));
    }
}
```

### 2.3.3 转换功能的方法

- `public char[] toCharArray () ` ：将此字符串转换为新的字符数组。 

- ` public byte[] getBytes () ` ：使用平台的默认字符集将该 String编码转换为新的字节数组。

- `public String replace (CharSequence target, CharSequence replacement) ` ：将与target匹配的字符串使用replacement字符串替换。

  说明：CharSequence 是一个接口，也是一种引用类型。作为参数类型，可以把String对象传递到方法中。可以理解为CharSequence 是String类的父接口即老子，String类即儿子类的对象可以在这里接收。

方法演示，代码如下：

```java
public class String_Demo03 {
    public static void main(String[] args) {
        //创建字符串对象
        String s = "abcde";

        // char[] toCharArray():把字符串转换为字符数组
        char[] chs = s.toCharArray();
        for(int x = 0; x < chs.length; x++) {
          	System.out.println(chs[x]);
        }
        System.out.println("-----------");

        // byte[] getBytes ():把字符串转换为字节数组
        byte[] bytes = s.getBytes();
        for(int x = 0; x < bytes.length; x++) {
          	System.out.println(bytes[x]);
        }
        System.out.println("-----------");

        // 替换字母it为大写IT
        String str = "itcast itheima";
        String replace = str.replace("it", "IT");
        System.out.println(replace); // ITcast ITheima
        System.out.println("-----------");
    }
}
```



### 2.3.4 分割功能的方法

- `public String[] split(String regex)` ：将此字符串按照给定的regex（规则）拆分为字符串数组。

方法演示，代码如下：

将字符串"aa,bb,cc" 以逗号进行切割。

  ```java
public class String_Demo03 {
    public static void main(String[] args) {
        //创建字符串对象
        String s = "aa,bb,cc";
        String[] strArray = s.split(","); // ["aa","bb","cc"]
        for(int x = 0; x < strArray.length; x++) {
          	System.out.println(strArray[x]); // aa bb cc
        }
    }
}
  ```

## 2.4 String类的练习

### 2.4.1 模拟用户登录

需求：已知用户名和密码，请用程序实现模拟用户登录。总共给三次机会，登录之后，给出相应的提示

```java
/*
    思路：
        1:已知用户名和密码，定义两个字符串表示即可
        2:键盘录入要登录的用户名和密码，用 Scanner 实现
        3:拿键盘录入的用户名、密码和已知的用户名、密码进行比较，给出相应的提示。字符串的内容比较，用equals() 方法实现
        4:用循环实现多次机会，这里的次数明确，采用for循环实现，并在登录成功的时候，使用break结束循环
 */
public class StringTest01 {
    public static void main(String[] args) {
        //已知用户名和密码，定义两个字符串表示即可
        String username = "itheima";
        String password = "czbk";

        //用循环实现多次机会，这里的次数明确，采用for循环实现，并在登录成功的时候，使用break结束循环
        for(int i=0; i<3; i++) {

            //键盘录入要登录的用户名和密码，用 Scanner 实现
            Scanner sc = new Scanner(System.in);

            System.out.println("请输入用户名：");
            String name = sc.nextLine();

            System.out.println("请输入密码：");
            String pwd = sc.nextLine();

            //拿键盘录入的用户名、密码和已知的用户名、密码进行比较，给出相应的提示。字符串的内容比较，用equals() 方法实现
            if (name.equals(username) && pwd.equals(password)) {
                System.out.println("登录成功");
                break;
            } else {
                if(2-i == 0) {
                    System.out.println("你的账户被锁定，请与管理员联系");
                } else {
                    //2,1,0
                    //i,0,1,2
                    System.out.println("登录失败，你还有" + (2 - i) + "次机会");
                }
            }
        }
    }
}
```

### 2.4.2 遍历字符串

需求：键盘录入一个字符串，使用程序实现在控制台遍历该字符串

```java
/*
    思路：
        1:键盘录入一个字符串，用 Scanner 实现
        2:遍历字符串，首先要能够获取到字符串中的每一个字符
            public char charAt(int index)：返回指定索引处的char值，字符串的索引也是从0开始的
        3:遍历字符串，其次要能够获取到字符串的长度
            public int length()：返回此字符串的长度
            数组的长度：数组名.length
            字符串的长度：字符串对象.length()
        4:遍历字符串的通用格式
 */
public class StringTest02 {
    public static void main(String[] args) {
        //键盘录入一个字符串，用 Scanner 实现
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入一个字符串：");
        String line = sc.nextLine();

        for(int i=0; i<line.length(); i++) {
            System.out.println(line.charAt(i));
        }
    }
}
```

### 2.4.3 统计字符个数

键盘录入一个字符串，统计字符串中大小写字母及数字字符个数.

```java
public class StringTest2 {
    public static void main(String[] args) {
        //键盘录入一个字符串数据
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个字符串数据：");
        String s = sc.nextLine();

        //定义三个统计变量，初始化值都是0
        int bigCount = 0;
        int smallCount = 0;
        int numberCount = 0;

        //遍历字符串，得到每一个字符
        for(int x=0; x<s.length(); x++) {
            char ch = s.charAt(x);
            //拿字符进行判断
            if(ch>='A'&&ch<='Z') {
              	bigCount++;
            }else if(ch>='a'&&ch<='z') {
              	smallCount++;
            }else if(ch>='0'&&ch<='9') {
              	numberCount++;
            }else {
              	System.out.println("该字符"+ch+"非法");
            }
        }

        //输出结果
        System.out.println("大写字符："+bigCount+"个");
        System.out.println("小写字符："+smallCount+"个");
        System.out.println("数字字符："+numberCount+"个");
    }
}
```

### 2.4.4 拼接字符串

需求：定义一个方法，把数组{1,2,3}按照指定个格式拼接成一个字符串。格式参照如下：[word1#word2#word3]。

```java
public class StringTest1 {
    public static void main(String[] args) {
        //定义一个int类型的数组
        int[] arr = {1, 2, 3};
        //调用方法
        String s = arrayToString(arr);
        //输出结果
        System.out.println("s:" + s);
    }
    /*
     * 写方法实现把数组中的元素按照指定的格式拼接成一个字符串
     * 两个明确：
     * 返回值类型：String
     * 参数列表：int[] arr
     */
    public static String arrayToString(int[] arr) {
        // 创建字符串s
        //String s = new String("[");
        String s="[";
        // 遍历数组，并拼接字符串
        for (int x = 0; x < arr.length; x++) {
            if (x == arr.length - 1) {
              	s = s+arr[x]+"]";
            } else {
              	s = s+arr[x]+"#";
            }
        }
        return s;
    }
}
```

### 2.4.5 字符串反转

定义一个方法，实现字符串反转。键盘录入一个字符串，调用该方法后，在控制台输出结果

	例如，键盘录入 abc，输出结果 cba

```java
/*
    思路：
        1:键盘录入一个字符串，用 Scanner 实现
        2:定义一个方法，实现字符串反转。返回值类型 String，参数 String s
        3:在方法中把字符串倒着遍历，然后把每一个得到的字符拼接成一个字符串并返回
        4:调用方法，用一个变量接收结果
        5:输出结果
 */
public class StringTest05 {
    public static void main(String[] args) {
        //键盘录入一个字符串，用 Scanner 实现
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入一个字符串：");
        String line = sc.nextLine();

        //调用方法，用一个变量接收结果
        String s = reverse(line);

        //输出结果
        System.out.println("s:" + s);
    }

    //定义一个方法，实现字符串反转
    /*
        两个明确：
            返回值类型：String
            参数：String s
     */
    public static String reverse(String s) {
        //在方法中把字符串倒着遍历，然后把每一个得到的字符拼接成一个字符串并返回
        String ss = "";

        for(int i=s.length()-1; i>=0; i--) {
            ss += s.charAt(i);
        }

        return ss;
    }
}
```

# 第三章 StringBuilder类

## 3.1 StringBuilder概述

查阅`java.lang.StringBuilder`的API，StringBuilder又称为可变字符序列，它是一个类似于 String 的字符串缓冲区，通过某些方法调用可以改变该序列的长度和内容。

原来StringBuilder是个字符串的缓冲区，即它是一个容器，容器中可以装很多字符串。并且能够对其中的字符串进行各种操作。

说明：

​	1、缓冲区：就是一个临时空间，它里面可以临时存储数据。缓冲区本身就是一个容器。

​	2、字符串缓冲区：它本身就是一个容器，只不过这个缓冲区最后会把里面的所有数据全部给变成字符串而已。

​	3、当我们需要对字符串进行数据的修改，这时不能直接使用String类，而把需要修改的字符串先存储到字符串缓冲区容器中，在容器中进行各种修改，等最后确定不再修改的时候，把里面的数据变成一个字符串，然后存储在字符串常量池中。

## 3.2 StringBuilder类的特点

StringBuilder：

1）是一个字符串缓冲区，其实就是一个容器；

2）长度是可变的，任意类型都可以。注意：是将任意数据都转成字符串进行存储；

3）容器对象提供很多对容器中的数据操作的功能，比如添加，删除，修改，查询；

4）所有的数据最终都会变成一个字符串；

和数组最大的不同就是数组存储完可以单独操作每一个元素，每一个元素都是独立的。

字符串缓冲区，所有存储的元素都会被转成字符串，而且变成了一个更长的字符串。

## 3.3 StringBuilder存储数据的原理

它的内部拥有一个数组用来存放字符串内容，进行字符串拼接时，直接在数组中加入新内容。StringBuilder会自动维护数组的扩容。原理如下图所示：(默认16字符空间，超过自动扩充)

![06-StringBuilder的原理](img/StringBuilder的原理.png)

**注意：**

**解释：StringBuilder底层体现就是一个字符数组，StringBuilder类的对象将数组封装起来，然后对外提供很多便捷方法，而数组本身是没有什么太多方法的。如果外界将数据存放到底层的数组中，如果底层数组空间存放不下外界传递过来的值，那么jvm会基于原来存在的数组在创建一个新的数组，长度是原来数组的一倍，然后jvm将原来数组的数据全部复制（遍历数组，将数据添加到新的数组中）到新的数组中，然后在数组后面的空间中给数组添加新的值，如果还是存不下在创建一个新的数组。**

## 3.4 StringBuilder类和String类的区别

- String类：内容是不可变的
- StringBuilder类：内容是可变的

## 3.5 构造方法

根据StringBuilder的API文档，常用构造方法有2个：

- `public StringBuilder()`：构造一个空的StringBuilder容器。
- `public StringBuilder(String str)`：构造一个StringBuilder容器，并将字符串添加进去。

```java
public class StringBuilderDemo {
    public static void main(String[] args) {
        StringBuilder sb1 = new StringBuilder();
        System.out.println(sb1); // (空白)
        // 使用带参构造
        StringBuilder sb2 = new StringBuilder("itcast");
        System.out.println(sb2); // itcast
    }
}
```

## 3.6 常用方法

StringBuilder常用的方法有2个：

- `public StringBuilder append(...)`：添加任意类型数据的字符串形式，并返回当前对象自身。
- `public String toString()`：将当前StringBuilder对象转换为String对象。
- 'public StringBuilder reverse()`：返回反转的字符序列

### append方法

append方法具有多种重载形式，可以接收任意类型的参数。任何数据作为参数都会将对应的字符串内容添加到StringBuilder中。例如：

```java
public class Demo02StringBuilder {
	public static void main(String[] args) {
		//创建对象
		StringBuilder builder = new StringBuilder();
		//public StringBuilder append(任意类型)
		StringBuilder builder2 = builder.append("hello");
		//对比一下
		System.out.println("builder:"+builder);
		System.out.println("builder2:"+builder2);
		System.out.println(builder == builder2); //true
	    // 可以添加 任何类型
		builder.append("hello");
		builder.append("world");
		builder.append(true);
		builder.append(100);
		// 在我们开发中，会遇到调用一个方法后，返回一个对象的情况。然后使用返回的对象继续调用方法。
        // 这种时候，我们就可以把代码现在一起，如append方法一样，代码如下
		//链式编程
		builder.append("hello").append("world").append(true).append(100);
		System.out.println("builder:"+builder);
	}
}
```

> 备注：StringBuilder已经覆盖重写了Object当中的toString方法。

### toString方法

通过toString方法，StringBuilder对象将会转换为不可变的String对象。如：

```java
public class Demo16StringBuilder {
    public static void main(String[] args) {
        // 链式创建
        StringBuilder sb = new StringBuilder("Hello").append("World").append("Java");
        // 调用方法
        String str = sb.toString();
        System.out.println(str); // HelloWorldJava
    }
}
```

### reverse方法

通过 reverse()方法可以实现字符串缓冲区中的数据反转。前后进行交换。如：

```java
public class Demo16StringBuilder {
    public static void main(String[] args) { 
	//public StringBuilder reverse()：返回相反的字符序列
 	 StringBuilder sb = new StringBuilder("Hello").append("World").append("Java");
   	 sb.reverse();
   	 System.out.println("sb:" + sb);
   }
}
```



## 3.7 StringBuilder和String相互转换

- StringBuilder转换为String

          public String toString()：通过 toString() 就可以实现把 StringBuilder 转换为 String

- String转换为StringBuilder

          public StringBuilder(String s)：通过构造方法就可以实现把 String 转换为 StringBuilder

- 示例代码

```java
public class StringBuilderDemo02 {
    public static void main(String[] args) {
        /*
        //StringBuilder 转换为 String
        StringBuilder sb = new StringBuilder();
        sb.append("hello");

        //String s = sb; //这个是错误的做法

        //public String toString()：通过 toString() 就可以实现把 StringBuilder 转换为 String
        String s = sb.toString();
        System.out.println(s);
        */

        //String 转换为 StringBuilder
        String s = "hello";

        //StringBuilder sb = s; //这个是错误的做法

        //public StringBuilder(String s)：通过构造方法就可以实现把 String 转换为 StringBuilder
        StringBuilder sb = new StringBuilder(s);

        System.out.println(sb);
    }
}
```

## 3.8 StringBuilder练习

- 字符串拼接

  定义一个方法，把 int 数组中的数据按照指定的格式拼接成一个字符串返回，调用该方法，

  	并在控制台输出结果。例如，数组为int[] arr = {1,2,3}; ，执行方法后的输出结果为：[1, 2, 3]

  ```java
  /*
      思路：
          1:定义一个 int 类型的数组，用静态初始化完成数组元素的初始化
          2:定义一个方法，用于把 int 数组中的数据按照指定格式拼接成一个字符串返回。
            返回值类型 String，参数列表 int[] arr
          3:在方法中用 StringBuilder 按照要求进行拼接，并把结果转成 String 返回
          4:调用方法，用一个变量接收结果
          5:输出结果
   */
  public class StringBuilderTest01 {
      public static void main(String[] args) {
          //定义一个 int 类型的数组，用静态初始化完成数组元素的初始化
          int[] arr = {1, 2, 3};
  
          //调用方法，用一个变量接收结果
          String s = arrayToString(arr);
  
          //输出结果
          System.out.println("s:" + s);
  
      }
  
      //定义一个方法，用于把 int 数组中的数据按照指定格式拼接成一个字符串返回
      /*
          两个明确：
              返回值类型：String
              参数：int[] arr
       */
      public static String arrayToString(int[] arr) {
          //在方法中用 StringBuilder 按照要求进行拼接，并把结果转成 String 返回
          StringBuilder sb = new StringBuilder();
  
          sb.append("[");
  
          for(int i=0; i<arr.length; i++) {
              if(i == arr.length-1) {
                  sb.append(arr[i]);
              } else {
                  sb.append(arr[i]).append(", ");
              }
          }
  
          sb.append("]");
  
          String s = sb.toString();
  
          return  s;
      }
  }
  ```

- 字符串反转

定义一个方法，实现字符串反转。键盘录入一个字符串，调用该方法后，在控制台输出结果

	例如，键盘录入abc，输出结果 cba

```java
/*
    思路：
        1:键盘录入一个字符串，用 Scanner 实现
        2:定义一个方法，实现字符串反转。返回值类型 String，参数 String s
        3:在方法中用StringBuilder实现字符串的反转，并把结果转成String返回
        4:调用方法，用一个变量接收结果
        5:输出结果
 */
public class StringBuilderTest02 {
    public static void main(String[] args) {
        //键盘录入一个字符串，用 Scanner 实现
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入一个字符串：");
        String line = sc.nextLine();

        //调用方法，用一个变量接收结果
        String s = myReverse(line);

        //输出结果
        System.out.println("s:" + s);
    }

    //定义一个方法，实现字符串反转。返回值类型 String，参数 String s
    /*
        两个明确：
            返回值类型：String
            参数：String s
     */
    public static String myReverse(String s) {
        //在方法中用StringBuilder实现字符串的反转，并把结果转成String返回
        //String --- StringBuilder --- reverse() --- String
//        StringBuilder sb = new StringBuilder(s);
//        sb.reverse();
//        String ss = sb.toString();
//        return ss;

       return new StringBuilder(s).reverse().toString();
    }
}
```

