# day03【 选择语句、循环语句、随机数】

## 今日内容

- switch选择语句
- for循环语句
- while循环语句
- do while循环语句
- 跳出语句break，continue
- 循环嵌套
- 随机数字

## 教学目标

- [ ] 能够使用switch语句完成根据月份输出对应季节
- [ ] 能够使用for循环完成一个范围的数据求和
- [ ] 能够使用for循环完成统计水仙花个数
- [ ] 能够使用while循环完成珠穆朗玛峰案例
- [ ] 能够知道三种循环的区别
- [ ] 能够知道循环嵌套的执行流程
- [ ] 能够知道break和continue的作用
- [ ] 能够完成猜数字小游戏程序


# 第一章 选择语句

## 1.1 选择语句--switch

- **switch语句格式：**


```java
switch(表达式) {
  case 常量值1:
    语句体1;
    break;
  case 常量值2:
    语句体2;
    break;
  ...
  default:
    语句体n+1;
    break;
}
```
- **执行流程**
  - 首先计算出表达式的值
  - 其次，和case依次比较，一旦有对应的值，就会执行相应的语句，在执行的过程中，遇到break就会结束。
  - 最后，如果所有的case都和表达式的值不匹配，就会执行default语句体部分，然后程序结束掉。

![](img/switch.jpg)

要求这个表达式最后必须能计算出一个准确的结果，并且这个结果的类型只能是 byte short int char  enum（枚举）， 在JDK7以后增加了字符串类型。

break的作用是结束switch语句，跳出switch语句。

- switch语句练习-春夏秋冬

  - 需求：一年有12个月，分属于春夏秋冬4个季节，键盘录入一个月份，请用程序实现判断该月份属于哪个季节，并输出。

  - 演示效果

    输入： 1、2、12	输出：冬季

    输入： 3、4、5	输出：春季

    输入： 6、7、8	输出：夏季

    输入： 9、10、11	输出：秋季

    输入：其它数字	输出：数字有误

    ```java
    public static void main(String[] args) {
        //定义月份变量，判断季节
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入月份：");
        int month = sc.nextInt();//6
       
        //switch语句实现选择
        switch(month) {
            case 1:
                System.out.println("冬季");
                break;
            case 2:
                System.out.println("冬季");
                break;
            case 3:
                System.out.println("春季");
                break;
            case 4:
                System.out.println("春季");
                break;
            case 5:
                System.out.println("春季");
                break;
            case 6:
                System.out.println("夏季");
                break;
            case 7:
                System.out.println("夏季");
                break;
            case 8:
                System.out.println("夏季");
                break;
            case 9:
                System.out.println("秋季");
                break;
            case 10:
                System.out.println("秋季");
                break;
            case 11:
                System.out.println("秋季");
                break;
            case 12:
                System.out.println("冬季");
                break;
            default:
                System.out.println("你输入的月份数字有误");
                break;
        }
    }
    ```



## 1.2 case的穿透性

在switch语句中，如果case的后面不写break，将出现穿透现象，也就是不会在判断下一个case的值，直接向后运行，直到遇到break，或者整体switch结束。

```java
public static void main(String[] args) {
    //定义月份变量，判断季节
    Scanner sc = new Scanner(System.in);
    System.out.println("请输入月份：");
    int month = sc.nextInt();//3
    //switch语句实现选择
    switch(month) {
        case 12:
        case 1:
        case 2:
            System.out.println("冬季");
            break;
        case 3:
        case 4:
        case 5:
            System.out.println("春季");
            break;
        case 6:
        case 7:
        case 8:
            System.out.println("夏季");
            break;
        case 9:
        case 10:
        case 11:
            System.out.println("秋季");
            break;
        default:
            System.out.println("你输入的月份数字有误");
            break;
    }
}
```

上述程序中，执行case3后，由于没有break语句，程序会一直向后走，不会在判断case，直接向下运行，直到遇到break关键字，才会结束switch语句。



# 第二章 循环语句

## 2.1 循环概述

在生活中有时我们做某些事情，需要重复往复性的做好多次，根据具体的情况，最后才能决定是否还需要继续做这件事。

我们要想把生活中的这些重复性的动作在Java中体现出来，这时就需要使用Java提供的循环。

