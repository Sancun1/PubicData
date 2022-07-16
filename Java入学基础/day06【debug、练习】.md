# day06【debug、方法参数传递、练习】

## 今日内容

- debug调试
- 选择语句练习
- 循环语句练习
- 数组练习
- 方法练习

## 教学目标

- [ ] 能够使用断点调试查看循环求和流程
- [ ] 能够知道方法的参数是基本类型和引用类型的区别
- [ ] 能够完成减肥计划案例
- [ ] 能够完成逢七必过案例
- [ ] 能够完成不死神兔案例
- [ ] 能够完成百钱百鸡案例
- [ ] 能够完成数组中的元素查找
- [ ] 能够完成数组中的元素反转
- [ ] 能够完成评委打分案例

# 第一章 Debug调试

### 1.1 什么是Debug模式

Idea的断点调试可以查看程序的执行流程和解决程序中的bug。

我们在运行程序的过程中，经常需要看程序运行过程中某些变量，容器等里面数据的具体的结果，或者是数据的变化情况。而我们之前都是通过输出语句System.out.println()来查看的，这样虽然可以实现结果，但是比较麻烦。我们可以使用更简单的方法来实现，就是可以使用编辑器Idea提供的程序调试工具。



1. 要想看程序流程，就必须设置断点。在需要查看的代码的前面即行号右边的空白区域单击左键设置断点。

   什么是断点：就是一个标记，程序从哪里开始debug调试开始。

        在哪里设置断点：

   ​			哪里不会点哪里。

   ​			目前：我们就在每个方法的第一条有效语句上都加。

   设置完断点之后，程序执行到断点处将停止，我们可以手动来运行程序。



![01](/img/01.png) 

- 如何运行加了断点的程序

  - 在代码区域右键Debug执行

  ![02](/img/02.png)

- 看哪里

  - 看Debugger窗口

  ![03](/img/03.png)

  - 看Console窗口

  ![04](/img/04.png)

- 点哪里

  - 点Step Into (F7)这个箭头，也可以直接按F7

  ![05](/img/05.png)

- Debug调试窗口介绍

  ![](img/debug5.png)

- 如何删除断点

  - 选择要删除的断点，单击鼠标左键即可

  ![06](/img/06.png)

  - 如果是多个断点，可以每一个再点击一次。也可以一次性全部删除

  ![07](/img/07.png)



# 第二章 方法的参数传递

## 2.1 参数传递的概念

- 可以理解当我们要调用一个方法时，我们会把指定的数值，传递给方法中的参数，这样方法中的参数就拥有了这个指定的值，可以使用该值，在方法中运算了。这种传递方式，我们称为参数传递。
- 在这里，定义方法时，参数列表中的变量，我们称为形式参数
- 调用方法时，传入给方法的数值，我们称为实际参数

## 2.2 基本数据类型作为方法参数

```java
public class Demo01Args {
	public staticvoid main(String[] args) {
		// 定义变量
		int a = 10;
		int b = 20;
		System.out.println("a:" + a + ",b:" + b);// a:10,b:20
		change(a, b);
		System.out.println("a:" + a + ",b:" + b);// a:10,b:20
	}

	public static void change(inta, intb) { // a=10,b=20
		System.out.println("a:" + a + ",b:" + b);// a:10,b:20
		a *= 10; // a=100;
		b *= 10;// b=200;
		System.out.println("a:" + a + ",b:" + b);// a:100,b:200
	}
}
```

注意：形式参数的改变不影响实际参数

## 2.3 基本数据类型作为方法参数调用图解

![](img/基本数据类型作为方法参数调用图解.png)

## 2.4 引用数据类型作为方法参数

```java
public class Demo02Args {
	public static void main(String[] args) {
		// 定义数组
		int[] arr = {10, 20};
		System.out.println(arr[0]);
        System.out.println(arr[1]);
		System.out.println("----------------");
		change(arr);
		System.out.println(arr[0]);
        System.out.println(arr[1]);
	}

	public static void change(int[] arr) {
		arr[0] = arr[0]*10;
        arr[1] = arr[1]*10;
	}
}
```

注意：引用类型，作为方法参数，形式参数的改变会影响实际参数

## 2.5 引用数据类型作为方法参数调用图解

![](img/引用类型作为方法参数传递.jpg)

# 第三章 基础练习

### 3.1 减肥计划if版本

