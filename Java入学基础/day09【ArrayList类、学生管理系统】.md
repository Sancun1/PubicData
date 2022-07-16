# day09【ArrayList类、学生管理系统】

## 今日内容

*  ArrayList类
*  学生管理系统


## 教学目标

- [ ] 能够知道集合和数组的区别

- [ ] 能够完成ArrayList集合添加字符串并遍历

- [ ] 能够完成ArrayList集合添加学生对象并遍历

- [ ] 能够完成学生管理系统主界面编写

- [ ] 能够完成学生管理系统添加操作

- [ ] 能够完成学生管理系统查询操作

- [ ] 能够完成学生管理系统删除操作

- [ ] 能够完成学生管理系统修改操作



#  第一章 ArrayList类

## 1.1 引入——对象数组

回顾之前都学习过哪些容器可以保存数据：

1）变量空间中就可以保存数据；

2）数组中可以保存多个类型相同的数据；

需求：使用数组存储3个学生对象，然后遍历并输出。

分析和步骤：

分析：

我们之前只学习过创建数组存储基本数据类型常量数据，比如创建一个数组来存储整数类型。那么我们可以这样做：假设存储int类型数据，创建int数组，int[] arr=new int[3];

假设我们要存储String类型的数据，则需要创建String类型的数组，

String[] arr=new String[3];

 	而现在我们要存Student类型的数据，所以这里我们应该创建Student类型的数组，Student[]，由于String类和Student都是类，只不过Student类是我们自定义类，所以我们可以按照定义String类型的数组去定义Student类型的数组。

步骤：

​	1）：创建学生类

 	2）：创建学生数组

  	3）：创建学生对象

  	4）：添加学生到数组

 	5）：遍历数组

代码如下所示：

Student类的代码如下所示：

```java
package cn.itcast.sh.demo;
//描述学生
public class Student {
	//属性
	String name;
	int age;
	//定义构造函数给属性初始化值
	public Student(String name, int age) {
		this.name = name;
		this.age = age;
	}
	//给属性生成get和set方法
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
}
```

ArrayDemo类代码如下所示：

```java
package cn.itcast.sh.demo;
/*
 * 需求：使用数组存储3个学生对象，然后遍历并输出。
 * 如果使用数组存储int类型的数据：int[] arr=new int[3];
 * 如果使用数组存储String类型的数据：String[] arr=new String[3];
 * 如果使用数组存储Student类型的数据：Student[] arr=new Student[3];
 */
public class ArrayDemo {
	public static void main(String[] args) {
		//创建Student类型的数组
		Student[] arr=new Student[3];
		//创建Student类的对象
		Student s1=new Student("heixuanfeng",19);
		Student s2=new Student("bandao",18);
		Student s3=new Student("zhujiao",20);
		//将学生对象存储到数组中
		arr[0]=s1;
		arr[1]=s2;
		arr[2]=s3;
		//遍历数组
		for (int i = 0; i < arr.length; i++) {
			//通过数组名和下标取出Student类的数组中的数据 arr[i]
			Student s=arr[i];
			//输出数据
			System.out.println(s.getName()+"====="+s.getAge());
		}
	}
}
```

#### 对象数组的内存图

![](img/对象数组内存图.jpg)



以上方案虽然可以实现结果，但是对于开发人员来讲书写比较麻烦，那么有没有其他解决办法呢？

到目前为止我们只学习了2种存储数据的容器：变量 、数组。

1）上述我们使用的是数组来存储类的对象，那其他两种容器能否替代数组并简化代码的书写呢，答案是否定的，

因为首先要排除变量，变量只能保存具体的一个值，而上述有三个对象需要保存，所以变量不可以。

补充：在这里需要强调一点，对于基本数据类型变量或者叫做普通变量空间只能保存基本数据类型，不能保存对象，而引用变量是可以保存对象的，但是引用变量只能保存一个对象。

那我们是否还有除了数组更简单的办法吗？

如果按照我们之前的知识，在这里我们只能使用数组，但是今天我们又会学习一个新的容器，就是**集合容器**可以解决上述办法，并且还可以简化上述代码的书写。

## 1.2 集合概述

