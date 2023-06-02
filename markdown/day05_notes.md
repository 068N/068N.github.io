# day05 notes

## 1 for结构的特殊格式

|格式||
|---|---|
|省略要素1||
|省略要素3||
|省略要素1,3||
|省略要素1,2,3|死循环|

```java
package day05;
import java.sql.SQLOutput;
//for结构展示
public class ForDemo {
    public static void main(String[] args) {
        /*
        int num = 1;
        for (; num <= 9; num++) {
            System.out.println("我爱java");
        }
        
        int num = 1;
        for (; num <= 9;) {
            System.out.println("我爱java");
            num++;
        }
         */
        
        
        for (;;) {
            System.out.println("我爱java");
        }
        
        //若上一段代码是死循环，则下面的代码会标红
//        for (int i = 1, j = 5; i <= 5 && j < 0; i += 2, j -= 2) {
//            System.out.println("我爱java");
//        }
    }
}
```

## 2 随机加法运算器

```java
package day05;
//随机加法运算器
import java.util.Scanner;

public class Addition {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        int score = 0;//总分

        for (int i = 1; i <= 10; i++) {
            //1）出题 2）答题 3）判题
            int a = (int)(Math.random() * 100), b = (int)(Math.random() * 100);//加数a,b(0-99)
            System.out.println("(" + i + ")" + a + "+" + b + "=?" + "\n算吧！");//1）出题
            if (scan.nextInt() == a + b) {//2）答题 3）判题
                System.out.println("答对了");
                score += 10;//答对1题加10分
            } else {
                System.out.println("答错了");
            }
        }
        System.out.println("总分为：" + score);
    }
}
```

## 3 break

```java
package day05;
import java.sql.SQLOutput;
//for结构展示
public class ForDemo {
    public static void main(String[] args) {
        for (int num = 1; num <= 9; num++) {
            if (num == 4) {//在某种特定条件下，提前结束循环
                break;//跳出循环
            }
            System.out.println(num + "*9=" + num * 9);
        }
    }
}
```

| |输出|
|---|---|
|num==1|1*9=9|
|num==2|2*9=18|
|num==3|3*9=27|
|num==4||

## 4 continue

- 应用率不高

```java
package day05;
import java.sql.SQLOutput;
//for结构展示
public class ForDemo {
    public static void main(String[] args) {
        for (int num = 1; num <= 9; num++) {
            if (num % 3 == 0) {
                continue;//跳过，继续循环
            }
            System.out.println(num + "*9=" + num * 9);
        }
    }
}
```

| |输出|
|---|---|
|num==1|1*9=9|
|num==2|2*9=18|
|num==3|(continue)|
|num==4|4*9=36|
|num==5|5*9=45|
|num==6|(continue)|
|num==7|7*9=63|
|num==8|8*9=72|
|num==9|(continue)|
|num==10|(false)|

等效于：

```java
package day05;
import java.sql.SQLOutput;
//for结构展示
public class ForDemo {
    public static void main(String[] args) {
        for (int num = 1; num <= 9; num++) {
            if (num % 3 != 0) {
                System.out.println(num + "*9=" + num * 9);
            }
        }
    }
}
```

## 5 嵌套循环

- 循环中套循环，常常多行多列使用，外层控制行，外层控制列
- 执行规则：外层走一次，内层走所有次
- 建议嵌套循环越少越好
- break默认只跳出一层循环