- 案例需求

	输入星期数，显示今天的减肥活动
          周一：跑步
          周二：游泳
          周三：慢走
          周四：动感单车
          周五：拳击 
          周六：爬山
          周日：好好吃一顿

- 思路

  1:键盘录入一个星期数，用一个变量接收
  2:对星期数进行判断，这里用 if 语句实现
  3:在对应的语句控制中输出对应的减肥活动

- 代码实现

```java
public class Test01 {
    public static void main(String[] args) {
        //键盘录入一个星期数，用一个变量接收
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入一个星期数：");
        int week = sc.nextInt();

        //对星期数进行判断，这里用 if 语句实现
        if (week < 1 || week > 7) {
            System.out.println("你输入的星期数有误");
        } else if (week == 1) {
            System.out.println("跑步");
        } else if (week == 2) {
            System.out.println("游泳");
        } else if (week == 3) {
            System.out.println("慢走");
        } else if (week == 4) {
            System.out.println("动感单车");
        } else if (week == 5) {
            System.out.println("拳击");
        } else if (week == 6) {
            System.out.println("爬山");
        } else {
            System.out.println("好好吃一顿");
        }
    }
}
```

### 3.2 减肥计划switch版本

- 案例需求

	输入星期数，显示今天的减肥活动
          周一：跑步
          周二：游泳
          周三：慢走
          周四：动感单车
          周五：拳击 
          周六：爬山
          周日：好好吃一顿

- 思路

   1:键盘录入一个星期数，用一个变量接收
   2:对星期数进行判断，这里用 switch 语句实现
   3:在对应的语句控制中输出对应的减肥活动

- 代码实现

```java
public class Test02 {
    public static void main(String[] args) {
        //键盘录入一个星期数，用一个变量接收
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入一个星期数：");
        int week = sc.nextInt();

        //对星期数进行判断，这里用 switch 语句实现
        switch (week) {
            case 1:
                System.out.println("跑步");
                break;
            case 2:
                System.out.println("游泳");
                break;
            case 3:
                System.out.println("慢走");
                break;
            case 4:
                System.out.println("动感单车");
                break;
            case 5:
                System.out.println("拳击");
                break;
            case 6:
                System.out.println("爬山");
                break;
            case 7:
                System.out.println("好好吃一顿");
                break;
            default:
                System.out.println("你输入的星期数有误");
        }
    }
}
```

### 3.3 打印5位数中所有的回文数

- 案例需求

  打印5位数中的所有回文数。

    什么是回文数呢?举例：12321是回文数，个位与万位相同，十位与千位相同。

  **说明：回文数不一定是只有5位数，只要满足将某位数的各位数字反向排列所得自然数与之前的数字比较相等就是回文数。例如：1234321。**

    

    分析：

    		A:5位数告诉了我们数据的范围，用for循环实现提供五位数的所有数字。

    		B:获取每一个5位数，然后得到它的个位，十位，千位，万位

    			假设x是一个5位数：

    				个位：x%10

    				十位：x/10%10

   				千位：x/10/10/10%10

    				万位：x/10/10/10/10%10

    		C:把满足条件的数据输出即可

- 代码实现

```java
package com.itheima;
/*
 * 需求：打印5位数中的所有回文数。
 * 		什么是回文数呢?举例：12321是回文数，个位与万位相同，十位与千位相同。
 * 
 * 分析：
 * 		A:5位数告诉了我们数据的范围，用for循环实现
 * 		B:获取每一个5位数，然后得到它的个位，十位，千位，万位
 * 			假设x是一个5位数：
 * 				个位：x%10
 * 				十位：x/10%10
 * 				千位：x/10/10/10%10
 * 				万位：x/10/10/10/10%10
 * 		C:把满足条件的数据输出即可
 */
public class Test3 {
	public static void main(String[] args) {
		//5位数告诉了我们数据的范围，用for循环实现
		for(int x=10000; x<100000; x++) {
			//获取每一个5位数，然后得到它的个位，十位，千位，万位
			int ge = x%10;
			int shi = x/10%10;
			int qian = x/10/10/10%10;
			int wan = x/10/10/10/10%10;
			
			//把满足条件的数据输出即可
			if((ge==wan) && (shi==qian)) {
				System.out.println(x);
			}
		}
	}
}
```

### 3.4 不死神兔

