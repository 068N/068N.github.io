# day04 notes

## Scanner

- Scanner:java提供的一个零件，而接收用户输入数据是这个零件的一个小功能
- 共3步

```java
int a = 5;//固定的
int a = ?;//接受用户输入的数据----scanner
int a = ?;//系统随机生成
```

```java
package day04;
import java.util.Scanner;//1.导入扫描仪组件

public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);//2.新建一个扫描仪，叫scan
        System.out.println("请输入年龄：");
        int age = scan.nextInt();//3.扫描了一个整数赋值给age
        System.out.println("请输入商品价格：");
        double price = scan.nextDouble();//3.扫描一个小数赋值给prices

        System.out.println("年龄为：" + age + "，价格为：" + price);
    }
}
```

## 结构

### 分支结构(下)

#### switch ... case

    优点：效率高、结构简单
    缺点：只能对整数进行操作

- 对**整数、只能判断相等**----应用率特别高
- default位置不固定
- 不适用于存在**范围**、**小数**的情况
- if ... else if使用范围更广，但有时不直观

```java
package day04;

public class SwitchCasedDemo {
    public static void main(String[] args) {
        int num = 2;
        switch(num) {//byte, short, int, char, String, 枚举
            case 1://if(num==1)
                System.out.println(111);
                break;
            case 2://以此为入口
                System.out.println(222);
                break;//跳出switch
            case 3:
                System.out.println(333);
                break;
            default://所有case都没配上（eg. num==4)
                System.out.println(666);
        }
    }
}
```

```java
package day04;
import java.util.Scanner;
//命令解析程序
public class CommandBySwitch {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请选择功能：1.存款 2.取款 3.查询余额 4.退卡");
        int command = sc.nextInt();

        switch (command) {
            case 1:
                System.out.println("存款业务...");
                break;
            case 2:
                System.out.println("取款业务...");
                break;
            case 3:
                System.out.println("查询余额业务...");
                break;
            case 4:
                System.out.println("退卡成功");
                break;
            default:
                System.out.println("输入错误");
                break;
        }
    }
}
```

### 循环结构

- while
- do...while
- for

```java
if(boolean) {//判断一次
    语句块 //最多执行一次
}

while(boolean) {//判断多次
    语句块 //执行多次
}
```

- 循环：反复多次执行一段相同或相似的代码
- 例如：
    - 跑3圈
    - 打印4份简历
    - 输出5次“行动是成功的阶梯” 
    - 输出9*9乘法表

### 循环三要素

- 循环变量的初始化
- 循环的条件（以循环变量为基础）
- 循环变量的改变
**（适用于所有循环）**

- 循环变量：在整个循环过程中反复改变的那个数

例：

|跑3圈||||
|---|---|---|---|
| | | |圈数为0|
|够3圈吗？|不够| 跑一圈|圈数为1|
|够3圈吗？|不够|跑一圈|圈数为2|
|够3圈吗？|不够|跑一圈|圈数为3|
|够3圈吗？|够了|||

循环变量：所跑圈数count
1) int count = 0;
2) count <3
3) count++; <br>
   count = 0/1/2/  3时结束

#### while结构

- 执行过程：

先判断boolean的值，若为true则执行语句块，<br>
再判断boolean的值，若为true则再执行语句块，<br>
再判断boolean的值，若为true则再执行语句块，<br>
如此反复，直到boolean的值为false时，while循环结束。<br>

```java
while(boolean) {
    语句块
}
```

```java
package day04;
//while结构的展示
public class WhileDemo {
    public static void main(String[] args) {
        //1）输出5次“行动是成功的阶梯”：
        int times = 0;//1）循环变量的初始化
        while (times < 5) {//2）循环的条件
            System.out.println("行动是成功的阶梯");
            times++;//3）循环变量的改变
        }
        System.out.println("继续执行...");

        //2）输出9的乘法表(1-9)
        int num = 1;//1）循环变量的初始化
        while (num <= 9) {//2）循环的条件
            System.out.println(num + " * 9 = " + 9 * num);
            num++;//3）循环变量的改变
        }
        System.out.println("继续执行...");

        //3）输出9的乘法表(1,3,5,7,9)
        int n = 1;//1）循环变量的初始化
        while (n <= 9) {//2）循环的条件
            System.out.println(n + " * 9 = " + 9 * n);
            n += 2;//3）循环变量的改变
        }
        System.out.println("继续执行...");
    }
}
```

- 猜数字小游戏


    猜数字小游戏
    需求：
    int num = 250;//手里藏的数
    循环变量：用户猜的数guess
    1）System.out.println("猜吧！")
    int guess = scan.nextInt();
    2）guess != num
    3）System.out.println("猜吧！")
    guess = scan.nextInt();
    
    猜吧！
    300
    太大了
    猜吧！
    200
    太小了
    猜吧！
    251
    太大了
    猜吧！
    250
    恭喜你猜对了！

