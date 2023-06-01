# day03 notes

## 运算符

- 符号：+、-、*、/、%、++、--
    - %：取模、取余，余数为零的即为整除
    - ++/--：自增1/自减1，可在变量前，也可在变量后
        - 单独使用时，在前在后都一样
        - 被使用时，在前在后不一样

|a++|++a|
|:---:|:---:|
|a|a+1|


```java
package day03;

public class OperDemo {
    public static void main(String[] args) {
        /*
        符号：+、-、*、/、%、++、--
        %：取模、取余，余数为零的即为整除
         */

        /**
        System.out.println(5%2);//1
        System.out.println(8%2);//0
        System.out.println(2%8);//2

        int a = 5, b = 5;
        a++;
        ++b;
        System.out.println(a);//6
        System.out.println(b);//6
         */

        /**
        int a = 5, b = 5;
        int c = a++;//将a++的值5赋给c，同时a自增1变为6
        int d = ++b;//将++b的值6赋给d，同时b自增1变为6
        System.out.println(a);//6
        System.out.println(b);//6
        System.out.println(c);//5
        System.out.println(d);//6
        */
        
        
        int a = 5, b= 5;
        int c = a--;//将a--的值5赋给c，同时a自减1变为4
        int d = --b;//将--b的值4赋给c，同时b自减1变为4
        System.out.println(a);//4
        System.out.println(b);//4
        System.out.println(c);//5
        System.out.println(d);//4
    }
}
```

## 关系运算符

- 符号：>、<、>=、<=、==、!=
- 关系运算的结果为boolean型，关系成立为true，关系不成立为false

```java
package day03;

public class OperDemo {
    public static void main(String[] args) {
        int a = 5, b= 10, c = 5;
        boolean b1 = a>b;
        System.out.println(b1);//false
        System.out.println(c<b);//true
        System.out.println(a>=c);//true
        System.out.println(a<=b);//true
        System.out.println(a==c);//true
        System.out.println(a!=c);///false

        System.out.println(a%2==0);//false
        System.out.println(a+c>b);//false

        System.out.println(a++>5);//false---------a自增1变为6
        System.out.println(++a>5);//true---------a自增1变为7
    }
}
```

## 逻辑运算符

    只要考试及格就能毕业-----单条件
    考试及格并且出勤率够80%才能毕业-----多条件

- 符号：&&、||、!
- 逻辑运算是建立在关系运算之上
- 逻辑运算的结果也是boolean型
    

- &&：逻辑与（并且），两边都为真则为真，**见false则false**
    - 当第一个条件为false时会发生短路，后面的就不执行了

|能毕业吗？|false|false|false|true|
|:---:|:---:|:---:|:---:|:---:|
|考试及格吗？|true|false|false|true|
|出勤率够80%吗？|false|true|false|true|

- ||：逻辑或（或者），**有真则为真**，见true则true
    - 当第一个条件为true时会发生短路，后面的就不执行了
    - 不短路或：|
    - 例：相亲时第一条件（性别）为false则后面的条件不执行了

|能结账吗？|true|true|true|false|
|:---:|:---:|:---:|:---:|:---:|
|有现金吗？|true|false|true|false|
|有微信吗？|false|true|true|false|

- !：逻辑非（取反），非真则假，非假则真

|!|true|false|
|:---:|:---:|:---:|
|下雨了？|false|true|

```java
package day03;

public class OperDemo {
    public static void main(String[] args) {

        /*

        //&&
        int a = 5, b = 10, c = 5;
        boolean b1 = b>=a && b<c;
        System.out.println(b1);//true&&false==false
        System.out.println(b<=c && b>a);//false&&true==false
        System.out.println(a==b && c>b);//false&&false==false
        System.out.println(b!=c && a<b);//true&&true==true

        //在。。。之间|between ... and ...
        int age = 39;
        //年龄在18到50之间
        //age>=0 && age<=50
        System.out.println(age>=18 && age<=50);//年龄在18到50之间
        int score = 86;
        System.out.println(score>=0 && score<=100);//成绩在0到100之间
         */

        /*
        
        //||
        int a = 5, b = 10, c = 5;
        System.out.println(b>=a || b<c); //true||false==true
        System.out.println(b<c || b>a);//false||true==true
        System.out.println(b!=c || a<b);//true||true==true
        System.out.println(a==b || b<c);//false||false==false

        int score = 90;
        //score<0 || score>100
        System.out.println(score<0 || score>100);//成绩不合法验证
         */

        /*
        
        int a = 5, b = 10, c = 5;
        boolean b2 = !(a<b);
        System.out.println(b2);//!true==false
        System.out.println(!(a>b));//!false==true
         */

        //短路
        int a = 5, b = 10, c = 5;
        boolean b3 = a>b && c++>2;
        System.out.println(b3);//false
        System.out.println(c);//5，短路

        boolean b4 = a<b || c++>2;
        System.out.println(b4);//true
        System.out.println(c);//5，短路
    }
}
```