```java
package day05;

public class MultiTable {
  public static void main(String[] args) {
    int num = 9;
    for (int i = 1; i <= num; i++) {
      for (int j = 1; j <= i; j++) {
        System.out.print(j + " * " + i + " = " + i * j + "\t");//用"\t"间隔替代空格
      }
      System.out.println();
    }

//        int num = 9;//9,12
//        int count = 1;
//        for (int i = 1; i <= num; i++) {
//            for (int k = 1; k <= count; k++) {
//                if (num <= 9) {
//                    System.out.print("————————————————");//9*9表的水平边线
//                } else {
//                    System.out.print("————————————————————————");//12*12表的水平边线
//                }
//            }
//            System.out.println();
//            count += 1;
//            for (int j = 1; j <= i; j++) {
//                if (num <= 9) {
//                    System.out.print("|\t" + j + " * " + i + " = " + i * j + "\t");//添加竖直边线
//                } else {
//                    System.out.print("|\t\t" + j + " * " + i + " = " + i * j + "\t\t");//添加竖直边线
//                }
//            }
//            System.out.print("|");//最后一列的竖直边线
//            System.out.println();
//        }
//        for (int k = 1; k <= num; k++) {//最后一行的水平边线
//            if (num <= 9) {
//                System.out.print("————————————————");
//            } else {
//                System.out.print("————————————————————————");
//            }
//        }
  }
}
```

## 6 数组（上）

- 是一种**引用数据**类型
- **相同数据类型**元素的集合
- 数组的定义
- 数组的初始化
- 数组的访问
- 数组的遍历
- 数组的排序

```java
package day05;
//数组的演示
public class ArrayDemo {
   public static void main(String[] args) {
      //1.数组的定义
      //声明整型数组变量a，包含5个元素
      int[] a = new int[5];
      //声明浮点型数组变量d，包含10个元素
      double[] d = new double[10];
      //声明布尔型数组变量b，包含26个元素
      boolean[] b = new boolean[26];

      //2.数组的初始化
      int[] arr1 = new int[3];//0,0,0
      int[] arr2 = {2,5,8};//2,5,8 (元素少)
      int[] arr3 = new int[]{2,5,8};//2,5,8
      int[] arr4;
      //arr2 = {2,5,8};//编译错误，此方式只能声明同时初始化
      arr4 = new int[]{2,5,8};
   }
}
```

- 默认值规则


    byte, short, int, long char-------0
    float, double---------------------0.0
    boolean---------------------------false


```java
package day05;
//数组的演示
public class ArrayDemo {
    public static void main(String[] args) {
        //3.数组的访问：访问的是数组中的元素
        int[] arr = new int[3];//0,0,0
        System.out.println("数组的长度：" + arr.length);
        //通过下标/索引/引号来访问元素，下标从0开始，最大到（数组长度-1）
        arr[0] = 100;//给第1个元素赋值为100
        arr[1] = 200;//给第2个元素赋值为200
        arr[2] = 300;//给第3个元素赋值为300
        //arr[3] = 400;//运行时会发生数组下标越界异常
        System.out.println(arr[arr.length-1]);//300
    }
}
```
- ArrayIndexOutOfBoundsException: 数组下标越界异常
   - 数组下标一定在0到数组长度-1之内，越界不会有编译错误，但运行时会有异常

```java
package day05;
//数组的演示
public class ArrayDemo {
    public static void main(String[] args) {
        //4.数组的遍历/迭代
        int[] arr = new int[10];
        for (int i = 0; i < arr.length; i++) {//遍历arr数组
            arr[i] = (int)(Math.random() * 100);//赋随机数
            System.out.println(arr[i]);
        }
    }
}
```

```java
package day05;

public class MaxOfArray {
    public static void main(String[] args) {
        int[] arr = new int[10];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (int)(Math.random() * 100);
            System.out.println(arr[i]);
        }

        //最大值
        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {//遍历剩余元素
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println("最大值：" + max);

        //最小值
        int min = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] < min) {
                min = arr[i];
            }
        }
        System.out.println("最小值：" + min);

        //总和
        int sum = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < sum) {
                sum += arr[i];
            }
        }
        System.out.println("总和：" + sum);
    }
}
```

- 数组的排序：升序（自然排序）、降序
   - 常见的排序算法：冒泡排序、快速排序、插入排序、希尔排序、归并排序、选择排序...