什么是集合？

集合也是一种容器，也可以存放数据。随着我们学习技术的深入，那么我们在程序中创建的对象也会越来越多。这时在程序中就要想办法先把这些对象给存储起来，然后在需要使用这些对象的时候从容器中把对象取出，再去使用这些对象。

## 1.3 集合与数组区别

1）从长度来讲：

数组：需要固定长度。

集合：长度可以改变，可以根据保存的数据进行扩容。

2）从存储内容上：

数组：可以存储基本类型数据，还可以存储引用类型的数据（比如：String和上述演示的Student类）。

 **集合：只能存储引用类型的数据，也就是说集合只能存储类的对象。**

3）从存储类型上：

数组：只能存储相同类型的数据。

集合：可以存储不同类型的数据，集合中可以存储任意类型的**引用数据类型。**



## 1.4 什么是ArrayList类

集合容器从jdk1.2之后形成了一个庞大的继承体系图，而我们这里先学习集合中的一种，叫做ArrayList集合类，其余集合到后面我们会详细讲解。

java.util.ArrayList` 是大小可变的数组的实现，存储在集合内的数据称为元素。此类提供一些方法来操作内部存储的元素。 `ArrayList 中可不断添加元素，其大小也自动增长。

## 1.5 ArrayList使用步骤

**查看类**

- `java.util.ArrayList <E>` ：该类需要 import导入使后使用。  

`<E>` ，表示一种指定的数据类型，叫做泛型。`E` ，取自Element（元素）的首字母。在出现`E` 的地方，我们使用一种引用数据类型将其替换即可，表示我们将存储哪种引用类型的元素。代码如下：

```java
ArrayList<String>，ArrayList<Student>
```

**查看构造方法**

- `public ArrayList() `：构造一个内容为空的集合。

基本格式:

```java 
ArrayList<String> list = new ArrayList<String>();
```

在JDK 7后,右侧泛型的尖括号之内可以留空，但是<>仍然要写。简化格式：

```java
ArrayList<String> list = new ArrayList<>();
```

**查看成员方法**

- ` public boolean add(E e)  `： 将指定的元素添加到此集合的尾部。

  参数 `E e `，在构造ArrayList对象时，`<E>`指定了什么数据类型，那么`add(E e)`方法中，只能添加什么数据类型的对象。

  ​

**需求：使用ArrayList类，存储三个字符串元素**

代码如下：

```java
public class Test02StudentArrayList {
    public static void main(String[] args) {
        //创建集合对象
        ArrayList<String> list = new ArrayList<>();

        //定义字符串对象
        String s1 = "曹操";
        String s2 = "刘备";
        String s3 = "孙权";

        //打印ArrayList集合
        System.out.println(list);

        //把字符串作为元素添加到集合
        list.add(s1);
        list.add(s2);
        list.add(s3);

        //打印ArrayList集合
        System.out.println(list);
    }
}
```

## 1.6 常用方法和遍历

对于元素的操作,基本体现在——增、删、查。常用的方法有：

- `public boolean add(E e)`：将指定的元素添加到此集合的尾部。 

- `public E remove(int index)` ：移除此集合中指定位置上的元素。返回被删除的元素。   

- ` public E get(int index)` ：返回此集合中指定位置上的元素。返回获取的元素。

- `public int size()` ：返回此集合中的元素数。遍历集合时，可以控制索引范围，防止越界。

这些都是最基本的方法，操作非常简单，代码如下:

```java
public class Demo01ArrayListMethod {
    public static void main(String[] args) {
        //创建集合对象
        ArrayList<String> list = new ArrayList<String>();

        //添加元素
        list.add("hello");
        list.add("world");
        list.add("java");

        //public E get(int index):返回指定索引处的元素
        System.out.println("get:"+list.get(0));
        System.out.println("get:"+list.get(1));
        System.out.println("get:"+list.get(2));

        //public int size():返回集合中的元素的个数
        System.out.println("size:"+list.size());

        //public E remove(int index):删除指定索引处的元素，返回被删除的元素
        System.out.println("remove:"+list.remove(0));

        //遍历输出
        for(int i = 0; i < list.size(); i++){
        	System.out.println(list.get(i));
        }
    }
}
```