## 赋值运算符

- 简单赋值运算符：=
- 扩展赋值运算符：+=、-=、*=、/=、%=
- 自带**强转**功能

```java
package day03;

public class OperDemo {
    public static void main(String[] args) {
        //面试题：
        /*
        short s = 5;//没问题
        s = s + 10;//编译错误，需强转，改为：s = (short)(s+10)
        s += 10;//没问题，+=(赋值运算符)自带强转功能，相当于s = (short)(s + 10)
        */
        
        int a = 5;
        a += 10;//相当于a = (int)(a + 10)
        System.out.println(a);//15
        a *= 2;//相当于a = (int)(a * 2)
        System.out.println(a);//30
        a /= 6;//相当于a = (int)(a / 6)
        System.out.println(a);//5
    }
}
```

## 字符串连接运算符

- ’+‘
- 若加号的两边出现了字符串，则做字符串连接


    char: 字符型，单引号中，1个字符
    string: 字符串型，双引号中，0个到多个字符

    “” 0个字符
    “女” 1个字符
    “hello” 5个字符

- 若两边为数字，则做加法运算
- 任何类型的数据与字符串相连，结果一定是字符串

```java
package day03;

public class OperDemo {
    public static void main(String[] args) {
        int age = 39;
        System.out.println("age=");//age=
        System.out.println(age);//39
        System.out.println("age=" + age);
        System.out.println("我今年" + age + "岁了");

        String name = "WKJ";
        System.out.println("大家好，我叫" + name);
        System.out.println("大家好，我叫" + name + "，今年" + age + "岁了");

        System.out.println(10+20+""+30);//"3030"
        System.out.println(""+10+20+30);//"102030"
        System.out.println(10+20+30+"");//"60"
    }
}
```

## 三目运算符

条件运算符/三目运算符：有三个操作数的

- 一目：!、++、--、....
- 二目：+、-、....
- 三目：boolean?数1:数2（boolean）

- 执行过程：
    - 整个条件运算是有值的，它的值要么是?后的数1，要么是:后的数2
    - 判断boolean的值：
      - 若为true，执行?后的数1
      - 若为false，执行:后的数2
    
```java
package day03;

public class OperDemo {
    public static void main(String[] args) {
        int num = 0;
        int flag = num > 0 ? 1 : -1;
        System.out.println(flag);

        int a = 8, b = 55;
        int max = a > b ? a : b;
        System.out.println("max=" + max);
    }
}
```

## 结构

- 顺序结构：**从上往下**逐行执行，每行必走
- 分支结构：有条件的执行语句**一次**，并非每句必走
- 循环结构：有条件的执行语句**多次**，并非每句必走

基于条件执行

- 满500打8折，满79减30
- 打8折--基于条件执行
- 减30--基于条件执行

### 分支结构（上）

- if ...
- if ... else
- if ... else if
- switch ... case

- 满500打8折
- 满500打8折，不满500打9折
- 满1000打7折，满500打8折，不满500打9折

#### if

```java
if (boolean) {
    语句块
}
```
- 执行过程：
  - 判断boolean的值：
    - 若为true，则执行语句块（结束）
    - 若为false，则直接结束

```java
package day03;
//if...结构的展示
public class IfDemo {
    public static void main(String[] args) {
        //1)满500打8折
        double price = 600.0;//消费金额，带数（400）
        if (price >= 500) {//满500
            price *= 0.8;//打8折
        }
        System.out.println("最终消费金额为" + price);

        //2)判断成绩是否合法：
        int score = 95;//分数，带数（-5，555）
        if (score >= 0 && score <= 100) {
            System.out.println(score + "是合法成绩");
        }
        System.out.println("继续执行...");
    }
}
```

#### if ... else

```java
if (boolean) {
    语句块1
} else {
    语句块2
}
```

- 执行过程：
    - 判断boolean的值：
        - 若为true，则执行语句块1（结束）
        - 若为false，则执行语句块2（结束）
    - 语句块2选1
        - 语句块1、语句块2不会同时走
        - 语句块1、语句块2不会同时都不走