```java
package day05;
//数组的演示
import java.util.Arrays;

public class ArrayDemo {
    public static void main(String[] args) {
        //5.数组的排序：
        int[] arr = new int[10];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (int)(Math.random() * 100);
            System.out.println(arr[i]);
        }
        Arrays.sort(arr);//排序
        System.out.println("排序后：");
        System.out.println("升序：");
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
        System.out.println("降序：");
        for (int i = arr.length - 1; i >= 0; i--) {
            System.out.println(arr[i]);
        }
    }
}
```

## 7 随机数（下）

```java
import java.util.Random;
Random rand = new Random();
arr[i] = rand.nextInt(100);//0-99之间的随机整数，写100不包括100
```

```java
package day05;
//数组的演示
import java.util.Random;

public class ArrayDemo {
    public static void main(String[] args) {
        //5.数组的排序：
        Random rand = new Random();
        int[] arr = new int[10];
        for (int i = 0; i < arr.length; i++) {
            //arr[i] = (int)(Math.random() * 100);
            arr[i] = rand.nextInt(100);//0-99之间的随机整数
            System.out.println(arr[i]);
        }
    }
}
```

## practice

```java
package day05;
import java.util.Random;
import java.util.Scanner;
import java.util.Arrays;

public class Practice05 {
    public static void main(String[] args) {
        Random rand = new Random();//随机数工具
        Scanner scan = new Scanner(System.in);//扫描仪工具
        
        //1
        //Addition随机加法运算器：由系统随机出10道加法题，而后由用户来答题，答题后输出"答对了"或"答错了"，答对1题得10分，答错1题不扣分,最后输出总分数。
        int score = 0;//总分
        for (int i = 1; i <= 10; i++) {//重复10次
            int a = rand.nextInt(99);//生成0-100的随机数
            int b = rand.nextInt(99);//生成0-100的随机数
            System.out.println(a + "+" + b + "=");//输出问题
            int input = scan.nextInt();//用户输入的答案
            int result = a + b;//正确答案
            if (result == input) {
                System.out.println("答对了");//回答正确的提示
                score += 10;//加10分
            } else {
                System.out.println("答错了");//输错答案的提示
            }
        }
        System.out.println("总分为：" + score);//输出分数

        //2
        //MultiType九九乘法表：输出九九乘法表
        int num = 9;
        for (int n = 1; n <= 9; n++) {//行
            for (int i = 1; i <= n; i++) {//列
                System.out.print(i + "*" + n + "=" + n * i + "\t");//"\t"用于对齐
            }
            System.out.println();
        }
        
        //3
        //数组小代码练习：声明
        //定义至少两个数组，设计包含一些元素
        int[] arr1 = new int[10];//声明整型数组变量arr1，包含10个元素
        double[] arr2 = new double[5];//声明浮点型数组变量arr2，包含5个元素
        boolean[] arr3 = new boolean[7];//声明布尔型数组变量arr3，包含7个元素

        //4
        //数组小代码练习：初始化
        //定义至少三个数组，演示三种元素初始化方式
        //初始化方式1
        int[] arr4 = new int[5];//声明并初始化arr4，数组里已经有默认值：0,0,0,0,0
        //初始化方式2
        int[] arr5;//声明arr4
        arr5 = new int[]{1,2,3,4,5};//初始化arr5，数组里包含：1,2,3,4,5
        double[] d1 = new double[]{10.2, 29.1, 1.2};//声明并初始化d1，数组里包含：10.2,29.1,1.2
        //初始化方式3
        boolean[] b1 = {true, false, true};//声明并初始化b1，数组里包含：true,false,true

        //5
        //数组小代码练习：访问
        //定义数组，输出数组的长度
        //定义数组并分别给每个元素赋值，输出最后一个元素的值
        //编写代码演示数组操作常见的异常----数组下标越界
        int[] arr6 = new int[5];//定义数组
        System.out.println(arr6.length);//输出数组的长度
        arr6[0] = 1;//给arr6中第1个元素赋值为1
        arr6[1] = 3;//给arr6中第2个元素赋值为3
        arr6[2] = 5;//给arr6中第3个元素赋值为5
        arr6[3] = 7;//给arr6中第4个元素赋值为7
        arr6[4] = 9;//给arr6中第5个元素赋值为9
        System.out.println(arr6[arr6.length - 1]);//输出最后一个元素的值
        //arr6[5] = 11;//数组下标越界，arr6中只有5个元素

        //6
        //数组小代码练习：遍历
        //定义数组，包含10个元素，遍历数组，给每个元素赋值为0到99之间的随机数，输出每个元素的值
        int[] arr7 = new int[10];//定义数组，包含10个元素
        for (int i = 0; i < arr7.length; i++) {
            arr7[i] = rand.nextInt(100);//遍历数组，给每个元素赋值为0到99之间的随机数
            System.out.println(arr7[i]); //输出每个元素的值
        }

        //7
        //MaxOfArray求数组元素最大值
        //定义数组，包含10个元素，遍历数组，给每个元素赋值为0到99之间的随机数并输出，找到数组元素的最大值并输出
        int[] arr8 = new int[10];//定义数组，包含10个元素
        for (int i = 0; i < arr8.length; i++) {
            arr8[i] = rand.nextInt(100);//遍历数组，给每个元素赋值为0到99之间的随机数
            System.out.println(arr8[i]); //输出每个元素的值
        }

        int max = arr8[0]; //假设第1个元素为最大值
        for(int i = 1; i < arr8.length; i++){ //遍历剩余元素
            if(arr8[i] > max){   //若剩余元素大于max
                max = arr8[i]; //将max修改为较大的
            }
        }
        System.out.println("最大值为:" + max);

        //8
        //对数组进行升序排列，并输出排序后的结果
        int[] arr9 = new int[10];//定义数组，包含10个元素
        for (int i = 0; i < arr9.length; i++) {
            arr9[i] = rand.nextInt(100);//遍历数组，给每个元素赋值为0到99之间的随机数
            System.out.println(arr9[i]); //输出每个元素的值
        }

        Arrays.sort(arr9); //对arr数组做升序排列

        System.out.println("排序后:");

        System.out.println("升序输出:");
        for(int i = 0 ; i < arr9.length; i++){
            System.out.println(arr9[i]);//输出排序后的结果
        }

        /*
        System.out.println("倒着输出:");
        for(int i = arr9.length-1; i >= 0; i--){
            System.out.println(arr9[i]);//并没有改变数组arr9的升序排列
        }
        */
    }
}
```