## 1.7 如何存储基本数据类型

ArrayList集合不能存储基本类型，只能存储引用类型的数据。类似**`<int>`不能写**，但是存储基本数据类型对应的包装类型是可以的。所以，想要存储基本类型数据，`<>`中的数据类型，必须转换后才能编写，转换写法如下：

| 基本类型 | 基本类型包装类 |
| -------- | -------------- |
| byte     | Byte           |
| short    | Short          |
| int      | Integer        |
| long     | Long           |
| float    | Float          |
| double   | Double         |
| char     | Character      |
| boolean  | Boolean        |

我们发现，只有`Integer`和`Character`需要特殊记忆，其他基本类型只是首字母大写即可。那么存储基本类型数据，代码如下：

```java
public class Demo02ArrayListMethod {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<Integer>();
        list.add(1);
        list.add(2);
        list.add(3);
        list.add(4);

        System.out.println(list);     
    }
}
```

注意：我们发现基本数据类型只能作为简单基本算术运算，但是我们在开发中可不是只有简单算术运算，我们希望，基本数据类型对应的数据有更广泛的操作，所以我们可以将基本数据类型包装成对应的包装类，然后使用对应类中的方法，这样就可以有更广泛的操作了。比如可以求出int类型的最大和最小值，将一个十进制整数变为其他进制等。

## 1.8 ArrayList练习

### 1.8.1 数值添加到集合

生成6个1~33之间的随机整数,添加到集合,并遍历 

```java
public class Test01ArrayList {
    public static void main(String[] args) {
        // 创建Random 对象
        Random random = new Random();

        // 创建ArrayList 对象
        ArrayList<Integer> list = new ArrayList<>();

        // 添加随机数到集合
        for (int i = 0; i < 6; i++) {
            int r = random.nextInt(33) + 1;
            list.add(r);
        }

        // 遍历集合输出
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
    }
}
```

### 1.8.2 自定义对象添加到集合

创建一个存储学生对象的集合，存储3个学生对象，使用程序实现在控制台遍历该集合

```java
public class ArrayListTest03 {
  public static void main(String[] args) {
    //创建集合对象
    ArrayList<Student> list = new ArrayList<Student>();

    //创建学生对象
    Student s1 = new Student("赵丽颖",18);
    Student s2 = new Student("唐嫣",20);
    Student s3 = new Student("景甜",25);
    
    //把学生对象作为元素添加到集合中
    list.add(s1);
    list.add(s2);
    list.add(s3);    

    //遍历集合
    for(int x = 0; x < list.size(); x++) {
      Student s = list.get(x);
      System.out.println(s.getName()+"---"+s.getAge());
    }
  }
}
```

### 1.8.3 ArrayList存储学生对象并遍历升级版

创建一个存储学生对象的集合，存储3个学生对象，使用程序实现在控制台遍历该集合

学生的姓名和年龄来自于键盘录入

```java
/*
    思路：
        1:定义学生类，为了键盘录入数据方便，把学生类中的成员变量都定义为String类型
        2:创建集合对象
        3:键盘录入学生对象所需要的数据
        4:创建学生对象，把键盘录入的数据赋值给学生对象的成员变量
        5:往集合中添加学生对象
        6:遍历集合，采用通用遍历格式实现
 */
public class ArrayListTest04 {
    public static void main(String[] args) {
        //创建集合对象
        ArrayList<Student> array = new ArrayList<Student>();

        //为了提高代码的复用性，我们用方法来改进程序
        addStudent(array);
        addStudent(array);
        addStudent(array);

        //遍历集合，采用通用遍历格式实现
        for (int i = 0; i < array.size(); i++) {
            Student s = array.get(i);
            System.out.println(s.getName() + "," + s.getAge());
        }
    }

    /*
        两个明确：
            返回值类型：void
            参数：ArrayList<Student> array
     */
    public static void addStudent(ArrayList<Student> array) {
        //键盘录入学生对象所需要的数据
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入学生姓名:");
        String name = sc.nextLine();

        System.out.println("请输入学生年龄:");
        String age = sc.nextLine();

        //创建学生对象，把键盘录入的数据赋值给学生对象的成员变量
        Student s = new Student();
        s.setName(name);
        s.setAge(age);

        //往集合中添加学生对象
        array.add(s);
    }
}
```