```java
package day03;
//if...else结构的展示
public class IfElseDemo {
    public static void main(String[] args) {
        //1)满500打8折，不满500打9折
        double price = 600.0;//带数（600.0，300.0）
        if (price >= 500) { //满500
            price *= 0.8;
        } else { //不满500
            price *= 0.9;
        }
        System.out.println("最终消费金额：" + price);

        //2)判断成绩合法还是不合法
        int score = 95;//带数（95，-5，555）
        if (score >= 0 && score <= 100) {
            System.out.println(score + "是合法成绩");
        } else {
            System.out.println(score + "不是合法成绩");
        }
    }
}
```

#### if ... else if

```java
if (boolean1) {
    语句块1
} else if (boolean2) {
    语句块2
} else if (boolean3) {
    语句块3
} else {
    语句块4
}
```

- 执行过程：
    - 判断boolean1的值：
        - 若为true，则执行语句块1（结束）
        - 若为false，则判断boolean2的值
            - 若为true，则执行语句块2（结束）
            - 若为false，则判断boolean3的值
                - 若为true，则执行语句块3（结束）
                - 若为false，则执行语句块4（结束）
  - 语句块必走其中之一
      - 语句块不会同时走
      - 语句块不会同时都不走

```java
package day03;
//if...else if结构的展示
public class IfElseIfDemo {
    public static void main(String[] args) {
        //1)满2000打5折，满1000不满2000打7折，满500不满1000打8折，不满900打9折
        double price = 6000.0;//带数(6000.0，1000.0，600.0，300.0)
        if (price >= 2000) {
            price *= 0.5;
        } else if (price >= 1000) {//(price >= 1000 && price < 2000)
            price *= 0.7;
        } else if (price >= 500) {//(price >= 500 && price < 1000)
            price *= 0.8;
        } else {//(price < 500)
            price *= 0.9;
        }
        System.out.println("最终消费金额为：" + price);
    }
}
```

- - -

## practice