循环语句可以在满足循环条件的情况下，反复执行某一段代码，这段被重复执行的代码被称为循环体语句，当反复执行这个循环体时，需要在合适的时候把循环判断条件修改为false，从而结束循环，否则循环将一直执行下去，形成死循环。

Java中提供的循环有三种：

for循环、while循环、do-while循环。

## 2.2 循环组成

循环的组成(手写100遍HelloWorld案例):
(1)【初始化表达式1】准备工作:笔墨伺候,最优先唯一执行一次的操作
(2)【布尔表达式2】条件判断:每次书写前,判断一下,要不要写
(3)【循环体语句3】循环所要进行的操作:手写一个HelloWorld案例
(4)【修改布尔表达式4】扫尾的工作:每写一次HelloWorld,计数(+1)



## 2.3 循环语句1--for

- **for循环语句格式：**


```java
for(初始化表达式1; 布尔表达式2; 修改布尔表达式4){
		循环体语句3
}
```

1. 初始化表达式1：就是对循环变量进行初始化（**循环变量**就是控制循环次数的变量）
2. 布尔表达式2：就是判断是否要进行循环执行（就是布尔表达式）
3. 循环体语句3：就是循环执行的代码
4. 修改布尔表达式4：也叫条件控制语句，每次循环体执行后就对循环变量进行改变值



- **执行流程**
  - 执行顺序：①②③④>②③④>②③④…②不满足为止。
  - ①负责完成循环变量初始化
  - ②负责判断是否满足循环条件，不满足则跳出循环
  - ③具体执行的语句
  - ④循环后，循环条件所涉及变量的变化情况

![](img/for.jpg)

```java
public static void main(String[] args) {
    //控制台输出10次HelloWorld，不使用循环
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("HelloWorld");
    System.out.println("-------------------------");

    //用循环改进，循环10次
    //定义变量从0开始，循环条件为<10
    for(int x = 0; x < 10; x++) {
      	System.out.println("HelloWorld"+x);
    }
}
```

* for循环练习1：在控制台输出1-5和5-1的数据

```java
public static void main(String[] args) {
    //需求：输出数据1-5
    for(int i=1; i<=5; i++) {
    	System.out.println(i);
    }
    System.out.println("--------");
    //需求：输出数据5-1
    for(int i=5; i>=1; i--) {
   		System.out.println(i);
    }
}
```

* for循环练习2：求1-5之间的数据和，并把求和结果在控制台输出

```java
public static void main(String[] args) {
    //求和的最终结果必须保存起来，需要定义一个变量，用于保存求和的结果，初始值为0
    int sum = 0;
    //从1开始到5结束的数据，使用循环结构完成
    /*
        sum += i; sum = sum + i;
        第一次：sum = sum + i = 0 + 1 = 1;
        第二次：sum = sum + i = 1 + 2 = 3;
        第三次：sum = sum + i = 3 + 3 = 6;
        第四次：sum = sum + i = 6 + 4 = 10;
        第五次：sum = sum + i = 10 + 5 = 15;
        */
    for(int i=1; i<=5; i++) {
        //将反复进行的事情写入循环结构内部
        // 此处反复进行的事情是将数据 i 加到用于保存最终求和的变量 sum 中
        sum += i;        
    }
}

```

- 本题要点
  - 今后遇到的需求中，如果带有求和二字，请立即联想到求和变量
  - 求和变量的定义位置，必须在循环外部，如果在循环内部则计算出的数据将是错误的



- for循环练习3：求1-100之间的偶数和，并把求和结果在控制台输出

```java
public static void main(String[] args) {
    //求和的最终结果必须保存起来，需要定义一个变量，用于保存求和的结果，初始值为0
    int sum = 0;
    //对1-100的数据求和与1-5的数据求和几乎完全一样，仅仅是结束条件不同
    for(int i=1; i<=100; i++) {
        //对1-100的偶数求和，需要对求和操作添加限制条件，判断是否是偶数
        if(i%2 == 0) {
        	sum += i;
        }
    }
    //当循环执行完毕时，将最终数据打印出来
    System.out.println("1-100之间的偶数和是：" + sum);
}
```





 

 		A:三位数其实就告诉了我们水仙花数的范围

 			100-999

 		B:如何获取一个数据的每一个位上的数呢?

 			举例：我有一个数据153，请问如何获取到个位，十位，百位

 			个位：153%10 = 3;

 			十位：153/10%10 = 5;

 			百位：153/10/10%10 = 1;

 			

 		C:让每个位上的立方和相加，并和该数据进行比较，如果相等，就说明该数据是水仙花数，在控制台输出