### 1.8.4 ArrayList类型作为参数_指定格式打印集合

定义以指定格式打印集合的方法(ArrayList类型作为参数)，使用{}扩起集合，使用@分隔每个元素。格式参照 {元素@元素@元素}。

```java
public class Test03ArrayList {
    public static void main(String[] args) {
        // 创建集合对象
        ArrayList<String> list = new ArrayList<String>();

        // 添加字符串到集合中
        list.add("张三丰");
        list.add("宋远桥");
        list.add("张无忌");
        list.add("殷梨亭");

        // 调用方法
        printArrayList(list);
    }

  	public static void printArrayList(ArrayList<String> list) {
        // 拼接左括号
        System.out.print("{");
        // 遍历集合
        for (int i = 0; i < list.size(); i++) {
            // 获取元素
            String s = list.get(i);
            // 拼接@符号
            if (i != list.size() - 1) {
                System.out.print(s + "@");
            } else {
                // 拼接右括号
                System.out.print(s + "}");
            }
        }
    }
}
```

### 1.8.5 ArrayList类型作为方法返回值_获取集合方法

定义获取所有偶数元素集合的方法(ArrayList类型作为返回值)。

分析：将生成的1-1000的随机数添加到集合ArrayList中，一共添加10个随机数。

```java
public class Test04ArrayList {
    public static void main(String[] args) {
        // 创建Random 对象
        Random random = new Random();
        // 创建ArrayList 对象
        ArrayList<Integer> list = new ArrayList<>();

        // 添加随机数到集合
        for (int i = 0; i < 10; i++) {
            int r = random.nextInt(1000) + 1;
            list.add(r);
        }
        // 调用偶数集合的方法
        ArrayList<Integer> arrayList = getArrayList(list);
        System.out.println(arrayList);
    }

  	public static ArrayList<Integer> getArrayList(ArrayList<Integer> list) {
        // 创建小集合,来保存偶数
        ArrayList<Integer> smallList = new ArrayList<>();

        // 遍历list
        for (int i = 0; i < list.size(); i++) {
            // 获取元素
            Integer num = list.get(i);
            // 判断为偶数,添加到小集合中
            if (num % 2 == 0){
              	smallList.add(num);
            }
        }
        // 返回小集合
        return smallList;
    }
}
```

# 第二章 学生管理系统

![学生管理系统流程](assets/学生管理系统流程.png)

## **2.1** 学生管理系统案例需求

系统演示：将我之前准备好的resource文件夹下的studentManager项目导入eclipse中，然后运行该项目，具体演示如下所示：

![](img/1.bmp)

利用集合完成对学生的增删改查四个功能。

## **2.2** 学生管理系统案例实现

步骤如下：

  A:定义学生类

  B:学生管理系统的主界面的代码编写

  C:学生管理系统的查看所有学生的代码编写

  D:学生管理系统的添加学生的代码编写

  E:学生管理系统的删除学生的代码编写

  F:学生管理系统的修改学生的代码编写

 

### **2.2.1** **创建学生类:**

学生类Student有id name age address属性。

注意：

在eclipse中可以使用快捷键生成Student类的构造函数和get/set方法：

1）生成Student类的空参构造函数：alt+shift+s---->选择Generate Constructors from Superclass...；

2）生成Student类的满参构造函数：alt+shift+s---->选择Generate Constructor using Fields...；

3）生成get和set方法：alt+shift+s---->选择 Generate Getters and Setters...；

```java
package com.itheima;
/*
 * 这是我的学生类
 */
public class Student {
	//学号
	private String id;
	//姓名
	private String name;
	//年龄 我们键盘录入，所以为了统一，年龄定义为String类型
	private String age;
	//居住地
	private String address;
	
	public Student() {
		
	}

	public Student(String id, String name, String age, String address) {
		this.id = id;
		this.name = name;
		this.age = age;
		this.address = address;
	}

	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public String getAge() {
		return age;
	}

	public void setAge(String age) {
		this.age = age;
	}

	public String getAddress() {
		return address;
	}

	public void setAddress(String address) {
		this.address = address;
	}
}
```