## extra practice

```java
package day05;

public class Practice05E {
    public static void main(String[] args) {
        //1
        //利用for循环计算：求数字1到100之内，所有偶数的和，并输出
        int sum = 0;
        for (int i = 1; i <= 100; i++) {
            if (i % 2 == 0) {//筛选偶数
                sum += i;
            }
        }
        System.out.println("数字1到100之内所有偶数的和：" + sum);//输出

        //2
        //利用for循环计算：求8的阶乘，并输出
        int factorial = 1;
        int num = 8;
        for (int i = 1; i <= num; i++) {
            factorial *= i;
        }
        System.out.println(num + "的阶乘：" + factorial);//输出

        //3
        //利用for循环计算：打印字符*组成的等腰三角形
        int n = 6;
        for (int i = 1; i <= 2 * n; i+=2) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }

        //4
        //定义数组，包含10个元素，随机生成数据(范围自拟)，查找最大值和最小值，并输出
        int n1 = 10;
        int[] arr = new int[n1];
        for (int i = 0; i < n1; i++) {
            arr[i] = (int) (Math.random() * 100);
            System.out.println(arr[i]);
        }

        //最大值
        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {//遍历剩余元素
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println("最大值：" + max);

        //最小值
        int min = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] < min) {
                min = arr[i];
            }
        }
        System.out.println("最小值：" + min);

        /*
        //总和
        int sumAll = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < sumAll) {
                sumAll += arr[i];
            }
        }
        System.out.println("总和：" + sum);
         */
    }
}
```