- for循环练习4：在控制台输出所有的“水仙花数”
  - 解释：什么是水仙花数？
    - 水仙花数，指的是一个三位数，百位、十位、个位的数字立方和等于原数
    - 例如 `153 1*1*1 + 5*5*5 + 3*3*3  = 153`

  - 步骤：

    - 三位数其实就告诉了我们水仙花数的范围   100-999

    - 如何获取一个数据的每一个位上的数呢?

      举例：我有一个数据153，请问如何获取到个位，十位，百位

       			个位：153%10 = 3;

       			十位：153/10%10 = 5;

       			百位：153/10/10%10 = 1;

    - 让每个位上的立方和相加，并和该数据进行比较，如果相等，就说明该数据是水仙花数，在控制台输出

      

```java
/*
 * 需求：在控制台输出所有的”水仙花数”
 * 
 * 分析：
 * 		什么是水仙花数呢?
 * 			所谓的水仙花数是指一个三位数，其各位数字的立方和等于该数本身。
 *			举例：153就是一个水仙花数。
 *			153 = 1*1*1 + 5*5*5 + 3*3*3
 *
 *		A:三位数其实就告诉了我们水仙花数的范围
 *			100-999
 *		B:如何获取一个数据的每一个位上的数呢?
 *			举例：我有一个数据153，请问如何获取到个位，十位，百位
 *			个位：153%10 = 3;
 *			十位：153/10%10 = 5;
 *			百位：153/10/10%10 = 1;
 *			千位：...
 *			万位：...
 *		C:让每个位上的立方和相加，并和该数据进行比较，如果相等，就说明该数据是水仙花数，在控制台输出
 */
public class ForTest4 {
	public static void main(String[] args) {
		//通过循环获取到每一个三位数
		for(int x=100; x<1000; x++) {
			//获取个位，十位，百位
			int ge = x%10;
			int shi = x/10%10;
			int bai = x/10/10%10;
			
			//让每个位上的立方和相加，并和该数据进行比较，如果相等，就说明该数据是水仙花数，在控制台输出
			if((ge*ge*ge+shi*shi*shi+bai*bai*bai) == x) {
				System.out.println(x);
			}
		}
```



- for循环练习5：统计三位数的“水仙花数”一共有多少个，并在控制台输出个数

```java
public static void main(String[] args) {
    //定义变量count，用于保存“水仙花数”的数量，初始值为0
    int count = 0;
    //输出所有的水仙花数必然要使用到循环，遍历所有的三位数，三位数从100开始，到999结束
    for(int i=100; i<1000; i++) {
        //在计算之前获取三位数中每个位上的值
        int ge = i%10;
        int shi = i/10%10;
        int bai = i/10/10%10;
        //在判定水仙花数的过程中，满足条件不再输出，更改为修改count的值，使count+1
        if(ge*ge*ge + shi*shi*shi + bai*bai*bai == i) {
        	count++;
        }
    }
    //打印输出最终结果
    System.out.println("水仙花共有：" + count + "个");
}
```

- 本题要点：
  - 今后如果需求带有统计xxx，请先想到计数器变量
  - 计数器变量定义的位置，必须在循环外部

## 2.4 循环语句2--while

- **while循环语句格式：**


```java
初始化表达式1
  while(布尔表达式2){
    循环体3
    修改布尔表达式4
}
```

- **执行流程**
  - 执行顺序：①②③④>②③④>②③④…②不满足为止。
  - ①负责完成循环变量初始化。
  - ②负责判断是否满足循环条件，不满足则跳出循环。
  - ③具体执行的语句。
  - ④循环后，循环变量的变化情况。

![](img/while.jpg)

- while循环练习1：在控制台输出10次HelloWorld


