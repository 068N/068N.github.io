# day05 notes

## 1 数组的复制

System.arraycopy(a,1,b,0,4);
- 灵活性好

```java
package day06;
//数组的展示
public class ArrayDemo {
    public static void main(String[] args) {
        //6.数组的复制
        int[] a = {10,20,30,40,50};
        int[] b = new int[6];

        //a:源数组
        //1:源数组的起始下标
        //b:目标数组
        //0:目标数组的起始下标
        //4:要复制的元素个数
//        System.arraycopy(a,1,b,0,4);//复制a数组下标为1-4元素至b数组的0-3下标
        System.arraycopy(a,0,b,0,5);//复制a数组的前5个元素至b数组的0-4下标

        for (int i = 0; i < b.length; i++) {
            System.out.println(b[i]);
        }
    }
}
```

int[] c = Arrays.copyOf(a, 6);
- 灵活性差


    若目标数组长度>原数组长度，则末尾补默认值
    若目标数组长度<原数组长度，则末尾的截掉

```java
package day06;
//数组的展示
import java.util.Arrays;
public class ArrayDemo {
    public static void main(String[] args) {
        //6.数组的复制
        int[] a = {10,20,30,40,50};
        int[] b = new int[6];

        //a:源数组
        //1:源数组的起始下标
        //b:目标数组
        //0:目标数组的起始下标
        //4:要复制的元素个数
//        System.arraycopy(a,1,b,0,4);//复制a数组下标为1-4元素至b数组的0-3下标
        System.arraycopy(a,0,b,0,5);//复制a数组的前5个元素至b数组的0-4下标

        int[] c = Arrays.copyOf(a, 6);

//        for (int i = 0; i < b.length; i++) {
//            System.out.println(b[i]);
//        }

        for (int i = 0; i < c.length; i++) {
            System.out.println(c[i]);
        }
    }
}
```

- 数组的扩容(创建了一个更大的新的数组，并将数组**复制**了进去)

```java
package day06;
//数组的展示
import java.util.Arrays;
public class ArrayDemo {
    public static void main(String[] args) {
        //6.数组的复制
        int[] a = {10,20,30,40,50};
        
        //数组的扩容(创建了一个更大的新的数组，并将数组复制了进去)
        a = Arrays.copyOf(a, a.length + 1);

        for (int i = 0; i < a.length; i++) {
            System.out.println(a[i]);
        }
    }
}
```

```java
package day06;
//求数组的最大值，并将其存储到数组最后一个元素的下一个位置
import java.util.Arrays;

public class MaxOfArray {
    public static void main(String[] args) {
        int[] arr = new int[10];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (int)(Math.random() * 100);
            System.out.println(arr[i]);
        }

        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {//遍历剩余元素
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println("最大值：" + max);

        arr = Arrays.copyOf(arr, arr.length + 1);//扩容数组

        arr[arr.length - 1] = max;//把最大值max赋值到最后一个元素上

        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

## 2 方法

### 2.1 方法的意义

- 也称函数、过程
- 作用：用于封装一段业务逻辑功能
- 建议：尽可能独立，一个方法只干一件事
- 调用：可以反复被调用
- 好处：可以减少代码重复，有利于代码维护
- 何时用：只要是一个独立的业务，就应该封装到一个方法中


    System.out.println();
    int a = scan.nextInt();
    int b = scan.nextDouble();
    int c = Math.random();
    Arrays.sort();
    arr = Arrays.copyOf(arr, arr.length + 1);//扩容数组
    int[] d = Arrays.copyOf(a,6)//---------有返回值
    System.arraycopy(a,0,b,0,5);//---------无返回值（void）

- 定义方法的五个要素：修饰词、返回值类型、方法名、参数列表、方法体

方法可以有返回值，也可以没有返回值：
1. 无返回值--------返回值统一写成void
2. 有返回值--------返回值类型设计为特定的数据类型即可---8种基本类型、String、数组

何时有返回值？何时无返回值？
1. 方法执行完之后：
    1. 若还需要用到方法中的数据---有返回值
    2. 若不需要用到方法中的数据---无返回值

```java
public static void say()
public static int plus(int num1, int num2)
```

方法可以有参数，也可以无参数
- 有参可以使方法更灵活

### 2.2 方法的定义和调用

#### 2.2.1 方法的定义

```java
修饰词 返回值类型 方法名（参数列表）{
    方法体
}
```

#### 2.2.2 方法的调用

- 无返回值：方法名（有参传参）
- 有返回值：数据类型 变量=方法名（有参传参） 


      return：1）结束方法 2）返回值
      return：1）结束方法



```java
package day06;
//方法的演示
import java.util.Arrays;
import java.util.Random;