```java
package day04;
//猜数字小游戏
import java.util.Scanner;

public class Guessing {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        int num = 250;//手里藏的数
//        System.out.println("设置手里藏的数：");
//        int num = scan.nextInt();

        System.out.println("猜吧！");
        int guess = scan.nextInt();//1.
        while (guess != num) {//2.
            if (guess > num) {
                System.out.println("太大了");
            } else {
                System.out.println("太小了");
            }
            System.out.println("猜吧！");
            guess = scan.nextInt();//3.
        }
        System.out.println("恭喜你猜对了！");
    }
}
```

#### do ... while结构

```java
do {
    语句块
} while(boolean);
```

- 执行过程：
  - 先执行语句块，在判断boolean的值，若为true则
  - 先执行语句块，在判断boolean的值，若为true则
  - 先执行语句块，在判断boolean的值，若为true则
  - 再执行语句块，如此反复，直到boolean的值为false时，do...while结束


    while：有可能一次都不执行
    do ... while：先执行后判断，至少执行一次
    1、3要素相同用do ... while

变量的作用域/范围
- 从变量的声明开始，到最近的while结束

```java
package day04;
//猜数字小游戏
import java.util.Scanner;

public class Guessing {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        int num = 250;//手里藏的数
//        System.out.println("设置手里藏的数：");
//        int num = scan.nextInt();

        int guess;
        do {//2.
            System.out.println("猜吧！");
            guess = scan.nextInt();//3.
            if (guess > num) {
                System.out.println("太大了");
            } else if (guess < num ) {
                System.out.println("太小了");
            } else {
                System.out.println("恭喜你猜对了！");
            }
        } while (guess != num);
    }
}
```

#### for结构

- 应用率最高
- 和次数有关

```java
for(第一要素、第二要素、第三要素) {
    语句块
}
```

```java
package day04;
//for循环的展示
public class ForDemo {
    public static void main(String[] args) {
//        for (int i = 0; i < 5; i++) {//1,2,3
//            System.out.println("行动是成功的阶梯");
//        }
//        System.out.println("继续执行...");

//        for (int i = 1; i <= 9; i++) {//1,2,3
//            System.out.println(i + " * 9 = " + 9 * i);
//        }

//        for (int i = 9; i >= 1; i--) {//1,2,3
//            System.out.println(i + " * 9 = " + 9 * i);
//        }

        int sum = 0;
        for (int i = 1; i <= 100; i++) {
            sum += i;
        }
        System.out.println("sum=" + sum);

//        for (int i = 1; i <= 9; i++) {
//            for (int j = 1; j <= 9; j++) {
//                if (i >= j) {
//                    if (i * j <= 9) {//对齐
//                        System.out.print(j + " * " + i + " = " + i * j + "     ");
//                    } else {
//                        System.out.print(j + " * " + i + " = " + i * j + "    ");
//                    }
//                }
//            }
//            System.out.println();
//        }
    }
}
```

执行过程：

| times = 0 | true | 输出"行动是成功的阶梯" |
|---|---|---|
| times = 1 | true | 输出"行动是成功的阶梯" |
| times = 2 | true | 输出"行动是成功的阶梯" |
| times = 3 | true | 输出"行动是成功的阶梯" |
| times = 4 | true | 输出"行动是成功的阶梯" |
| times = 5 | false | for循环结束 |
| | |输出"继续执行..."|

##

|次数|代码|循环|
|---|---|---|
|相关|/|for|
|无关|相同|do...while|
|无关|不同|while|

## 随机数（上）

- 生成100个1-1000随机数

```java
for (int i = 0; i < 100; i++) {
    int num = (int)(1000 * Math.random() + 1);//生成1-1000随机数
    System.out.println(num);
}
```

## 其他

```java
for (int i = 0; i < 100; i++) {
    UUID uuid = UUID.randomUUID();
    System.out.println(uuid);
}
```

```java
int count = 0;
//10000次顺序生成char
for (int i = 0; i < 100; i++) {
    for (int j = 0; j < 100; j++) {
         char c = (char)count;
         System.out.print(c);
         count++;
    }
    System.out.println();
}
```

### 一些操作

```java
//\u000d + 任意代码
//测试\u000dSystem.out.println("hello world");
// ↑ 输出结果为hello world
//\u000aSystem.out.println(111_111);
// ↑ 输出结果为111111（111_111会变成111111）
```

- - -

## practice

