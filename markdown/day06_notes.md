# day06 notes

## 8种基本数据类型

- 不包括所有大写单词，如：String，Integer等。
- 详细内容见[day06周测总结](../html/day06周测总结.html)。

## if的简便写法

```java
if(false)
    System.out.println("1");//不会执行
    System.out.println("2");//会执行，不在if条件作用范围内
System.out.println("3");
if(false)
    System.out.println("4");//不会执行
System.out.println("5");

//输出结果2，3，5
```

## double的输出精度问题

```java
double d = 3 - 2.9;
System.out.println(d);//输出0.10000000000000009
```