public class MethodDemo {
    //方法的主入口
    public static void main(String[] args) {
        say();//调用say()方法//----------------------------------------实参
        //sayHi();//编译错误，有参必须传参
        //sayHi(250);//编译错误，参数类型必须匹配
        sayHi("张三");//----------------------------------------实参
        sayHello("张三", 25);//----------------------------实参
        sayHello("李四", 66);//----------------------------实参
        double a = getNum();
        a = a + 1;
        System.out.println(a);

        int b = plus(5, 6);
        System.out.println(b);//11-----------------------模拟对返回值的后续操作

        int m = 5, n = 6;
        int c = plus(m, n);//传的是m,n里的数
        System.out.println(c);//11-----------------------模拟对返回值的后续操作

        int[] d = generateArray(5,100);//模拟第1个人的访问
        System.out.println("数组的长度：" + d.length);//---模拟对返回值的后续操作

        int[] e = generateArray(8,20);//模拟第2个人的访问
        System.out.println("第一个元素的值：" + e[0]);//?---模拟对返回值的后续操作

        for (int i = 0; i < e.length; i++) {//-----------模拟对返回值的后续操作
            System.out.println(e[i]);
        }
    }

    //无参无返回值
    public static void say() {
        System.out.println("大家好，我叫WKJ，今年39岁了");
    }

    //有参无返回值
    public static void sayHi(String name) {//----------------------------形参
        System.out.println("大家好，我叫" + name + "，今年39岁了");
    }

    //有参无返回值
    public static void sayHello(String name, int age) {//----------------形参
        if (age >= 50) {//在某种特定条件下，提前结束方法
            return;//结束方法
        }
        System.out.println("大家好，我叫" + name + "，今年" + age + "岁了");
    }

    //无参有返回值
    public static double getNum() {
        //在所有返回值的方法中，必须通过return来返回数据，并且类型必须匹配
        //return;//编译错误，return后必须跟一个数据
        //return "abc";//类型不匹配
        return 8.8;//1）结束方法的执行 2）返回结果给调用方
    }

    //有参有返回值
    public static int plus(int num1, int num2) {
        int num = num1 + num2;
        return num;
        //return num1 + num2;//返回的是num1与num2的和
    }

    //生成一个整型数组，并填充随机数据
    public static int[] generateArray(int len, int max) {
        Random rand = new Random();
        int[] arr = new int[len];
        for (int i = 0; i < arr.length; i++)
            arr[i] = rand.nextInt(max + 1);
        return arr;
    }
}
```

### 2.3 方法的重载

- 语法：发生在同一类中，方法名相同，参数列表不同
- 绑定：编译器在编译时会根据方法的签名自动绑定方法

```java
package day06;
//方法的演示
import java.util.Arrays;
import java.util.Random;

public class MethodDemo {
   //方法的主入口
   public static void main(String[] args) {
      say();//调用say()方法//------------------------------------------实参
      //say();//编译错误，有参必须传参
      //say(250);//编译错误，参数类型必须匹配
      say("张三");//--------------------------------------------实参
      say("张三", 25);//-----------------------------------实参
      say("李四", 66);//-----------------------------------实参
      //say(3.4567);//编译错误，没有double参的say方法

      double a = getNum();
      a = a + 1;
      System.out.println(a);

      int b = plus(5, 6);
      System.out.println(b);//11-----------------------模拟对返回值的后续操作

      int m = 5, n = 6;
      int c = plus(m, n);//传的是m,n里的数
      System.out.println(c);//11-----------------------模拟对返回值的后续操作

      int[] d = generateArray(5,100);//模拟第1个人的访问
      System.out.println("数组的长度：" + d.length);//---模拟对返回值的后续操作

      int[] e = generateArray(8,20);//模拟第2个人的访问
      System.out.println("第一个元素的值：" + e[0]);//?---模拟对返回值的后续操作

      for (int i = 0; i < e.length; i++) {//-----------模拟对返回值的后续操作
         System.out.println(e[i]);
      }
   }

   //无参无返回值
   public static void say() {
      System.out.println("大家好，我叫WKJ，今年39岁了");
   }

   //有参无返回值
   public static void say(String name) {//------------------------------形参
      System.out.println("大家好，我叫" + name + "，今年39岁了");
   }

   //有参无返回值
   public static void say(String name, int age) {//---------------------形参
      if (age >= 50) {//在某种特定条件下，提前结束方法
         return;//结束方法
      }
      System.out.println("大家好，我叫" + name + "，今年" + age + "岁了");
   }

   public static void say(int age) {}
   public static void say(int age, String name) {}
   //public static int say( return 1) {}//编译错误，重载与返回值类型无关
   //public static void say(String address) {}//编译错误，重载与参数名称无关