```java
public static void main(String[] args) {
    //for循环实现打印10次HelloWorld
    for(int i=1; i<=10; i++) {
    	System.out.println("HelloWorld");
    }
    //while循环实现打印10次HelloWorld
    //定义初始化变量
    int i = 1;
    //循环条件<=10
    while(i<=10){
        System.out.println("HelloWorld");
        //步进
        i++;
    }
}
```



- while循环练习2：珠穆朗玛峰
  - 需求：世界最高山峰是珠穆朗玛峰(8844.43米=8844430毫米)，假如我有一张足够大的纸，它的厚度是0.1毫米。请问，我折叠多少次，可以折成珠穆朗玛峰的高度?
  - 思路：
    1. 定义计数器变量，准备用于统计次数
    2. 定义纸张的厚度，和珠穆朗玛峰的高度，注意单位换算
    3. 编写while循环的判断条件，当纸张厚度小于等于珠穆朗玛峰的高度，说明循环可以继续，循环内部纸张*=2
    4. 循环中每一次折完，计数器增长一次，循环结束后打印计数器

```java
 public static void main(String[] args) {
		//定义一个计数器，初始值为0
		int count = 0;		
		//定义纸张厚度
		double paper = 0.1;		
		//定义珠穆朗玛峰的高度
		int zf = 8844430;		
		//因为要反复折叠，所以要使用循环，但是不知道折叠多少次，这种情况下更适合使用while循环
		//折叠的过程中当纸张厚度大于珠峰就停止了，因此继续执行的要求是纸张厚度小于等于珠峰高度
		while(paper <= zf) {
			//循环的执行过程中每次纸张折叠，纸张的厚度要加倍
			paper *= 2;			
			//在循环中执行累加，对应折叠了多少次
			count++;
		}		
		//打印计数器的值
		System.out.println("需要折叠：" + count + "次");
 }
```

## 2.5 循环语句3--do...while

- **do...while循环格式**


```java
初始化表达式①
    do{
    循环体③
    修改布尔表达式④
}while(布尔表达式②);
```

- **执行流程**
  - 执行顺序：①③④>②③④>②③④…②不满足为止。
  - ①负责完成循环变量初始化。
  - ②负责判断是否满足循环条件，不满足则跳出循环。
  - ③具体执行的语句
  - ④循环后，循环变量的变化情况

![](img/dowhile.jpg)



- do-while循环练习1：在控制台输出10次HelloWorld


```java
public static void main(String[] args) {
    int x=1;
    do {
      System.out.println("HelloWorld");
      x++;
    }while(x<=10);
}
```

do...while循环的特点：无条件执行一次循环体，即使我们将循环条件直接写成false，也依然会循环一次。这样的循环具有一定的风险性，因此初学者不建议使用do...while循环。

```java
public static void main(String[] args){
    do{
      	System.out.println("无条件执行一次");
    }while(false);
}
```

## 2.6 循环语句的区别

- 三种循环的区别
  - for循环和while循环先判断条件是否成立，然后决定是否执行循环体（先判断后执行）
  - do...while循环先执行一次循环体，然后判断条件是否成立，是否继续执行循环体（先执行后判断）

- for循环和while的区别
   - 控制条件语句所控制的那个变量，在for循环结束后，就不能再被访问到了，而while循环结束还可以继续使用，如果你想继续使用，就用while，否则推荐使用for。原因是for循环结束，该变量就从内存中消失，能够提高内存的使用效率。

   - 条件控制语句所控制的自增变量，因为归属for循环的语法结构中，在for循环结束后，就不能再次被访问到了

   - 条件控制语句所控制的自增变量，对于while循环来说不归属其语法结构中，在while循环结束后，该变量还可以继续使用

     代码如下所示：

   ```java
   public class Demo2 {
   	public static void main(String[] args) {
   		
   		for(int x=1; x<=5; x++){
   			System.out.println("爱生活，爱Java");
   		}
   		//这里的x无法继续访问
   		//System.out.println(x);
   		System.out.println("-----------------");
   		
   		int y = 1;
   		while(y<=10) {
   			System.out.println("爱生活，爱Java");
   			y++;
   		}
   		System.out.println(y);
   	}
   }
   ```