- 案例需求

  不死神兔也叫做斐波那契数列或者叫做黄金分割数列或者叫做兔子数列：

  不死神兔问题：有1对兔子，从出生的第3个月开始，每个月都生1对兔子，假如兔子都不死，问第n个月有几对兔子?

  **需求：我们这里需要知道第二十个月的兔子对数为多少？**

- 思路

  斐波那契数列思想的图解如下图所示：

  ![](img/斐波那契数列.bmp)

  斐波那契数列思想如下所示：

  找规律：

  ​    月份(n)：  1	2	3	4	5	6	7	8	9	10   .....

  兔子对数(f)： 1	1	2	3	5	8	13	21	34	55   .....   

   

  规律：从第三个月开始，每个月的兔子对数是前两个月的兔子对数之和。

    			第一个月和第二个月的兔子对数是1

  f(n) = f(n-1) + f(n-2)(n>=3)

   

  上述规律我们可以使用数组结构来实现：

  分析：

    		int[] arr = new int[20];

    		arr[0] = 1;//表示第一个月 数组索引从0开始

    		arr[1] = 1;//表示第二个月 数组索引从0开始

    		arr[2] = arr[0] + arr[1];

    		arr[3] = arr[1] + arr[2];

    		arr[4] = arr[2] + arr[3];

   		...	

- 代码实现

```java
package com.itheima;
public class Test4 {
	public static void main(String[] args) {
		//为了存储多个月的兔子对数，定义一个数组，用动态初始化完成数组元素的初始化，长度为20
		int[] arr = new int[20];
		
		//因为第1个月，第2个月兔子的对数是已知的，都是1，所以数组的第1个元素，第2个元素值也都是1
		arr[0] = 1;
		arr[1] = 1;
		//用循环实现计算每个月的兔子对数.月份从第三个月开始，下标从2开始
		for(int n=2; n<arr.length; n++) {
			arr[n] = arr[n-2] + arr[n-1];
		}
		//输出数组中最后一个元素的值，就是第20个月的兔子对数
		System.out.println("第二十个月的时候的兔子对数是："+arr[19]);
	}
}
```

### 3.5 数组元素求和

- 案例需求

	有这样的一个数组，元素是{68,27,95,88,171,996,51,210}。求出该数组中满足要求的元素和，
        要求是：求和的元素个位和十位都不能是7，并且只能是偶数

- 思路

  1:定义一个数组，用静态初始化完成数组元素的初始化
  2:定义一个求和变量，初始值是0
  3:遍历数组，获取到数组中的每一个元素
  4:判断该元素是否满足条件，如果满足条件就累加
  5:输出求和变量的值

- 代码实现

```java
public class Test06 {
    public static void main(String[] args) {
        //定义一个数组，用静态初始化完成数组元素的初始化
        int[] arr = {68, 27, 95, 88, 171, 996, 51, 210};

        //定义一个求和变量，初始值是0
        int sum = 0;

        //遍历数组，获取到数组中的每一个元素
        for(int x=0; x<arr.length; x++) {
            //判断该元素是否满足条件，如果满足条件就累加
            if(arr[x]%10!=7 && arr[x]/10%10!=7 && arr[x]%2==0) {
                sum += arr[x];
            }
        }

        //输出求和变量的值
        System.out.println("sum:" + sum);
    }
}
```

### 3.6 判断两个数组是否相同

- 案例需求

	定义一个方法，用于比较两int个数组的内容是否相同

- 思路

  1:定义两个数组，分别使用静态初始化完成数组元素的初始化
  2:定义一个方法，用于比较两个数组的内容是否相同
  3:比较两个数组的内容是否相同，按照下面的步骤实现就可以了
     首先比较数组长度，如果长度不相同，数组内容肯定不相同，返回false
     其次遍历，比较两个数组中的每一个元素，只要有元素不相同，返回false
     最后循环遍历结束后，返回true

  4:调用方法，用变量接收

  5:输出结果

- 代码实现