```java
package day03;

public class Practice03 {
    public static void main(String[] args) {
        //标准练习

        /*
        列表：
            运算符的练习：算术、关系、逻辑、赋值、字符串连接、条件
            分支结构的练习：if结构
            分支结构的练习：if...else结构
            分支结构的练习：if...else if结构
         */

        //1
        //运算符的练习：算术
        //输出几个整数取模，验证结果
        System.out.println(10%2);//0
        System.out.println(10%3);//1
        System.out.println(10%7);//3
        System.out.println(10%17);//10

        //声明两个整型变量，演示单独使用时的自增和自减
        //自增
        int a = 1, b = 2;
        a++;
        ++b;
        System.out.println(a);//2
        System.out.println(b);//3

        //自减
        int c = 1, d = 2;
        c--;
        --d;
        System.out.println(c);//0
        System.out.println(d);//1

        // 声明几个整型变量，演示被使用时的自增和自减
        //自增
        int e = 10, f = 10;
        int i = e++;
        int j = ++f;
        System.out.println(e);//10
        System.out.println(f);//10
        System.out.println(i);//11
        System.out.println(j);//11

        //自减
        int g = 10, h = 10;
        int k = g--;
        int l = --h;
        System.out.println(g);//10
        System.out.println(h);//10
        System.out.println(k);//9
        System.out.println(l);//9

        //2
        //运算符的练习：关系
        //声明几个变量，演示最基本的>，<，>=，<=，==，!=操作
        int m = 10;
        int n = 5;
        boolean b1 = m > n, b2 = m < n, b3 = m >= n, b4 = m <= n,
                b5 = m == n, b6 = m != n;
        System.out.println(b1);//true
        System.out.println(b2);//false
        System.out.println(b3);//true
        System.out.println(b4);//false
        System.out.println(b5);//false
        System.out.println(b6);//true

        //演示关系运算符和算术运算符联合使用的效果
        System.out.println(m + 5 > n);//true
        System.out.println(m % 5 < n);//true
        System.out.println(m / 5 == n);//false
        System.out.println(n++ <= 5);//true
        System.out.println(n++ <= 5);//false

        //3
        //声明三个整型变量，演示&&和||，演示!
        //&&的演示要求：true+false、false+true、true+true、false+false
        int o = 5, p = 10, q = 10;
        System.out.println(o < 10*p && p == o);//true+false==false
        System.out.println(o == p && p == q);//false+true==false
        System.out.println(o < p && p == q);//true+true==true
        System.out.println(o > p && p != q);//false+false==false

        //||的演示要求：true+false、false+true、true+true、false+false
        System.out.println(o < 10*p || p == o);//true+false==true
        System.out.println(o == p || p == q);//false+true==true
        System.out.println(o < p || p == q);//true+true==true
        System.out.println(o > p || p != q);//false+false==false

        //!的演示要求：true、false
        System.out.println(!(10*p == q));//!false==true
        System.out.println(!(p == q));//!true==false

        //演示短路&&与短路||
        int r = 5;
        System.out.println(r != 5 && r++ < 10);//有false,短路
        System.out.println(r);
        System.out.println(r < 10 || r-- < 10);//有true,短路
        System.out.println(r);

        //4
        //运算符的练习：赋值
        //声明一个整型变量，演示扩展赋值+=、-=、*=、/=、%=的效果
        int s = 10;
        s += 3;
        System.out.println(s);//13
        s -= 1;
        System.out.println(s);//12
        s *= 2;
        System.out.println(s);//24
        s /= 4;
        System.out.println(s);//6
        s %= 5;
        System.out.println(s);//1

        //声明short型变量s，演示简单赋值运算的自增10，演示扩展赋值运算的自增10
        short s1 = 10;
        s1 = (short)(s1 + 10);
        System.out.println(s1);//1
        s1 += 10;
        System.out.println(s1);//1

        //5
        //运算符的练习：字符串连接
        //声明整型变量age和字符串型变量name，输出字符串连接的结果
        int age = 30;
        String name = "Ka";
        System.out.println("age: " + age + ", " + "name: " + name + ".");

        int averageScore = 100;
        char grade = 'A';
        System.out.println("The average score of course " + grade + " is " + averageScore + ".");

        //输出几个数据的拼接，演示字符串连接的同化作用
        int u = 10, v = 20, w = 100;
        System.out.println(u + v + w);//130
        System.out.println("" + u + v + w);//"1020100"
        System.out.println(u + "" + v + w);//"1020100"
        System.out.println(u + v + "" + w);//"30100"
        System.out.println(u + v + w + "");//"130"

        //6
        //运算符的练习：条件/三目
        //声明并初始化整型变量，使用条件运算符实现：若>0则给flag赋值为1，否则赋值为0
        int x = 10;
        int flag = x > 0 ? 1 : 0;//1
        System.out.println(flag);

        //声明两个整型变量，使用条件运算符实现：求这两个变量的最大值
        int y = 10, z = 20;
        System.out.println(y > z ? y : z);//20

        //7
        //分支结构的练习：if
        //满500打8折
        int price = 200;
        if (price >= 500) {
            price *= 0.8;
        }
        System.out.println("最终金额为: " + price);//200

        //判断成绩是否合法
        int score = 90;
        if (score <= 100 && score >= 0) {
            System.out.println("成绩合法");//执行
        }
        System.out.println("继续执行...");

        //8
        // 分支结构的练习：if...else
        //满500打8折，不满500打9折
        int price2 = 200;
        if (price2 >= 500) {
            price2 *= 0.8;
        } else {
            price2 *= 0.9;
        }
        System.out.println("最终金额为: " + price2);//180

        //判断成绩合法还是不合法
        int score2 = 110;
        if (score2 <= 100 && score >= 0) {
            System.out.println("成绩合法");
        } else {
            System.out.println("成绩不合法");//执行
        }
        System.out.println("继续执行...");

        //9
        //分支结构的练习：if...else if
        //满2000打5折，满1000不满2000打7折，满500不满1000打8折，不满500打9折
        int price3 = 1100;
        if (price3 >= 2000) {
            price3 *= 0.5;
        } else if (price3 >= 1000) {
            price3 *= 0.7;
        } else if (price3 >= 500) {
            price3 *= 0.8;
        } else {
            price3 *= 0.9;
        }
        System.out.println("最终金额为: " + price3);//770
    }
}
```

## extra practice

```java
package day03;

public class Practice03E {
    public static void main(String[] args) {
        //扩展练习

        //声明两个整型变量a和b并分别赋值，找到a和b中的最大值，并输出。用两种方式实现：条件运算符、if..else分支结构。
        int a = 10, b = 20;

        System.out.println(a > b ? a : b);
        
        if (a > b) {
            System.out.println(a);
        } else {
            System.out.println(b);
        }

        //声明一个整型变量year并存储年份，判断其是平年还是闰年，若是闰年则输出"某某某年是闰年"，否则输出"某某某年是平年"。
        int year = 2000;
        System.out.println(year % 4 == 0 ? year + "年是闰年" : year + "年不是闰年");

        //成绩等级判断：
        //注：考虑成绩的合法性：当不合法成绩时，输出"成绩不合法"
        int score = 100;

        if (score <= 100 && score > 85) {
            System.out.println("成绩：优");
        } else if (score <= 85 && score > 75) {
            System.out.println("成绩：良");
        } else if (score <= 75 && score >= 60) {
            System.out.println("成绩：合格");
        } else if (score < 60 && score >= 0) {
            System.out.println("成绩：不合格");
        } else {
            System.out.println("成绩不合法");
        }
    }
}

```