### **2.2.2** 学生管理系统界面实现:

说明：关于学生的管理系统增删改查数据，都是针对集合，所以我们需要创建一个ArrayList集合对象来存储数据。

```java
package com.itheima;
import java.util.ArrayList;
import java.util.Scanner;

/*
 * 这是我的学生管理系统的主类
 * 
 * 步骤如下：
 * A:定义学生类
 * B:学生管理系统的主界面的代码编写
 * C:学生管理系统的查看所有学生的代码编写
 * D:学生管理系统的添加学生的代码编写
 * E:学生管理系统的删除学生的代码编写
 * F:学生管理系统的修改学生的代码编写
 */
public class StudentManagerTest {
	public static void main(String[] args) {
		// 创建集合对象，用于存储学生数据
		ArrayList<Student> list= new ArrayList<Student>();

		// 为了让程序能够回到这里来，我们使用循环
		while (true) {
			// 这是学生管理系统的主界面
			System.out.println("--------欢迎来到学生管理系统--------");
			System.out.println("1 查看所有学生");
			System.out.println("2 添加学生");
			System.out.println("3 删除学生");
			System.out.println("4 修改学生");
			System.out.println("5 退出");
			System.out.println("请输入你的选择：");
			// 创建键盘录入对象
			Scanner sc = new Scanner(System.in);
			String choiceString = sc.nextLine();
			// 用switch语句实现选择
			switch (choiceString) {
			case "1":
				// 查看所有学生
				break;
			case "2":
				// 添加学生
				break;
			case "3":
				// 删除学生
				break;
			case "4":
				// 修改学生
				break;
			case "5":
				// 退出
				// System.out.println("谢谢你的使用");
				// break;
			default:
				System.out.println("谢谢你的使用");
				System.exit(0); // JVM退出
				//break;
			}
		}
	}
}
```

### **2.2.3** 学生管理系统之查询所有学生功能

```java
package com.itheima.test;
import java.util.ArrayList;
import java.util.Scanner;

/*
 * 这是我的学生管理系统的主类
 * 
 * 步骤如下：
 * A:定义学生类
 * B:学生管理系统的主界面的代码编写
 * C:学生管理系统的查看所有学生的代码编写
 * D:学生管理系统的添加学生的代码编写
 * E:学生管理系统的删除学生的代码编写
 * F:学生管理系统的修改学生的代码编写
 */
public class StudentManagerTest {
	public static void main(String[] args) {
		//创建集合对象，用于存储学生数据
		ArrayList<Student> list= new ArrayList<Student>();
		
		//为了让程序能够回到这里来，我们使用循环
		while(true) {
			//这是学生管理系统的主界面
			System.out.println("--------欢迎来到学生管理系统--------");
			System.out.println("1 查看所有学生");
			System.out.println("2 添加学生");
			System.out.println("3 删除学生");
			System.out.println("4 修改学生");
			System.out.println("5 退出");
			System.out.println("请输入你的选择：");
			//创建键盘录入对象
			Scanner sc = new Scanner(System.in);
			String choiceString = sc.nextLine();
			//用switch语句实现选择
			switch(choiceString) {
			case "1":
				//查看所有学生
				findAllStudent(list);
				break;
			case "2":
				//添加学生
				break;
			case "3":
				//删除学生
				break;
			case "4":
				//修改学生
				break;
			case "5":
				//退出
				//System.out.println("谢谢你的使用");
				//break;
			default:
				System.out.println("谢谢你的使用");
				System.exit(0); //JVM退出
				break;
			}
		}
	}
	//查看所有学生
	public static void findAllStudent(ArrayList<Student> list) {
		//首先来判断集合中是否有数据，如果没有数据，就给出提示，并让该方法不继续往下执行
		if(list.size() == 0) {
			System.out.println("不好意思,目前没有学生信息可供查询,请回去重新选择你的操作");
			return;
		}
		
		//\t 其实就是一个tab键的位置
		System.out.println("学号\t\t姓名\t年龄\t居住地");
		for(int i=0; x<list.size(); i++) {
			Student s = list.get(i);
			System.out.println(s.getId()+"\t"+s.getName()+"\t"+s.getAge()+"\t"+s.getAddress());
		}
	}
}
```