```java
public class Test07 {
    public static void main(String[] args) {
        //定义两个数组，分别使用静态初始化完成数组元素的初始化
        int[] arr = {11, 22, 33, 44, 55};
        //int[] arr2 = {11, 22, 33, 44, 55};
        int[] arr2 = {11, 22, 33, 44, 5};


        //调用方法，用变量接收
        boolean flag = compare(arr,arr2);
        //输出结果
        System.out.println(flag);
    }

    //定义一个方法，用于比较两个数组的内容是否相同
    /*
        两个明确：
            返回值类型：boolean
            参数：int[] arr, int[] arr2
     */
    public static boolean compare(int[] arr, int[] arr2) {
        //首先比较数组长度，如果长度不相同，数组内容肯定不相同，返回false
        if(arr.length != arr2.length) {
            return false;
        }

        //其次遍历，比较两个数组中的每一个元素，只要有元素不相同，返回false
        for(int x=0; x<arr.length; x++) {
            if(arr[x] != arr2[x]) {
                return false;
            }
        }

        //最后循环遍历结束后，返回true
        return true;
    }
}
```

### 3.7 查找元素在数组中出现的索引位置

- 案例需求

  数组元素查找(查找指定元素第一次在数组中出现的索引).如果没有查找到，则输出-1

   (1)给定数组int[] arr = {5,7,3,2,5};

   (2)要查询的元素通过键盘录入的方式确定

   (3)定义一个查找数组元素第一次出现位置的方法(注,要查找的元素就是键盘录入的数据)

  

- 思路

      A:给定数组int[] arr = {5,7,3,2,5};
      B:要查询的元素通过键盘录入的方式确定
      C:定义一个查找数组元素第一次出现位置的方法
      遍历数组，获取到每一个元素，进行比较，如果想等，就直接把该处的索引返回。
      D:调用方法，输出结果

- 代码实现

  ```java
  package com.itheima;
  import java.util.Scanner;
  /*
   *需求：数组元素查找(查找指定元素第一次在数组中出现的索引)
   *(1)给定数组int[] arr = {5,7,3,2,5};
   *(2)要查询的元素通过键盘录入的方式确定
   *(3)定义一个查找数组元素第一次出现位置的方法(注,要查找的元素就是键盘录入的数据)
   *
   *分析：
   *		A:给定数组int[] arr = {5,7,3,2,5};
   *		B:要查询的元素通过键盘录入的方式确定
   *		C:定义一个查找数组元素第一次出现位置的方法
   *			遍历数组，获取到每一个元素，进行比较，如果想等，就直接把该处的索引返回。
   *		D:调用方法，输出结果
   */
  public class Test8 {
  	public static void main(String[] args) {
  		// 给定数组int[] arr = {5,7,3,2,5};
  		int[] arr = { 5, 7, 3, 2, 5 };
  
  		//要查询的元素通过键盘录入的方式确定
  		Scanner sc = new Scanner(System.in);
  		
  		System.out.println("请输入要查找的元素：");
  		int number = sc.nextInt();
  		
  		//定义一个查找数组元素第一次出现位置的方法
  		//调用方法
  		int index =getIndex(arr, number);
  		System.out.println("index:"+index);
  	}
  	/*
  	 * 两个明确：
  	 * 		返回值类型：int
  	 * 		参数列表：int[] arr,int value
  	 */
  	public static int getIndex(int[] arr,int value) {
  		//遍历数组，获取到每一个元素，进行比较，如果相等，就直接把该处的索引返回。
  		for(int x=0; x<arr.length; x++) {
  			if(arr[x] == value) {
  				return x;
  			}
  		}
  //程序执行到这里，说明数组中没有要找的数据，我们一般返回-1
  		return -1;
  	}
  }
  ```

  

### 3.8 数组元素反转(难点)

- 案例需求

    (1)键盘录入5个int类型的数据存储数组arr中;

    (2)定义方法将arr数组中的内容反转;

    (3)定义方法对反转后的数组进行遍历;

  

- 分析

  ​	A:定义一个长度为5的数组

   	B:通过键盘录入数据给数组中的元素赋值

    	C:定义方法将arr数组中的内容反转

    			什么是反转?如何反转?

    	D:定义方法遍历数组

  说明：什么是反转？如何实现反转？

- 图解

  ![](img/数组反转.bmp)