- 三种循环的区别总结

  1.建议使用的顺序:for,while,do-while
  2.循环次数确定的话,建议使用for,循环次数不确定建议使用while
  3.do-while循环来讲的话,至少执行一次
  4.while和do-while循环而言,循环结束后,初始化条件中定义的变量可以继续使用,但是for循环的不能使用(在for循环内部定义初始化语句)

## 2.7  跳出语句

### break

- **使用场景：终止switch或者循环**

  break：它主要是在程序中跳出当前正在执行的代码。

  break，它主要用在switch的case中，或者用在循环中。

  当用在switch中的时候，在程序执行switch中的代码时候，遇到break，会导致当前这个switch代码彻底结束，而去执行和switch结构上并列的语句。

  当break使用在循环中的时候，只要JVM遇见break，就立刻让当前循环结束，不管循环条件是否还成立，循环都会强制结束。

  案例代码如下所示：

```java
public static void main(String[] args) {
    for (int i = 1; i<=10; i++) {
        //需求:打印完两次HelloWorld之后结束循环
        if(i == 3){
          break;
        }
        System.out.println("HelloWorld"+i);
    }
}
```

### continue

- continue（继续）：它主要用在循环中，不能使用在其他地方。（跳过本次循环，执行本循环的下一次的循环）

  continue：它的执行原理：当在循环中遇到的continue，这时JVM 就不会再执行continue下面属于本循环的其他语句，而直接进入本循环的下次循环。

  案例代码如下所示：

```java
public static void main(String[] args) {
    for (int i = 1; i <= 10; i++) {
        //需求:不打印第三次HelloWorld
        if(i == 3){
          continue;
        }
        System.out.println("HelloWorld"+i);
    }
}
```



# 第三章 循环扩展知识点

## 3.1 死循环

- **死循环：**也就是循环中的条件永远为true，死循环的是永不结束的循环。例如：while(true){}。

在后期的开发中，会出现使用死循环的场景，例如：我们需要读取用户输入的数据，但是用户输入多少数据我们并不清楚，也只能使用死循环，当用户不想输入数据了，就可以结束循环了，如何去结束一个死循环呢，就需要使用到跳出语句了。

- 死循环（无限循环）的三种格式
  - while的格式：

    ```java
    while( true )
    {
    	循环体;
    }
    ```

  - for的格式：

    ```java
    for(  ; 默认是true ; )
    {
    	循环体;
    }
    ```

    

  - do-while格式：

    ```java
    do {
        循环体;
    } while(true);
    ```

    注意：

    ​	1）只要使用无限循环，那么在循环的下面不要再写任何的语句。

    ​	**2）开发中如果使用到死循环，优先考虑while循环。**

    

## 3.2 嵌套循环

- **所谓嵌套循环**，是指一个循环的循环体是另一个循环。比如for循环里面还有一个for循环，就是嵌套循环。


- **嵌套循环格式：**	

```java
for(初始化表达式①; 循环条件②; 步进表达式⑦) {
    for(初始化表达式③; 循环条件④; 步进表达式⑥) {
      	执行语句⑤;
    }
}
```

- **嵌套循环执行流程：**
  - 执行顺序：①②③④⑤⑥>④⑤⑥>⑦②③④⑤⑥>④⑤⑥

  - 外循环一次，内循环多次（一圈）。

  - 总共的循环次数=外循环次数*内循环次数

  - 例如：日历中 年与月的关系，时钟中 分与秒的关系

    - 如 2021年至2023年，一共3年，每年12个月。其中，年份看成外循环，月份看成内循环。

    > 看系统日历 时钟
- **练习**：使用嵌套循环，打印2021年至2023年月份，格式：xxxx年x月

```java
public static void main(String[] args) {
    //打印2021年至2023年月份
    //年份是外循环，3年；月份是内循环，12月
    for (int i = 2021; i <= 2023; i++) {
        for (int j = 1; j <= 12; j++) {
            System.out.print(i + "年" + j + "月 ");
        }
        //内循环打印12个月后，需要一次换行
        System.out.println();
    }
}
```

# 第四章 随机数

## 4.1 什么是Random类

我们想产生1~100(包含1和100)的随机数该怎么办呢? 

