# 1. Java基础

P21-32

## 1.1 注释

1. 单行注释 //

2. 多行注释 /*

   ​			XXXXXXX

   ​					*/

``` java
// 此符号后的内容即被注释
```

## 1.2 标识符和关键字

### 1.2.1 标识符含义

Java 所有的组成部分都需要名字

public 、static 等等 都是关键字 是Java已经定义好的可以直接用的

- 48个关键字：

  abstract、assert、boolean、break、byte、case、catch、char、class、continue、default、do、double、else

  enum、extends、final、float、for、if、implements、import、int、interface、instanceof、long、native、new

  package、private、protected、public、return、short、static、strictfp、super、switch、synchronized、this

  throw、throws、transient、try、void、volatile

- 2个保留字：

  goto、const

- 3个特殊直接量：

  true、false、null

类名、变量名以及方法名都被称为标识符

```java
public class Basic2{
    public static void main(String[] args){
        String student = "GoQuokka";
    }
}
//这里有一个main方法 是程序的入口
```

类名：Basic2	变量名：student  	变量属性：String 	变量值：GoQuokka

### 1.2.2 标识符注意点

- 所有的标识符以字母（A-Z/a-z）、￥、_开头
- 首字符后可以是字母（A-Z/a-z）、￥、_、数字的任何组合
- 关键字不做变量名或方法名
- 大小写敏感
- 可以用中文 但不建议

## 1.3 数据类型

- Java 是<u>强类型语言</u>，要求变量的使用要严格符合规定，所有变量都必须先定义之后才能使用

> JavaScrip是弱类型语言

- 一旦定义变量，则变量类型确定，不经过转化就不会改变

### 1.3.1 分类

#### 基本类型(Primitive Type)

- ***数值型***

  - 整型

    **byte**:	1个字节范围：-128—127 

    **short**	2个字节范围：-32768—32767

    **int**		 4个字节范围：-2147483648—2147483647

    **long**	  8个字节范围：-9223372036854775808-9223372036854775807

  - 浮点型

    **float**	 4个字节范围

    **double** 8个字节范围

- ***字符型***

  **char** 	 2个字节范围