   //无参有返回值
   public static double getNum() {
      //在所有返回值的方法中，必须通过return来返回数据，并且类型必须匹配
      //return;//编译错误，return后必须跟一个数据
      //return "abc";//类型不匹配
      return 8.8;//1）结束方法的执行 2）返回结果给调用方
   }

   //有参有返回值
   public static int plus(int num1, int num2) {
      int num = num1 + num2;
      return num;
      //return num1 + num2;//返回的是num1与num2的和
   }

   //生成一个整型数组，并填充随机数据
   public static int[] generateArray(int len, int max) {
      Random rand = new Random();
      int[] arr = new int[len];
      for (int i = 0; i < arr.length; i++)
         arr[i] = rand.nextInt(max + 1);
      return arr;
   }
}
```

### 2.4 补充

1. - 形参：形式参数，在定义方法时的参数
   - 实参：实际参数，在调用方法时的参数
2. 方法的签名：方法名+参数列表

## practice

      public static void main(String[] args) {
         say();
         say("zhangsan");
         say("zhangsan", 25);
         double a = getNum();//输出a--模拟对返回值的后续操作
         int b = plus(5, 6);//输出b--模拟对返回值的后续操作
         int m = 50, n = 60; int c = plus(m, n);//输出c--模拟对返回值的后续操作
         int[] d = generateArray(5, 300);//输出d的长度，输出每个元素的值--模拟对返回值的后续操作
         int[] e = generateArray(3, 10);//输出第1个元素的值，输出e中每个元素的值--模拟对返回值的后续操作
      }
      public static void say() {固定的问好}
      public static void say(String name) {问好，名字写活了}
      public static void say(String name, int age) {问好，名字和年龄都写活了}
      public static double getNum() {return 8.88;}
      public static int plus(int num1, int num2) {return num1 + num2;}
      public static int[] generateArray(int len, int max){
         return arr;
      }


```java
package day06;
import java.util.Random;

public class MethodDemo2 {
    public static void main(String[] args) {
        say();
        say("zhangsan");
        say("zhangsan", 25);
        double a = getNum();//输出a--模拟对返回值的后续操作
        int b = plus(5, 6);//输出b--模拟对返回值的后续操作
        int m = 50, n = 60; int c = plus(m, n);//输出c--模拟对返回值的后续操作
        int[] d = generateArray(5, 300);//输出d的长度，输出每个元素的值--模拟对返回值的后续操作
        System.out.println("d的长度：" + d.length);
        for (int i = 0; i < d.length; i++) {
            System.out.println(d[i]);
        }
        int[] e = generateArray(3, 10);//输出第1个元素的值，输出e中每个元素的值--模拟对返回值的后续操作
        System.out.println("e的第一个元素：" + e[0]);
        for (int i = 0; i < e.length; i++) {
            System.out.println(e[i]);
        }
    }

    public static void say() {
        System.out.println("大家好，我是张三，今年25岁了");
    }
    public static void say(String name) {
        System.out.println("大家好，我是" + name + "，今年25岁了");
    }
    public static void say(String name, int age) {
        System.out.println("大家好，我是" + name + "，今年" + age + "岁了");
    }
    public static double getNum() {
        return 8.88;
    }
    public static int plus(int num1, int num2) {
        return num1 + num2;
    }
    public static int[] generateArray(int len, int max){
        int[] arr = new int[len];
        Random rand = new Random();
        for (int i = 0; i < arr.length; i++) {
            arr[i] = rand.nextInt(max + 1);
        }
        return arr;
    }
}
```

```java
package day06;

import java.util.Arrays;

public class MaxOfArray2 {
    public static void main(String[] args) {
        //创建数组
        int[] arr = new int[10];//声明数组
        for (int i = 0; i < arr.length; i++) {
            arr[i] = (int)(Math.random() * 100);//给数组里的数赋随机值
            System.out.println(arr[i]);//输出数组里的值
        }

        //找最大值
        int max = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if (max < arr[i]) {
                max = arr[i];
            }
        }

        System.out.println("最大值：" + max);//输出最大值
        
        arr = Arrays.copyOf(arr, arr.length + 1);//扩容数组
        arr[arr.length - 1] = max;//把最大值赋给arr最后一个元素

        //输出数组
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

## extra practice

```java
package day06;

import java.util.Random;

public class Practice06E {
    public static void main(String[] args) {
        int[] arr = generateArray(10, 100);
        System.out.println(getMaxOfArray(arr));
        printArrayData(arr);
    }

    public static int[] generateArray(int len, int max){
        int[] arr = new int[len];
        Random rand = new Random();
        for (int i = 0; i < arr.length; i++) {
            arr[i] = rand.nextInt(max + 1);
        }
        return arr;
    }

    public static int getMaxOfArray(int[] arr) {
        int max = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        return max;
    }

    public static void printArrayData(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```