Java已经为我们提供好了产生随机数的类---Random:

此类的实例用于生成随机数。

例如，以下代码使用户能够得到一个随机数：

```java
Random r = new Random();
int i = r.nextInt();//在整数范围内的任意随机数
```

## 4.2 Random产生随机数（掌握）

- 概述：

  - Random类似Scanner，也是Java提供好的API，内部提供了产生随机数的功能
  - API后续课程详细讲解，现在可以简单理解为Java已经写好的代码，我们可以直接使用

- 使用步骤：

  1. 导入包

     import java.util.Random;

  2. 创建对象

     Random r = new Random();

  3. 产生随机数

     int num = r.nextInt(10);

     解释：

      • 产生的数据在0到10之间，包括0，不包括10。产生的随机数就是0(包括)-9(包括).

     • 括号里面的10是可以变化的，如果是100，就是0-100之间的数据，包括0，不包括100.

- 使用Random类，完成生成3个10以内的随机整数的操作，代码如下：

  ```java
  //1. 导包
  import java.util.Random;
  public class Demo01_Random {
    	public static void main(String[] args) {
          //2. 创建键盘录入数据的对象
          Random r = new Random();
  
          for(int i = 0; i < 3; i++){
              //3. 随机生成一个数据
              int number = r.nextInt(10);
              //4. 输出数据
              System.out.println("number:"+ number);
          }		
      }
  }
  ```

## 4.3 练习

### 获取随机数

获取1-n之间的随机数，包含n，代码如下：

```java
// 导包
import java.util.Random;

public class Test01Random {
    public static void main(String[] args) {
        int n = 100; 
        // 创建对象
        Random r = new Random();
        // 获取随机数
        int number = r.nextInt(n) + 1;
        // 输出随机数
        System.out.println("number:" + number);
    }
}
```

### Random练习-猜数字

- 需求：猜数字小游戏案例，系统产生一个1-100之间的随机数，请猜出这个数据是多少。

- 效果：

  - 如果猜的数字比真实数字大，提示你猜的数据大了
  - 如果猜的数字比真实数字小，提示你猜的数据小了
  - 如果猜的数字与真实数字相等，提示恭喜你猜中了


- 分析：

    A:系统产生一个随机数1-100之间的。

   	int number = r.nextInt(100) + 1;

   B:键盘录入我们要猜的数据

   	用Scanner实现

   C:比较这两个数据(用if语句)

   	大了：给出提示大了

   	小了：给出提示小了

   	猜中了：给出提示，恭喜你，猜中了

   D:多次猜数据，而我们不知道要猜多少次，怎么办呢?

   	while(true) {循环的内容}

- 代码实现

  ```java
  package com.itheima;
  import java.util.Random;
  import java.util.Scanner;
  /*
   * 猜数字小游戏案例
   *		系统产生一个1-100之间的随机数，请猜出这个数据是多少。
   * 分析：
   * 		A:系统产生一个随机数1-100之间的。
   * 			int number = r.nextInt(100) + 1;
   * 		B:键盘录入我们要猜的数据
   * 			用Scanner实现
   *		C:比较这两个数据(用if语句)
   *			大了：给出提示大了
   *			小了：给出提示小了
   *			猜中了：给出提示，恭喜你，猜中了
   *		D:多次猜数据，而我们不知道要猜多少次，怎么办呢?
   *			while(true) {循环的内容}
   */
  public class RandomTest {
  	public static void main(String[] args) {
  		// 系统产生一个随机数1-100之间的。
  		Random r = new Random();
  		int number = r.nextInt(100) + 1;
           //System.out.println(number);
  
  		while(true){
  			// 键盘录入我们要猜的数据
  			Scanner sc = new Scanner(System.in);
  			System.out.println("请输入你要猜的数字(1-100)：");
  			int guessNumber = sc.nextInt();
  	
  			// 比较这两个数据(用if语句)
  			if (guessNumber > number) {
  				System.out.println("你猜的数据" + guessNumber + "大了");
  			} else if (guessNumber < number) {
  				System.out.println("你猜的数据" + guessNumber + "小了");
  			} else {
  				System.out.println("恭喜你,猜中了");
  				break;
  			}
  		}
  	}
  }
  ```