- ***boolean型***

  **true**/**false** 	1个字节范围

#### 引用类型（Reference Type）

类、接口、数组

#### 字节

- 位(bit)：计算机 **内部数据** 储存最小单位 

  > 11001100是一个八位二进制数

  字节(byte)：计算机 **数据处理** 的基本单位，用B表示

  字符：计算机中使用的字母、数字、字和符号

- 1bit表示1位

  1B = 8bit 

  1024B = 1KB

  1024KB = 1M

  1024M = 1G

  1024G = 1T

> 电脑的32位和64位的区别：32位支持4GB，64位支持128GB

### 1.3.2 数据类型间转换

低 --------------------------------------------------------> 高

byte,short,char -> int -> long -> float -> double

运算中，**不同类型的数据先转化为同一类型**，然后进行运算

#### 强制类型转换

高 -> 低

格式：（要转换的类型）要转换的变量

> E.g:
>
> ```java
> int i = 128;
> // byte b = i; 这样写会报错
> byte b = (byte)i;//i由int强制转换为byte
> System.out.println(i);
> System.out.println(b);
> ```
>
> 运行结果：
>
> 128
>
> -128

注意，这里b的值由i转换得到，按理应该也是128，但结果却是-128

这是因为，byte类型值最大为127，128超过了byte的范围，这就是 **内存溢出** 就出现问题了 

计算机直接从头顺延了 说白了就是：如果i是129，那么b就会是-127

所以，类型转换的时候，要注意范围！

#### 自动类型转换

低 -> 高

> E.g:
>
> ```java
> byte x = 12;
> int x2 = x; //自动转换了 什么都不用加
> System.out.println(x);
> System.out.println(x2);
> ```
>
> 运行结果：
>
> 12
>
> 12

#### 注意点

- 布尔值不能转换

- 不能把对象类型转换为不相干的类型 

  比如说，把引用类型转化为一个基本类型

- 在把高容量转化为低容量的时候，强制转换

  反之自动转换即可

- 转换时可能存在精度问题:

  > E.g:
  >
  > ```java
  > System.out.println((int)23.7);
  > System.out.println((int)-45.89f);
  > ```
  >
  > 运行结果：
  >
  > 23
  >
  > -45

  显而易见，int是整数类型，精度远小于double和float 在转换时要认真考虑 不存在四舍五入

- 操作比较大的数的时候，可能存在溢出问题（可见上文强制转换的byte例子）



### 1.3.3 拓展

- 整数进制：二进制(0b) 十进制 八进制(0) 十六进制(0x)

  ```java
  int i = 10;
  int i2 = 010;   //八进制 	0开头
  int i3 = 0x10;  //十六进制 0x   0~9 A~F
  int i4 = 0b10;  //二进制	0b
  System.out.println(i); 
  System.out.println(i2);
  System.out.println(i3);
  System.out.println(i4);
  ```

  > 运行结果：
  >
  > 10
  >
  > 8
  >
  > 16
  >
  > 2	

- 浮点数

  ```java
  float f = 0.1F;
  double d = 1.0/10;
  System.out.println(f==d);
  System.out.println(f);
  System.out.println(d);
  
  float f1 = 2131313131321F;
  float f2 = f1+1;
  System.out.println(f1==f2);
  ```

  > 运行结果：
  >
  > false
  >
  > 0.1
  >
  > 0.1
  >
  > true 
  
  float：有限 离散 舍入误差 --> 大约 接近但不等于
  
  ***<u>最好完全避免使用浮点数进行比较！</u>*** --->  **BigDecimal**	Java的一个数学工具类

---

- 字符

  ***<u>所有的字符本质还是数字！</u>***

  ```java
  char c1 = 'a';
  char c2 = '中';
  System.out.println(c1);
  System.out.println((int)c1);//强制转换
  System.out.println(c2);
  System.out.println((int)c2);//强制转换
  ```

  > 运行结果：
  >
  > a
  >
  > 97
  >
  > 中
  >
  > 20013 
  
  编码 **Unicode**表中 97=a 
  
  编码表达方式：
  
  ```java
  char c3 = '\u0061'; 	//	"\u"	表示编译 
  System.out.println(c3);
  ```
  
  运行结果： a

---

- 转义字符

  回车：\t (制表符)

  换行：\n

  ```java
  System.out.println("Hello\tWorld!");
  System.out.println("==============");
  System.out.println("Hello\nWorld!");
  System.out.println("==============");
  ```

  > 运行结果：
  >
  > Hello	World!
  >
  > ==============
  >
  > Hello
  >
  > World!
  >
  > ============== 

【这里只举了两个例子】

---

- ==的比较

  >如果比较的是基本数据类型，==比较的是**数值**是否一致
  >
  >如果比较的是引用数据类型，==比较的是**对象的地址**是否一致

  ```java
  String sa = new String("Hello world!");
  String sb = new String("Hello world!");
  System.out.println(sa==sb);	//false
  ```

  运行结果：false

  ```java
  String sc = "Hello world!";
  String sd = "Hello world!";
  System.out.println(sc==sd); //true
  ```

  运行结果：true

---

- 布尔值

  ```java
   boolean flag = true;
  if (flag==true){}
  if (flag) {}
  ```

  两个if语句实际上是一模一样的

  **【Less is more.】**代码要越 <u>精简</u> 越好

## 1.4 变量 常量 作用域

### 1.4.1 变量

- 变量，即可以变化的量

- 每个变量都有类型，类型可以是基本类型，也可以是引用类型

- 变量名必须是合法的标识符

- 变量声明是一条完整的语句，每个声明都必须以分号结束

  **type varName [=value] [{,varName[=value]}];**

  **数据类型 变量名 = 值; 可以用逗号隔开来声明多个变量**

- 注意 <u>程序可读性</u>

#### 变量作用域

- 类变量

  关键词：**static**

  从属于**类**

- 实例变量

  **没有static**关键词

  从属于**对象**

  如果不初始化，就是这个类型的默认值

  > E.g:
  >
  > ```java
  > public class variable{
  >  String name;
  >  int age;
  > 
  >  public static void main(String[] args){
  >      variable x = new variable();
  >      System.out.println(x.name);
  >      System.out.println(x.age);
  >  }
  > }
  > ```
  >
  > 运行结果：
  >
  > null
  >
  > 0

  - 布尔值默认值为**false**

    除了基本类型，其余的默认值都是**null**

- 局部变量

  从属于**方法**

  必须声明和初始化值

```java
public class Variable{
    static int allClicks = 0; //类变量
    String str = "hello world"; //实例变量
    
    public void method(){
        int i = 0; //局部变量
    }
}
```

#### 变量的命名规范

- 所有变量、方法、类名：见名知意
- **驼峰原则**：除了第一个单词之外，后面的单词首字母大写
- 类成员变量：首字母小写、驼峰原则 monthSalary
- 局部变量：首字母小写、驼峰原则
- 常量：大写字母、下划线 MAX_VALUE
- 类名：首字母大写、驼峰原则 Man,GoodMan
- 方法名：首字母小写、驼峰原则 run(),runRun()

### 1.4.2 常量

- 常量，初始化后不能再改变值，不会变动的量

- 是一种特殊的变量，值被设定后，在程序运行过程中不允许被改变

- 关键词：**final**

  格式：**final 常量名 = 值**

  > E.g:
  >
  > ```java
  > final int N = 0;
  > ```
  >
  > 如此，N值为0，不会再被改变

- 常量名一般用大写字符

- final、static、public、private是修饰符，在代码书写上不分前后

## 1.5 运算符

### 1.5.1 基本运算符

- 算术运算符：+ - * / % ++ --

- 赋值运算符：=

- 关系运算符：> < >= <= == !=instanceof

  返回的结果：布尔值（**true/false**）

- 逻辑运算符：&& || ！

- 位运算符：& | ^（取反） ~（非） >>（右移） <<（左移） >>>

- 条件运算符：？

- 扩展赋值运算符：+= -= *= /=

### 1.5.2 自增自减运算符

- ++ 自增

- -- 自减

- 是一元运算符

- 符号在前，先传原值再运算

  符号在后，先运算再传结果

  > E.g:
  >
  > ```java
  > int a = 3;
  > int b = a++;
  > int c = ++a;
  > ```
  >
  > 运行结果：
  >
  > a = 5
  >
  > b = 3
  >
  > c = 5

---

很多运算，我们会使用一些工具类来操作

比如：Math

> E.g:
>
> ```java
> double x = Math.pow(3，2);
> ```
>
> 运行结果：
>
> 9.0

### 1.5.3 逻辑运算符 位运算符

- 位运算符：& | ^（取反） ~（非） >>（右移） <<（左移） >>>

- 位运算符效率高

  ```java
  /*
          A = 0011 1100
          B = 0000 1101
          --------------------------
          A&B = 0000 1100
          A|B = 0011 1101
          A^B = 0011 0001 取反：相同取0，相反取1
          ~B = 0000 0010 非
          按位置来的
  
          2*8 = 16  2*2*2*2
          <<  *2
          >>  /2
  		
  		二进制
          0000 0000       0
          0000 0001       1
          0000 0010       2
          0000 0011       3
          0000 0100       4
          0000 1000       8
          0001 0000       16
           */
  
          System.out.println(2<<3);
  ```

  运行结果：16

### 1.5.4 三元运算符

> X ? Y : Z
>
> 如果X==true，则结果为Z，反之结果为Y

## 1.6 包机制

- 为了更好地组织类，用于区别类名的命名空间

- 一般利用公司域名倒置作为包名

- 包的本质就是文件夹

- 包内的类名不能重复

- 关键词：**package**

  格式：

  ```java
  package pk1[. pk2[. pk3...]];
  ```

  该命令必须在程序的最顶端，即第一行代码

- **导包**关键词：**import**

  格式：

  ```java
  import package1[.package2...].(classname|*);
  ```

  写在package命令行下面

## 1.7 JavaDoc

JavaDoc命令是用来生成自己API文档的

关键词：**/****

加在谁上面就是谁的，在类名上就是类的，在方法上就是方法的

参数

- @author 作者名
- @version 版本号
- @since 指明需要最早使用的jdk版本
- @param 参数名
- @return 返回值情况
- @throws 异常抛出情况

---

命令行生成JavaDoc文件：

在程序文件夹内以管理员身份运行cmd

输入命令：javaDoc -encoding UTF-8 -charset UTF-8 类名.java

生成该Java类的Doc相关文件

- index文件进入查看

![](C:\Users\奇遇记.Lin\Desktop\梅院资料\Java学习\Doc文件生成一览.png)



# 2. Java流程控制

## 2.1 Scanner

- 属于**IO流**的类

- 通过Scanner类获取用户的输入

- 基本语法：

  ```java
  Scanner s = new Scanner(System.in);
  ```

- 通过Scanner类获取输入的字符串：

  **next()**

  - 一定要读取到有效字符后才可以结束输入
  - 对输入有效字符之前遇到的空白，next()方法会自动将其去掉
  - 只有输入有效字符后才将其后面输入的空白作为分隔符或者结束符
  - next()不能得到带有空格的字符串

  **nextLine()**

  - 以Enter为结束符，也就是说，nextLine()方法返回的是输入回车键之前的所有字符
  - 可以获得空白

- 通过Scanner类判断是否有输入的数据：

  **hasNext()**

  **hasNextLine()**

- 用完就关

  **<u>凡是属于IO流的类，如果不关闭会一直占用资源</u>**

## 2.2 顺序结构

- java的基本结构就是顺序结构，除非特别指明，否则就按照顺序一句一句执行

- 顺序结构是最简单的算法结构，**从上到下**顺序
- 任何算法都离不开的基本算法结构

## 2.3 条件语句结构

### 2.3.1 if 选择结构

#### 单选择结构

```java
if(布尔表达式){
​	// 如果布尔表达式为true将执行的语句
}
```

#### 双选择结构

```java
if(布尔表达式){
    //如果布尔表达式为true将执行的语句
}else{
    //如果布尔表达式为false将执行的语句
}
```

#### 多选择结构

```java
if(布尔表达式1){
    //如果布尔表达式1为true将执行的语句
}else if(布尔表达式2){
    //如果布尔表达式2为true将执行的语句
}else if(布尔表达式3){
    //如果布尔表达式3为true将执行的语句
}else{
    //如果以上表达式都为false将执行的语句
}
```

- 一个语句至多有一个else语句，在所有的else if 语句之后
- 语句可以有若干个else if 语句，必须在else语句之前
- 一旦其中一个else if 语句为true，其他的else if 以及else语句都将跳过执行

#### 嵌套结构

```java
if(布尔表达式1){
    //如果布尔表达式1为true将执行的语句
    if(布尔表达式2){
        //如果布尔表达式2为true将执行的语句
    }
}
```

相互嵌套，互不影响

### 2.3.2 Switch多选择结构

- switch case语句

  判断、一个变量与一系列值中某个值是否相等，每个值称为一个分支

  ```java
  switch(expression){
      case value:
          //语句
          break;
      case value:
          //语句
          break;
      //可以有任何数量的case语句
      default://可选
          //语句
  }
  ```

- case标签必须为字符串常量或字面量

  **case穿透** ---> 要写**break**

## 2.4 循环

### 2.4.1 While 循环

- 最基本的循环

  ```java
  while(布尔表达式){
      //循环内容
  }
  ```

- 只要布尔表达式为true，循环就会一直执行下去

- 通过让表达式失效的方式来结束循环

- 循环条件一直为true就会造成死循环

### 2.4.2 DoWhile 循环

```java
do{
    
}while(布尔表达式);
```

- While 和 do...while的区别
  - while先判断后执行，do...while先执行后判断
  - do...while 循环至少会执行一次

### 2.4.3 For 循环

- 支持迭代，最有效，最灵活的循环结构

- 循环次数在执行前就确定

  ```java
  for(初始化;布尔表达式;更新){
      //代码语句
  }
  ```

- 最先执行初始化步骤

  可以声明一种类型，也可初始化一个或多个循环控制变量，也可以是空语句

- 再检测布尔表达式的值

  如果为true，循环体被执行，反之循环终止，开始执行循环体后面的语句

- 再次检测布尔表达式，循环执行上面的过程

#### 增强For循环

**遍历数组**

- 语法格式：

  ```java
  for(声明语句：表达式){
      //代码句子
  }
  ```

- 声明语句

  声明新的局部变量，该变量的类型必须和数组元素的类型匹配

  作用域限定在循环语句块其值与此时数组元素的值相等

- 表达式

  表达式是要访问的数组名，或者是返回值为数组的方法

## 2.5 break、continue、goto

### break

- 在任何循环语句的主体部分，均可以用break控制循环的流程

- break用于**强制退出循环**，不执行循环中剩余的语句
- break在switch语句中也适用

### continue

用于**中止某次循环过程**，即跳过循环体中尚未执行的语句，接着进行下一次是否执行循环的判定

### goto

- java中没有goto
- 在break和continue中有goto的影子：带标签的break和continue
- 标签指后面跟一个冒号的标识符，E.g: label:
- 对于java来说，唯一用到标签的地方是在循环语句之前，而唯一理由是：我们希望在其中嵌套另一个循环，由于break和continue关键字通常只中断当前循环，但若随同标签一起使用，他们就会中断到存在标签的地方

# 3. Java方法

## 3.1 定义

- java方法是语句的集合，在一起执行一个功能

  - 方法是解决一类问题的步骤的有序组合，是一段用来完成特定功能的代码片段
  - 方法包含于类或对象中
  - 方法在程序中被创建，在其他地方被引用

- 设计方法的原则：

  方法本意是功能块，就是实现某个功能的语句块的集合

  设计方法时，最好保持方法的原子性：一个方法只完成1个功能

- 方法包含一个方法头和一个方法体：

  ```java
  修饰符 返回值类型 方法名（参数类型 参数名）{
      ···
      方法体
      ···
      return 返回值；
  }
  ```

  - **修饰符**：

    可选的，决定方法被调用的方式，定义了方法的访问类型

  - **返回值类型**：

    方法可能会返回值

  - **方法名**：

    方法的实际名称，方法名和参数共同构成方法签名

  - **参数类型**：

    - 形式参数：在方法被调用时用于接收外界输入的数据
    - 实参：调用方法时实际传给方法的数据

    参数像是一个占位符

    当方法被调用时，传递值给参数，这个值被称为实参或者变量

    参数列表是指方法的参数类型、顺序和个数

    参数是可选的，方法可以不含任何参数

  - **方法体**：

    方法体包含具体语句，定义方法的功能

## 3.2 调用

- 格式：

  对象名.方法名(实参列表)

- java支持两种调用方法，根据方法是否返回值来选择

  - 当方法返回一个值：方法调用通常被当做一个值

    E.g：

    ```java
    int larger = max(30,40);
    ```

  - 如果方法返回值是void，方法调用一定是一条语句

    E.g:

    ```jav
    max();
    ```

## 3.3 重载

### 定义

在一个类中。有相同的函数名称，但形参不同

### 重载规则

- 方法名称必须相同
- 参数列表必须不同（个数不同或类型不同、参数排列不同）
- 方法的返回类型可以相同也可以不同
- 仅仅返回类型不同不足以构成方法的重载

### 实现理论

方法名称相同时，编译器会根据调用方法的参数个数、参数类型等去逐个匹配，已选择对应的方法，如果匹配失败，则编译器报错

## 3.4 命令行传递参数

当你希望**运行**一个程序**时**再给它**传递**消息，这要靠命令行参数给main()函数实现

```java
public class commandLine{
    public static void main(String[] args){
        for(int i=0;i<args.length;i++){
            System.out.println("args["+i+"]:"+args[i]);
        }
    }
}
```

实操练习：

先在类中写好代码：

```java
package com.javaStudy.week1.JavaMethod;