### **2.2.4** 学生管理系统之添加学生功能

```java
package com.itheima;

import java.util.ArrayList;
import java.util.Scanner;

/*
 * 这是我的学生管理系统的主类
 * 
 * 步骤如下：
 * A:定义学生类
 * B:学生管理系统的主界面的代码编写
 * C:学生管理系统的查看所有学生的代码编写
 * D:学生管理系统的添加学生的代码编写
 * E:学生管理系统的删除学生的代码编写
 * F:学生管理系统的修改学生的代码编写
 */
public class StudentManagerTest {
	public static void main(String[] args) {
		//创建集合对象，用于存储学生数据
		ArrayList<Student> list= new ArrayList<Student>();
		
		//为了让程序能够回到这里来，我们使用循环
		while(true) {
			//这是学生管理系统的主界面
			System.out.println("--------欢迎来到学生管理系统--------");
			System.out.println("1 查看所有学生");
			System.out.println("2 添加学生");
			System.out.println("3 删除学生");
			System.out.println("4 修改学生");
			System.out.println("5 退出");
			System.out.println("请输入你的选择：");
			//创建键盘录入对象
			Scanner sc = new Scanner(System.in);
			String choiceString = sc.nextLine();
			//用switch语句实现选择
			switch(choiceString) {
			case "1":
				//查看所有学生
//findAllStudent(list);
				break;
			case "2":
				//添加学生
				addStudent(list);
				break;
			case "3":
				//删除学生
				break;
			case "4":
				//修改学生
				break;
			case "5":
				//退出
				//System.out.println("谢谢你的使用");
				//break;
			default:
				System.out.println("谢谢你的使用");
				System.exit(0); //JVM退出
				break;
			}
		}
	}
	//添加学生
	public static void addStudent(ArrayList<Student> list) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入学生学号：");
		String id = sc.nextLine();
		System.out.println("请输入学生姓名：");
		String name = sc.nextLine();
		System.out.println("请输入学生年龄：");
		String age = sc.nextLine();
		System.out.println("请输入学生居住地：");
		String address = sc.nextLine();
		
		//创建学生对象
		Student s = new Student();
		s.setId(id);
		s.setName(name);
		s.setAge(age);
		s.setAddress(address);
		//把学生对象作为元素添加到集合
		list.add(s);
		//给出提示
		System.out.println("添加学生成功");
	}
}
```

注意：上述添加学生的代码是存在问题的，正常系统中，学生的学号是不能重复的，而按照我们上述书写的代码，学生的学号是可以重复的，演示结果如下：

![](img/2.bmp)

所以我们应该优化添加学生的代码，对于添加学生的时候，当输入学生学号的时候，我们要对学号进行合法的判断，如果新添加的学号在集合中已经存在了，那么我们应该提示学号已经存在了，重新输入学号。

注意：只是对学生的学号进行判断即可，其他的属性不用判断。

优化添加学生的代码如下所示：

```java
//添加学生
	public static void addStudent(ArrayList<Student> list) {
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		
		//为了让id能够被访问到，我们就把id定义在了循环的外面
		String id;
		
		//为了让代码能够回到这里，用循环
		while(true) {
			System.out.println("请输入学生学号：");
			//String id = sc.nextLine();
			id = sc.nextLine();
			
			//判断学号有没有被人占用
			//定义标记 true 表示学号被占用，重新输入学号，false表示没有被占用,结束循环，不用重新输入学号，向下执行其他的内容
			boolean flag = false;
			//遍历集合，得到每一个学生
			for(int i=0; i<list.size(); i++) {
				Student s = list.get(i);
				//获取该学生的学号，和键盘录入的学号进行比较
				if(s.getId().equals(id)) {
					flag = true; //说明学号被占用了
					break;
				}
			}
			
			if(flag) {
				System.out.println("你输入的学号已经被占用,请重新输入");
			}else {
				break; //结束循环
			}
		}

		System.out.println("请输入学生姓名：");
		String name = sc.nextLine();
		System.out.println("请输入学生年龄：");
		String age = sc.nextLine();
		System.out.println("请输入学生居住地：");
		String address = sc.nextLine();
		
		//创建学生对象
		Student s = new Student();
		s.setId(id);
		s.setName(name);
		s.setAge(age);
		s.setAddress(address);
		
		//把学生对象作为元素添加到集合
		list.add(s);
		
		//给出提示
		System.out.println("添加学生成功");
	}
```