```java
package day04;
import java.util.Scanner;

public class Practice04 {
    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);

        //1
        // CommandBySwitch命令解析程序：接收用户输入的命令，依据命令做不同的操作

        System.out.println("输入命令：");
        int num = scan.nextInt();
        switch(num) {
            case 1:
                System.out.println("命令1");
                break;
            case 2:
                System.out.println("命令2");
                break;
            case 3:
                System.out.println("命令3");
                break;
            case 4:
                System.out.println("命令4");
                break;
            default:
                System.out.println("输入错误");
                break;
        }


        //2
        //Guessing猜数字之while版：随机生成一个数，由用户来猜，猜不对则反复猜，并给出大小提示，猜对的则结束，用while来实现。

        int n1 = 250;
        System.out.println("猜吧！");
        int guess1 = scan.nextInt();
        while (guess1 != n1) {
            if (guess1 > n1) {
                System.out.println("太大了");
            } else {
                System.out.println("太小了");
            }
            System.out.println("猜吧！");
            guess1 = scan.nextInt();
        }
        System.out.println("恭喜你猜对了！");


        //3
        //Guessing猜数字之do...while版：随机生成一个数，由用户来猜，猜不对则反复猜，并给出大小提示，猜对的则结束，用do...while来实现。
        int n2 = 250;
        int guess2;
        do {
            System.out.println("猜吧！");
            guess2 = scan.nextInt();
            if (guess2 > n2) {
                System.out.println("太大了");
            } else if (guess2 < n2) {
                System.out.println("太小了");
            } else {
                System.out.println("恭喜你猜对了！");//也可以直接写break，最后写System.out.println("恭喜你猜对了！");
            }
        } while (guess2 != n2);


        //4
        //for循环：输出5次"行动是成功的阶梯"、输出9的乘法表(1到9、1/3/5/7/9、9到1)、累加1到100的和
        //输出5次"行动是成功的阶梯"
        for (int time = 1; time <= 5; time++) {
            System.out.println("行动是成功的阶梯");
        }

        //输出9的乘法表(1到9)
        for (int num1 = 1; num1 <= 9; num1++) {
            System.out.println(num1 + " * 9 = " + num1 * 9);
        }

        //输出9的乘法表(1/3/5/7/9)
        for (int num2 = 1; num <= 9; num+=2) {
            System.out.println(num2 + " * 9 = " + num2 * 9);
        }

        //输出9的乘法表(9到1)
        for (int num3 = 9; num3 >= 1; num3--) {
            System.out.println(num3 + " * 9 = " + num3 * 9);
        }

        //累加1到100的和
        int sum = 0;
        for (int i = 1; i <= 100; i++) {
            sum += i;
        }
        System.out.println("sum = " + sum);

    }
}
```

## extra practice

```java
package day04;
import java.util.Scanner;

public class Practice04E {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        
        //接收用户输入的一个整数num，判断它的正负零值，正数则输出"+"，负数则输出"-"，0则输出"0"
        System.out.println("输入一个整数：");
        int num = scan.nextInt();
        if (num > 0) {
            System.out.println("+");
        } else if (num < 0) {
            System.out.println("-");
        } else {
            System.out.println("0");
        }
        
        //接收用户输入的年份year和月份month，计算该年该月的天数，并输出
        System.out.println("请输入年份：");
        int year = scan.nextInt();
        System.out.println("请输入月份：");
        int month = scan.nextInt();
        if (month == 2) {
            if (year % 4 == 0) {
                System.out.println(year + "年的" + month + "有29天");
            } else {
                System.out.println(year + "年的" + month + "有28天");
            }
        } else if (month == 4 || month == 6 || month == 9 || month == 11) {
            System.out.println(year + "年的" + month + "有30天");
        } else {
            System.out.println(year + "年的" + month + "有31天");
        }
        
        //输出1900到2023年之间所有的闰年(每够10个年份，换一行)
        int difference = 0;
        while (difference <= 2023 - 1900) {
            System.out.print(1900 + difference + " ");
            difference += 4;
            if (difference % 40 == 0) {
                System.out.println();
            }
        }
    }
}
```

   1.参考代码：

   ```java
   package test;
   import java.util.Scanner;
   public class Day04 {
       public static void main(String[] args) {
   		Scanner scan = new Scanner(System.in);
           System.out.println("请输入一个整数:");
           int num = scan.nextInt();
   
           if(num>0){
               System.out.println("+");
           }else if(num<0){
               System.out.println("-");
           }else{
               System.out.println("0");
           }
       }
   }
   ```

   2.参考代码：

   ```java
   package test;
   import java.util.Scanner;
   public class Day04 {
       public static void main(String[] args) {
   		Scanner scan = new Scanner(System.in);
           System.out.println("请输入年份:");
           int year = scan.nextInt();
           System.out.println("请输入月份:");
           int month = scan.nextInt();
           int days = 0; //天数
           switch(month){
               case 1:
               case 3:
               case 5:
               case 7:
               case 8:
               case 10:
               case 12:
                   days = 31;
                   break;
               case 4:
               case 6:
               case 9:
               case 11:
                   days = 30;
                   break;
               case 2:
                   if((year%4==0 && year%100!=0) || year%400==0){
                       days = 29;
                   }else{
                       days = 28;
                   }
           }
           System.out.println(year+"年的"+month+"月共"+days+"天");
       }
   }
   ```

   3.参考代码：

   ```java
   int count=0;
   for(int year=1900;year<=2023;year++){
       if((year%4==0 && year%400!=0) || year%400==0){
           System.out.print(year+" ");
           count++;
           if(count%10==0){
               System.out.println();
           }
       }
   }
   ```