public class Demo03 {
    public static void main(String[] args) {
        for(int i=0;i<args.length;i++){//fori+tab
            System.out.println("args["+i+"]:"+args[i]);
        }
    }
}
```

然后在类的文件夹下打开cmd命令行：

1. 编译该类
2. cd../ 回到src层
3. 运行该类
4. 传递命令/字符串，运行

```
javac 类的地址.java
cd../ 直到回到src层的包为之
java 类的地址
java 类的地址 想要传递的信息或字符串
```

E.g:


```
D:\Java\IDEA\IDEA\SOSD\Week1\src\com\javaStudy\week1\JavaMethod>javac com.javaStudy.week1.JavaMethod.Demo03.java
D:\Java\IDEA\IDEA\SOSD\Week1\src\com\javaStudy\week1\JavaMethod>cd../
D:\Java\IDEA\IDEA\SOSD\Week1\src\com\javaStudy\week1>cd../
D:\Java\IDEA\IDEA\SOSD\Week1\src\com\javaStudy>cd../
D:\Java\IDEA\IDEA\SOSD\Week1\src\com>cd../
D:\Java\IDEA\IDEA\SOSD\Week1\src>java com.javaStudy.week1.JavaMethod.Demo03
D:\Java\IDEA\IDEA\SOSD\Week1\src>java com.javaStudy.week1.JavaMethod.Demo03 this is LinXX
结果：
args[0]:this
args[1]:is
args[2]:LinXX
```

### 可变参数

- 在方法声明中，在指定参数类型后加一个省略号(...)
- 一个方法中只能指定一个可变参数，它必须是方法的最后一个参数
- 任何普通的参数必须在它之前声名

## 3.5 递归

- 方法自己调用自己，就是递归

- 递归通常把一个大型复杂问题层层转化为一个与原问题相似的规模较小的问题来求解

- 递归的能力在于用有限的语句来定义对象的无限集合

- 递归的结构：

  递归头：什么时候不调用自身方法，即停止条件或**边界条件**，没有则会进入死循环，栈溢出

  递归体：什么时候需要调用自身方法以及调用的方式

- 递归思想

# 4. 数组

## 4.1 定义

- 数组是相同类型数据的有序集合
- 数组描述的是相同类型的若干个数组，按照一定的先后次序排列组合而成
- 其中，每个数据称作一个数组元素，每个数组元素可以通过一个下标来访问它们

### 4.1.1 声明与创建

- 首先必须声明数组变量，才能在程序中使用数组

  语法：

  ```java
  dataType[] arrayName;//首选方法
  dataType arrayName[];//效果相同
  ```

- java语言用**new**操作符来创建数组

  语法：

  ```java
  dataType[] arrayName = new dataType[arraySize];
  ```

- 数据的元素是通过索引访问的，数组索引**从0开始**

- 获取数组的长度：

  ```java
  array.length;
  ```

### 4.1.2 基本特点

- 其长度是确定的，数组一旦被创建，大小就不可改变
- 其元素必须是相同类型，不允许混合类型
- 数组中的元素可以是任何数据类型，包括基本类型和引用类型
- **数组变量属于引用类型**，数组也可以看成是对象，数组中的每个元素相当于该对象的成员变量
- 数组本身就是对象，java中对象是在堆中的，因此数组无论保存原始类型还是其他对象类型，**数组对象本身是在堆中的**

### 4.1.3 初始化

#### 静态初始化

```java
int[] a = {1,2,3};
Man[] mans = {new Man(1,1),new Man(2,2)}
```

#### 动态初始化

```java
int[] a = new int[2];
a[0] = 1;
a[1] = 2;
```

#### 默认初始化

数组是引用类型，它的元素相当于类的实例变量，因此数组一经分配空间，其中的每个元素也被按照实例变量同样的方式被隐式初始化

### 4.1.4 内存分析

- 堆

  存放new的对象和数组

  可以被所有的线程共享，不会存放别的对象引用

- 栈

  存放基本变量类型(会包含这个基本类型的具体数值)

  引用对象的变量(会存放这个引用在堆里面的具体地址)

- 方法区

  可以被所有线程共享

  包含了所有的class和static变量

<u>写代码画图分析内存</u>

### 4.1.5 下标越界

- 下标的合法区域：[0,length-1]，如果越界就会报错：

```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 
```

---

小结：

- 数组是相同数据类型的有序集合，数据类型可以是任意类型
- 数组也是对象，数组元素相当于对象的成员变量
- 数组长度是确定的，不可变的，如果越界，则报：ArrayIndexOutOfBounds

## 4.2 数组的使用

### 4.2.1 使用

- For循环
- For-Each循环
- 数组作方法入参
- 数组作返回值

### 4.2.2 多维数组

- 多维数组可以看成是数组的数组，比如二维数组就是一个特殊的一维数组，其每一个元素都是一个一维数组

- 二维数组

  ```java
  int a[][] = new int[2][5];
  ```

  以上二维数组a可以看成一个两行五列的数组