### **2.2.5** 学生管理系统之删除学生功能

删除学生的思路：键盘录入一个学号，到集合中去查找，看是否有学生使用的是该学号，如果有就删除该学生。

**注意:在删除之前，我们需要判断该学号是否存在。**

**补充：可以借助一个变量index来判断学号是否存在：**

**index=-1，表示集合中不存在该学号，重新选择；**

**index !=-1，表示该学号存在，则将学号所属对象所在的集合中的索引赋值给index。然后使用集合中的方法remove(index)删除该学生对象。**

```java
package com.itheima;

import java.util.ArrayList;
import java.util.Scanner;

/*
 * 这是我的学生管理系统的主类
 * 
 * 步骤如下：
 * A:定义学生类
 * B:学生管理系统的主界面的代码编写
 * C:学生管理系统的查看所有学生的代码编写
 * D:学生管理系统的添加学生的代码编写
 * E:学生管理系统的删除学生的代码编写
 * F:学生管理系统的修改学生的代码编写
 */
public class StudentManagerTest {
	public static void main(String[] args) {
		//创建集合对象，用于存储学生数据
		ArrayList<Student> list= new ArrayList<Student>();
		
		//为了让程序能够回到这里来，我们使用循环
		while(true) {
			//这是学生管理系统的主界面
			System.out.println("--------欢迎来到学生管理系统--------");
			System.out.println("1 查看所有学生");
			System.out.println("2 添加学生");
			System.out.println("3 删除学生");
			System.out.println("4 修改学生");
			System.out.println("5 退出");
			System.out.println("请输入你的选择：");
			//创建键盘录入对象
			Scanner sc = new Scanner(System.in);
			String choiceString = sc.nextLine();
			//用switch语句实现选择
			switch(choiceString) {
			case "1":
				//查看所有学生
//findAllStudent(list);
				break;
			case "2":
				//添加学生
//addStudent(list);
				break;
			case "3":
				//删除学生
				deleteStudent(list);
				break;
			case "4":
				//修改学生
				break;
			case "5":
				//退出
				//System.out.println("谢谢你的使用");
				//break;
			default:
				System.out.println("谢谢你的使用");
				System.exit(0); //JVM退出
				break;
			}
		}
	}
	
	//删除学生
	public static void deleteStudent(ArrayList<Student> list) {
		//删除学生的思路：键盘录入一个学号，到集合中去查找，看是否有学生使用的是该学号，如果有就删除该学生
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入你要删除的学生的学号：");
		String id = sc.nextLine();
		
		/*
		//遍历集合
		for(int x=0; x<list.size(); x++) {
			//获取到每一个学生对象
			Student s = list.get(x);
			//拿这个学生对象的学号和键盘录入的学号进行比较
			if(s.getId().equals(id)) {
				list.remove(x); //根据索引删除
				break;//因为学生的学号是不可能重复的，删除之后直接停止for循环
			}
		}
		//循环结束，删除成功
		//给出提示删除成功
		System.out.println("删除学生成功");
		*/
		//我们必须给出学号不存在的时候的提示
		//定义一个索引 
//index等于-1时，表示删除的学号不存在，需要重新选择操作
		int index = -1;
		
		//遍历集合
		for(int x=0; x<list.size(); x++) {
			//获取到每一个学生对象
			Student s = list.get(x);
			//拿这个学生对象的学号和键盘录入的学号进行比较
			if(s.getId().equals(id)) {
				index = x;
				break;
			}
		}
		
		if(index == -1) {
			System.out.println("不好意思,你要删除的学号对应的学生信息不存在,请回去重新你的选择");
		}else {
              /*
                 这里的index表示学号存在时，学号所对应学生对象在集合中的下标
                 所以这里根据下标index直接删除即可
*/
			list.remove(index);
			System.out.println("删除学生成功");
		}
	}
}
```