- 代码实现

  ```java
  package com.itheima;
  import java.util.Scanner;
  
  /*
   * 需求：
   * (1)键盘录入5个int类型的数据存储数组arr中
   * (2)定义方法将arr数组中的内容反转
   * (3)定义方法对反转后的数组进行遍历
   * 
   * 分析：
   * 		A:定义一个长度为5的数组
   * 		B:通过键盘录入数据给数组中的元素赋值
   * 		C:定义方法将arr数组中的内容反转
   * 			什么是反转?如何反转?
   * 		D:定义方法遍历数组
   */
  public class Test7 {
  	public static void main(String[] args) {
  		// 定义一个长度为5的数组
  		int[] arr = new int[5];
  
  		// 通过键盘录入数据给数组中的元素赋值
  		Scanner sc = new Scanner(System.in);
  		for (int x = 0; x < arr.length; x++) {
  			System.out.println("请给出第" + (x + 1) + "个元素");
  			arr[x] = sc.nextInt();
  		}
  		
  		System.out.println("反转前的数组元素：");
  		printArray(arr);
  
  		// 定义方法将arr数组中的内容反转
  		reverse(arr);
  		
  		System.out.println("反转后的数组元素：");
  		//定义方法遍历数组
  		printArray(arr);
  	}
  	// 遍历数组
  	public static void printArray(int[] arr) {
  		for (int x = 0; x < arr.length; x++) {
  				System.out.print(arr[x] + "	");
  		}
  		//换行
  		System.out.println();
  	}
  	
  
  	/*
  	 * 两个明确： 返回值类型：void 参数列表：int[] arr
  	 */
  	public static void reverse(int[] arr) {
  		for(int startIndex=0,endIndex=arr.length-1;startIndex<=endIndex;startIndex++,endIndex--) {
  			int temp = arr[startIndex];
  			arr[startIndex] = arr[endIndex];
  			arr[endIndex] = temp;
  		}
  	}
  }
  ```

  

### 3.9 裁判评分

- 案例需求

  在编程竞赛中，有6个评委为参赛的选手打分，分数为0-100的整数分。选手的最后得分为：去掉一个最高分和一个最低分后 其余4个选手的平均值。

  请写代码实现。(不考虑小数部分)

- 说明

  分数需要使用键盘录入的方式给评委。

- 思路

  ​	A:定义一个长度为6的数组。

    	B:通过键盘录入的方式给出评委的分数

    	C:写方法实现获取数组中的最大值，最小值

    	D:写方法实现数组元素的求和

    	E:平均分： (和-最高分-最低分)/(arr.length-2)

    	F:输出分数即可

- 代码实现

  ```java
  /*
   * 需求：在编程竞赛中，有6个评委为参赛的选手打分，分数为0-100的整数分。
   * 选手的最后得分为：去掉一个最高分和一个最低分后 其余4个选手的平均值。
   * 请写代码实现。(不考虑小数部分)
   * 步骤：
   * A:定义一个长度为6的数组存储评委的分数
   * B:通过键盘录入的方式给评委分数
   * C:书写方法获取数组的最大值 最小值
   * D:书写方法对数组数据求和sum
   * E:求出平均分：(sum-最大值-最小值)/(arr.length-2)
   * F:输出平均分
   */
  public class Demo2 {
  	public static void main(String[] args) {
  		//A:定义一个长度为6的数组存储评委的分数
  		int[] arr=new int[6];
  		//B:通过键盘录入的方式给评委分数
  		Scanner sc = new Scanner(System.in);
  		for (int i = 0; i < arr.length; i++) {
  			System.out.println("请输入第"+(i+1)+"位评委给的分数(0-100)");
  			int number = sc.nextInt();
  			arr[i]=number;
  		}
  		//C:书写方法获取数组的最大值 最小值
  		int max=getMax(arr);//获取最大值
  		int min=getMin(arr);//获取最小值
  		// D:书写方法对数组数据求和sum
  		int sum=getSum(arr);
  		//E:求出平均分：(sum-最大值-最小值)/(arr.length-2)
  		int avg=(sum-max-min)/(arr.length-2);
  		//F:输出平均分
  		System.out.println("该选手的最终得分是："+avg);
  	}
  	public static int getSum(int[] arr) {
  		int sum=0;
  		for (int i = 0; i < arr.length; i++) {
  			sum=sum+arr[i];
  		}
  		return sum;
  	}
  	//求最小值
  	public static int getMin(int[] arr) {
  		int min=arr[0];
  		for (int i = 1; i < arr.length; i++) {
  			if(min>arr[i])
  			{
  				min=arr[i];
  			}
  		}
  		return min;
  	}
  	//获取数组的最大值 
  	public static int getMax(int[] arr) {
  		int max=arr[0];
  		for (int i = 1; i < arr.length; i++) {
  			if(max<arr[i])
  			{
  				max=arr[i];
  			}
  		}
  		return max;
  	}
  }
  ```

