# day02 notes

## 1 Variable（变量）：存数的

  - 声明：----相当于在银行开了个帐户
  - 初始化：----相当于给帐户存钱
  - 使用：-----使用的是帐户里面的钱
    - 对变量的使用就是对它所存的那个数的使用
    - 变量的用之前必须声明并初始化
  - 命名：-----相当于给帐户起名
    - 只能包含字母、数字、_和$符，不能以数字开头
    - 严格区分大小写
    - 不能使用关键字
    - 允许中文命名，但不建议，建议"英文的见名知意"、"小驼峰命名法"

## 2 八种基本数据类型

- byte、short、int、long、float、double、boolean、char

## 2.1 int

- int：整型，4个字节，-21个多亿到21个多亿
  - 整数直接量默认为int类型，但不能超出范围，若超范围则发生编译错误
  - 两个整数相除，结果还是整数，小数位无条件舍弃(不会四舍五入)
  - 运算时若超出范围，则发生溢出，溢出不是错误，但是需要避免

## 2.2 long
- long：长整型，8个字节，-900万万亿多到900万万亿多
  - 若想表示长整型直接量，需在数字后加L或l
  - 运算时若有可能溢出，建议在第1个数字后加L

## 2.3 double
- double：浮点型，8个字节，很大很大很大
  - 小数直接量默认为double型，若想表示float，需在数字后加F或f
  - 不能表示精确数据，运算时有可能会发生舍入误差，精确场合不能使用
    
## 2.4 boolean
- boolean：布尔型，1个字节
  - 只能存储true或false
  
## 2.5 char

- 采用的是Unicode编码格式，一个字符对应一个码

       表现的形式是字符char，但本质上是码int(0到65535之间)
  - 字符型直接量必须放在单引号中，有且仅有1个

ASCII

|char|码|
|:-----:|:-----:|
| 'a' | 97  |
| 'A' | 65  |
| 0   | 48  |


<br>
- 只能存一个字符 'a' <br>
- 特殊字符通过\转义 <br>

```java
package day02;

public class DataTypeDemo {
    public static void main(String[] args) {
        char c1 = '女'; //字符女
        char c2 = 'f'; //字符f
        char c3 = '6'; //字符6
        char c4 = ' '; //空格符
        // char c5 = 女;
        // char c6 = '';
        // char c7 = '10';
        char c8 = 65; //0到65535之间
        System.out.println(c8); //println()会根据变量的类型做输出展示
                                // c8为char类型，会以字符类型输出
        char c9 = '\'';
        System.out.println(c9);

        char c10 = 97;
        char c11 = 48;
        System.out.println(c10);
        System.out.println(c11);

        char c12 = 10001;
        System.out.println(c12);

        int z = c11;
        System.out.println(z);
    }
}
```

## 3 typecasting

- 自动：隐式 **小到大** <br>
- 强制：**大到小** <br>
- 语法：注意装换为的类型 <br>
- 强制转换可能溢出，也可能丢失精度 <br>

- byte < short < int < long < float < double <br>
  char < int <br>

<br>


```java
package day02;

public class DataTypeDemo {
    public static void main(String[] args) {
        // byte
        int a = 5;
        long b = a; // 自动
        int c = (int)b; // 强制

        //自动
        long d = 5;
        double e = 5;

        //强制
        long f = 100000000000000L;
        int g = (int)f;
        System.out.println(g); // 溢出276447232

        double h = 25.987;
        int i = (int)h;
        System.out.println(i); // 丢失精度
    }
}
```

## 4 two rules

- int直接量可以直接赋值给byte，short，char，但不能超过范围 <br>
直接量可以直接赋值eg. byte b2 = 6; <br>
- byte，short，char型参与运算时，先一律自动转换为int再运算eg. byte b3 = b1 + b2; <br>

```java
package day02;

public class DataTypeDemo {
    public static void main(String[] args) {
        byte b1 = 5;
        byte b2 = 6;
        byte b3 = (byte)(b1 + b2); //byte和byte相加，自动转成int，因此不能直接赋值给byte类型 
        //               int + int
        //                 int
        
        System.out.println(2+2); //4
        System.out.println(2+'2'); //52，int和char相加
        System.out.println('2'+'2'); //100，char相加
        System.out.println('我'+'你'); //45425，char相加
        System.out.println((int)'我'); //25105，查看对应的码
        System.out.println((char)97); //a，查看对应的字符
        System.out.println('2'); //2，没有运算
    }
}
```

- - -

## practice

```java
package day02;

public class Practice02 {
    public static void main(String[] args) {
        //1
        //声明一个变量，一次声明多个变量。
        int a;
        int b,c;

        //声明变量直接初始化，先声明变量，而后再给变量初始化。
        int d = 114;

        int e;
        e = 514;

        //声明整型变量g，声明另一个整型变量h并赋值为g+10，输出变量h的值。
        int g = 1919810;
        int h = g + 10;
        System.out.println(h);

        //在g本身基础之上增10，输出变量g的值。
        g += 10;
        System.out.println(g);

        //声明一些正确的和错误的变量名。
        //正确的
        int age;
        int score,myScore,myJavaScore;
        //正确但不建议的
        int i = 10;
        int nianLing;
        int 年龄;
        //错误的
        //int 0x,a_5,_a,$_b;
        //int a*b;
        //int 1a;
        //int aa = 5;
        //System.out.println(aA);
        //int class;
        //int package;

        //2
        //声明初始化两个以上整数变量，并且输出两个整数变量的除法结果
        int l,m;
        l = 100;
        m = 5;
        System.out.println(l/m);

        //声明两个很大的变量，然后相加，输出运算结果，测试运算溢出现象
        int o,p;
        //long o = 10000000000;超100亿
        o = 2147483647;
        p = o + 1;
        System.out.println(p);

        //3
        //声明初始化两个以上的长整型变量
        long q = 1000L;
        //long r = 10000000000;超100亿
        long r = 10000000000L;

        //声明变量存储几个较大数据的运算，演示：若有可能溢出建议将L设计在第1个数字后。
        long s = 1000000000*3*10L;//L在后
        long t = 1000000000L*3*10;//L在前
        System.out.println(s);//不是300亿
        System.out.println(t);//300亿

        //4
        //声明初始化两个以上的浮点型变量
        double u = 12.34;
        double v = 12.3456F;

        //声明几个浮点型变量并将它们做数学操作，演示double运算的舍入误差问题
        double w=12.34,x=10.0;
        System.out.println(w-x);

        //5
        //声明初始化两个以上的布尔型变量
        boolean y = true;
        boolean z = false;

        //6
        //声明初始化五个以上的字符型变量
        char c1 = 'k';
        char c2 = 'a';
        char c3 = '3';
        char c4 = '男';
        char c5 = '!';

        //声明字符型变量，演示转义符
        char c6 = '\'';
        System.out.println(c6);

        //7
        //声明几个变量，演示自动类型转换和强制类型转换的语法
        int i1 = 10;
        long l1 = i1; //自动
        int i2 = (int)l1; //强制

        //声明一个较大类型的长整型变量，演示强转可能会发生的溢出问题
        long l3 = 10000000000L;
        int i3 = (int)l3;
        System.out.println(i3);

        //声明一个较大精度的浮点型变量，演示强转可能会发生的丢失精度问题
        double d1 = 10.029;
        int i10 = (int)d1;
        System.out.println(i10);

        //8
        //声明两个byte型变量b1和b2，并赋值为直接量
        byte b1 = 5, b2 = 10;

        //声明一个byte型变量，并赋值为b1与b2的和
        byte b3 = (byte)(b1+b2);

    }
}
```