### **2.2.6**学生管理系统之修改学生功能

修改学生的思路：键盘录入一个学号，到集合中去查找，看是否有学生使用的是该学号，如果有就修改该学生。

**注意:在修改之前，我们需要判断该学号是否存在。**

**补充：可以借助一个变量index来判断学号是否存在：**

**index=-1，表示集合中不存在该学号，重新选择；**

**index !=-1，表示该学号存在，则将学号所属对象所在的集合中的索引赋值给index。然后提示用户输入修改的******新姓名、年龄、住址。然后保存将id一同保存到新创建的学生对象中，最后使用集合中的[set](#set(int, E))(int index, [E](mk:@MSITStore:F:\itcast\开发资料\基础班\API\JDK_API_1_6_zh_CN.CHM::/java/util/../../java/util/ArrayList.html) element)方法修改对象。**

```java
package com.itheima;

import java.util.ArrayList;
import java.util.Scanner;

/*
 * 这是我的学生管理系统的主类
 * 
 * 步骤如下：
 * A:定义学生类
 * B:学生管理系统的主界面的代码编写
 * C:学生管理系统的查看所有学生的代码编写
 * D:学生管理系统的添加学生的代码编写
 * E:学生管理系统的删除学生的代码编写
 * F:学生管理系统的修改学生的代码编写
 */
public class StudentManagerTest {
	public static void main(String[] args) {
		//创建集合对象，用于存储学生数据
		ArrayList<Student> list= new ArrayList<Student>();
		
		//为了让程序能够回到这里来，我们使用循环
		while(true) {
			//这是学生管理系统的主界面
			System.out.println("--------欢迎来到学生管理系统--------");
			System.out.println("1 查看所有学生");
			System.out.println("2 添加学生");
			System.out.println("3 删除学生");
			System.out.println("4 修改学生");
			System.out.println("5 退出");
			System.out.println("请输入你的选择：");
			//创建键盘录入对象
			Scanner sc = new Scanner(System.in);
			String choiceString = sc.nextLine();
			//用switch语句实现选择
			switch(choiceString) {
			case "1":
				//查看所有学生
//findAllStudent(list);
				break;
			case "2":
				//添加学生
//addStudent(list);
				break;
			case "3":
				//删除学生
//deleteStudent(list);
				break;
			case "4":
				//修改学生
				updateStudent(list);
				break;
			case "5":
				//退出
				//System.out.println("谢谢你的使用");
				//break;
			default:
				System.out.println("谢谢你的使用");
				System.exit(0); //JVM退出
				break;
			}
		}
	}
	
	//修改学生
	public static void updateStudent(ArrayList<Student> list) {
		//修改学生的思路：键盘录入一个学号，到集合中去查找，看是否有学生使用的是该学号，如果有就修改该学生
		//创建键盘录入对象
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入你要修改的学生的学号：");
		String id = sc.nextLine();
		
		//定义一个索引
		int index = -1;
		
		//遍历集合
		for(int x=0; x<list.size(); x++) {
			//获取每一个学生对象
			Student s = list.get(x);
			//拿学生对象的学号和键盘录入的学号进行比较
			if(s.getId().equals(id)) {
				index = x;
				break;
			}
		}
		
		if(index == -1) {
			System.out.println("不好意思,你要修改的学号对应的学生信息不存在,请回去重新你的选择");
		}else {
			System.out.println("请输入学生新姓名：");
			String name = sc.nextLine();
			System.out.println("请输入学生新年龄：");
			String age = sc.nextLine();
			System.out.println("请输入学生新居住地：");
			String address = sc.nextLine();
			
			//创建学生对象
			Student s = new Student();
			s.setId(id);
			s.setName(name);
			s.setAge(age);
			s.setAddress(address);
			
			//修改集合中的学生对象
			list.set(index, s);
			
			//给出提示
			System.out.println("修改学生成功");
		}
	}
}
```

