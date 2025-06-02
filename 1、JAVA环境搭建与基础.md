[TOC]
# JAVA环境搭建与基础
## JAVA环境搭建
### Java的三个版本
1. **JavaSE**(Java Standard Edition):
  * 开发客户端应用程序平台。
  * vb,vc,delphi.powerbuilder
2. **JavaEE**:
  * 开发分布式企业级应用的平台。
  * 基于Internet环境的分布式软件: .NET平台中的ASP.NET
3. **JavaME**(Java  Micro Edition):
  * 开发电子产品为主的平台。 Android
### 大数据 (Hadoop): MapReduce+ HDFS 
### Java的运行环境
    源程序先被编译成bytecodes(字节码)文件，bytecodes文件再通过Java Virtual Machine(JavaVM)[JAVA虚拟机]解释执行
    一个Java源文件1.java被Compiler为1.class字节码文件，然后通过不同的虚拟机可以被解释执行为各种版本：Win32、UNIX、MacOS
### Java程序的开发环境

1.  java 2 SDK (Java software Development Kit):
    * http://java.sun.com 免费下载
    * **Javac**: compiler
    * **Java**: 启动JVM执行字节码文件
    * **Appletviewer**: Applet 程序浏览器
    * **Jar** : Java Archive 文件归档工具
2.  Java集成开发环境:**eclipse**
3.  JDK: Java Development Kit
    * 开发环境 [http://www.oracle.com/technetwork/java/index.html](http://www.oracle.com/technetwork/java/index.html) 免费下载
    * **Javac**: compiler
    * **Java**: 启动JVM执行字节码文件
4. JRE: Java Runtime Environment
    * 运行环境
    * 安装了JDK后，会自动安装JRE
###  Java程序类别

Java程序主要分为两大类（运行环境不同）：

* **Application (应用程序)**
    * **定义：** 独立的Java程序，可以在JVM上直接运行，无需浏览器。
    * **关键特点：**
        1.  必须包含一个 `main` 方法作为程序的入口点。
        2.  通常从 `main` 方法开始执行，并可以包含多个自定义类。
        3.  可以访问本地文件系统和网络资源。

* **Applet (小程序)**
    * **定义：** 小型Java程序，设计用于嵌入到网页中并在支持Java的浏览器中运行。
    * **关键特点：**
        1.  没有 `main` 方法。
        2.  其生命周期由浏览器或Applet Viewer管理（例如 `init()`, `start()`, `paint()`, `stop()`, `destroy()` 方法）。
        3.  受严格的安全沙箱限制，通常不能直接访问本地文件系统或执行某些敏感操作。
        4.  **注意：** Applet 技术在现代Web开发中已基本被淘汰，主要因为安全性和兼容性问题，以及HTML5等技术的兴起。
   
### Java开发环境的搭建

* 安装JDK
* 设置环境变量
    * (1) **JAVA_HOME**: java的安装目录
        * `c:\java1.6.0`
    * (2) **CLASSPATH**: 运行java程序所需要的类库
        * `c:\java1.6.0\lib\dt.jar;c:\java1.6.0\lib\tools.jar;`
        * `d:\save;`
    * (3) **PATH**: 运行java程序的命令所在的目录
        * `c:\java1.6.0\bin`

### Application (应用程序)

**例:** HelloWorld.java

1) 编辑HelloWorld.java

```java
/**
 * The HelloWorld class implements an application that
 * simply displays "Hello World!" to the standard output.
 */
public class HelloWorld {                      // <-- 主类：含有main()方法
    public static void main(String[] args) {   // <-- 程序执行的入口点
        System.out.println("Hello World!");    //display the string.
    } 
}
```
2. 编译HelloWorld.java生成字节码文件: HelloWorld.class
3. 运行Application应用程序
4. 结果: Hello World !

1. 检查计算机的环境变量：
==java_home= c:\jdk==    //用于指示 Java Development Kit (JDK) 的安装根目录。
==path=%path%;c:\jdk\bin==     //操作系统会按照这些路径的顺序查找可执行文件（如 .exe 文件、脚本等）。比如命令行输入java，javac，操作系统会遍历path变量
==Classpath=.; c:\jdk\lib\dt.jar; c:\jdk\lib\tools.jar;d:\save;== //告诉 JVM 在哪里查找 Java 类文件（.class 文件）和 JAR 文件
操作步骤：控制面板/系统/“高级”选项卡/环境变量

2. 编写一个Java Application应用程序，利用JDK软件包中的工具编译并运行，在屏幕上输出“Hello  World! ”。
步骤：
 1) 编辑HelloWorld.java: 
         在D:\Save目录中，编辑源文件HelloWorld.java (用记事本或editplus编辑)  
	    public class HelloWorld {
          public static void main(String[] args) {
            System.out.println("Hello World!"); //display the string.
         }
        }
 2) 在DOS命令窗口,编译HelloWorld.java：
    d:\save>javac  HelloWorld.java 
    生成字节码文件：HelloWorld.class
 3) 运行HelloWorld.class：
    D:\Save> java HelloWorld
    结果：Hello　World！`

**说明:** JVM只运行main方法中的语句。

### Applet (小程序): 运行在WWW浏览器上

**例:** HelloWorldApplet.java

1) 编辑HelloWorldApplet.java

```java
import java.applet.Applet;
import java.awt.Graphics;

public class HelloWorldApplet extends Applet { // <-- 主类: Applet类的子类
    public void paint(Graphics g) {
        g.drawString("Hello World!",50,50); // <-- 在屏幕上显示内容
    }
}
```
2. 编译HelloWorldApplet.java
 ```bash
d:\save>javac HelloWorldApplet.java
```
3. 编写一个HTML文件: HelloWorldApplet.html, 将HelloWorldApplet.class嵌入其中
```html
<html>
    <head>
        <title>hello world applet</title>
    </head>
    <body>
        <applet code="HelloWorldApplet.class"
                width=500
                height=500
                codebase=".">
        </applet>
    </body>
</html>
```
4. 用浏览器浏览HTML文件：HelloWorldApplet.html
5. 用appletviewer 浏览HTML文件：HelloWorldApplet.html
```bash
D:\save>appletviewer  HelloWorldApplet.html
      或 appletviewer -encoding UTF-8 HelloWorldApplet.html
```
**Notice: 关于classpath:**

**(1) 没有设置classpath:** java只能运行**当前目录**中的class文件

**(2) 设置了classpath:** java只能运行**classpath目录**下的class文件


### JAVA的基本特征
Sun公司的白皮书，Java的定义:

> “Java: A
> 1 Simple(简洁性),
> 2 object-oriented(面向对象),
> 3 distributed(分布式)
> 4 robust(健壮性),
> 5 architecture-neutral(结构中立)
> 6 secure(安全性),
> 7 portable(可移植性),
> 8 interpreted解释执行
> 9 high-performance(高性能),
> 10 multi-threaded(多线程)
> 11 dynamic(动态)
> language.”

### 面向对象程序设计的基本特征
面向对象程序设计（Object-Oriented Programming, **OOP**）是一种软件开发范式，它将数据和操作数据的方法封装在一起，形成**对象**。OOP 的核心思想是模拟现实世界，通过对象之间的交互来构建复杂的系统。

OOP 的基本特征通常被总结为以下四点，有时也会加上抽象性：
---
1. 封装 (Encapsulation)
**封装**是指将数据（属性）和操作数据的方法（行为）捆绑在一起，形成一个独立的单元——对象。同时，它还限制了对对象内部细节的直接访问，外部只能通过对象提供的公共接口来与对象进行交互。

* **优点：** 隐藏了实现细节，降低了系统的复杂性；提高了代码的模块化和可维护性；增强了数据的安全性，防止外部随意修改数据。
---
2. 继承 (Inheritance)
**继承**允许一个类（子类或派生类）继承另一个类（父类或基类）的属性和方法。子类可以重用父类的代码，并可以在此基础上添加新的功能或修改现有功能。

* **优点：** 实现了代码的重用，减少了冗余；建立了类之间的层次结构，有助于更好地组织和理解代码；是实现多态的前提。
---
3. 多态 (Polymorphism)
**多态**意味着允许使用一个共同的接口来表示不同类的对象。简单来说，就是同一个方法在不同的对象上可以有不同的行为。多态主要通过**方法重载**（Overloading）和**方法重写**（Overriding）实现。

* **方法重载：** 同一个类中，多个方法名相同但参数列表不同。
* **方法重写：** 子类重新定义父类中已有的方法，通常用于实现子类特有的行为。
* **优点：** 提高了代码的灵活性和可扩展性；简化了代码，降低了耦合度。
---
4. 抽象 (Abstraction)
**抽象**是指从具体的实现细节中抽离出共同的、本质的特征，并以简洁的方式表示出来。在 OOP 中，抽象通常通过**抽象类**和**接口**来实现。它关注的是“做什么”，而不是“如何做”。

* **抽象类：** 不能被实例化的类，可以包含抽象方法（只有声明没有实现）和具体方法。子类必须实现抽象方法。
* **接口：** 一组抽象方法的集合，定义了类应该遵循的行为规范，不包含任何实现细节。
* **优点：** 降低了系统的复杂性，有助于设计师和开发者关注核心功能；提供了更高层次的视图，便于理解和设计。
---
1. 聚合/关联 (Association/Aggregation/Composition) - 有时也被提及
虽然不总是被列为四大基本特征之一，但**聚合**和**组合**是描述对象之间**关系**的重要概念，它们都属于更广泛的**关联**关系。

* **关联 (Association):** 对象之间的一种泛化关系。
* **聚合 (Aggregation):** 表示一种“has-a”的关系，部分可以独立于整体存在。例如，一个汽车可以有多个轮子，但轮子可以独立于汽车存在。
* **组合 (Composition):** 表示一种更强的“has-a”关系，部分是整体不可或缺的一部分，生命周期与整体绑定。例如，一个人有心脏，心脏不能独立于人存在。

理解并熟练运用这些基本特征是掌握面向对象程序设计的关键，它们能够帮助我们构建出更健壮、可维护和可扩展的软件系统。

### 一个简单的JAVA程序
```java
public class BasicDemo {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i <= 10; i++) {
            sum += i;
        }
        System.out.println("Sum = " + sum);
    }
}
```
1. 变量、常量、数据类型、操作符、控制流程语句
2. java 无全局变量
3. java 不支持 goto 语句
4. java 不支持指针，但通过引用实现了指针的功能
5. 内存管理：自动分配和释放内存 (垃圾回收)
## 变量与数据类型
### 数据类型

-   基本数据类型
    -   数值类型
        -   整数类型
            -   字节型: Byte
            -   短整型: short
            -   整型: int
            -   长整型: long
        -   浮点类型
            -   单精度浮点型: float
            -   双精度浮点型: double
    -   字符类型: char
    -   布尔类型: boolean
-   引用数据类型
    -   类: class
    -   接口: interface
    -   数组(array)

### 基本数据类型

| 类别     | 类型    | 占用二进制位数      | 说明           | 默认值    |
| :------- | :------ | :------------------ | :------------- | :-------- |
| 整型     | byte    | 8bit                | 字节型整数     | 0         |
| 整型     | short   | 16bit               | 短整数         | 0         |
| 整型     | int     | 32bit               | 整数           | 0         |
| 整型     | long    | 64bit               | 长整数         | 0         |
| 浮点数   | float   | 32bit               | 单精度浮点数   | 0.0f      |
| 浮点数   | double  | 64bit               | 双精度浮点数   | 0.0       |
| 其它类型 | char    | 16bit Unicode字符集 | 单字符         | `\u0000`  |
| 其它类型 | boolean | true或false         | 布尔值         | false     |
### notice:

1.  数值类型大小固定，没有无符号整数。

2.  字符型采用Unicode编码(国际统一标准编码)，二个字节。
    * 范围：`0` - `(2^16 - 1)` (即 `0` - `65535`)，总共 `65536` 个值，能表示人类语言所有字符集。
    * Java源程序采用Unicode编码。
    * 在ASCII编码环境中输入Unicode字符的格式为：`\uXXXX`
        * 转义符：`\u`
        * `XXXX`：代表4个十六进制数字
    * `\uXXXX` 表示十六进制数值 `XXXX` 所对应的Unicode字符编码。
    * **Example:** `char c = '\u5f20';` 等价于 `char c = '张';`

3.  `boolean` 类型的值不是一个整数类型的值。
    * 只为 `true`、`false`。
    * **例:**
        * `boolean isVisible = true;`
        * `boolean isVisible = 1;` (编译出错)
  
### 引用数据类型：类(class)、接口(interface)和数组(array)

    引用类型的值是**对象的一个引用**。
    这类似于指针。

**例：**
```java
Account Tom = new Account("Tom");
Account Rose = new Account("Rose");
```
### 变量的作用域

1.  **成员变量**的作用域：整个类
2.  **方法参数**的作用域：整个方法
3.  **局部变量**的作用域：定义开始至块结束

```java
public class Person{
    int age;
    String name;
    public void setAge(int age2){
        age=age2; // 这里的age是成员变量
        {
            int age; // 这是块内的局部变量age
            age=2;   // 这里赋值给的是块内的局部变量age
        }
    }
}
```
### 变量的初始化：

1.  **整形**
    ```java
    int age=24;
    long l=1234L;
    byte b=34;
    short s=222;
    ```
2.  **实型**
    ```java
    float f=234.5F; // 浮点数常量默认为double
    ```
3.  **其它类型**
    ```java
    double d=-1.5E-8; 
    double s=12.5;
    char c='a',h='好';
    boolean isVisible=true;
    String s="hello world!";
    ```

### final变量:
数值不能在初始化之后进行改变，类似于常量。
例: 
```java
final int age=12;
```

## 运算符
###  运算符

1.  **单目运算符**：只有一个运算对象的运算符。`++`
    例: `i++`
2.  **双目运算符**：需要两个运算对象的运算符。`+`
    例: `a+b`
3.  **三目运算符**：需要三个运算对象的运算符。`?:`
    例: `x>y?x:y` 等价于 `max(x,y)`
4.  **前缀运算符**：运算符出现在它的运算对象之前。
    例: `++i`
5.  **后缀运算符**：运算符出现在它的运算对象之后。
    例: `i++`
6.  **中缀运算符**：运算符出现在它的运算对象之间。
    例: `a+b`, `x>y?x:y`

### 运算符种类

* 算术运算符、
* 关系和条件运算符、
* 移位和逻辑运算符、
* 赋值运算符
* 其他的运算符

### 算术运算符

| 类别       | 运算符 | 描述 |
| :--------- | :----- | :--- |
| 双目运算符 | `+`    | 加   |
|            | `-`    | 减   |
|            | `*`    | 乘   |
|            | `/`    | 除   |
|            | `%`    | 取模 |
| 单目运算符 | `+`    | 正   |
|            | `-`    | 负   |
|            | `++`   | 自增 |
|            | `--`   | 自减 |

### 运算结果的数据类型 (运算对象类型不同时)：

1.  如果两个运算对象的类型都是整数类型(`byte`, `short`, `int`, `long`)或者都是浮点类型(`float`, `double`)，则计算结果为**占位较多**的那种类型。
2.  如果一个运算对象的类型属于整数类型，另一个运算对象的类型为浮点，则计算结果为**浮点类型**。
3.  如果一个运算对象的类型属于字符类型(`char`)，另一个运算对象为数值类型，则计算结果为**数值类型**。
    例: `'a'+1` 结果为 `98` (因为 'a' 的 ASCII 值是 97)
4.  `String`类型 + 基本类型: `String`类型
    例: `"name"+23 = "name23"`
5.  被0除: 异常 `ArithmeticException`
6.  `整数/整数`: 整数类型
    `整数/浮点`: 浮点类型

### 赋值运算符

| 运算符  | 用法         | 描述           |
| :----- | :----------- | :------------- |
| `=`    | `X=3`        | 简单赋值        |
| `+=`   | `op1+=op2`   | `op1=op1+op2`  |
| `-=`   | `op1-=op2`   | `op1=op1-op2`  |
| `*=`   | `op1*=op2`   | `op1=op1*op2`  |
| `/=`   | `op1/=op2`   | `op1=op1/op2`  |
| `%=`   | `op1%=op2`   | `op1=op1%op2`  |
| `&=`   | `op1&=op2`   | `op1=op1&op2`  |
| `\|=`   | `op1\|=op2`   | `op1=op1\|op2`   |
| `^=`   | `op1^=op2`   | `op1=op1^op2`  |
| `<<=`  | `op1<<=op2`  | `op1=op1<<op2` |
| `>>=`  | `op1>>=op2`  | `op1=op1>>op2` |
| `>>>=` | `op1>>>=op2` | `op1=op1>>>op2`|

1.  **赋值操作的类型转换**(T1为赋值左侧的类型，T2为赋值右侧的类型：`T1=T2`)：
    1.  `T1`与`T2`类型相同，不转换。
    2.  `T1`为`boolean`类型，则`T2`必须为`boolean`。
    3.  如果`T1`与`T2`类型不相同且不是`boolean`类型，则按照占据二进制位数较多的数据类型的原则进行转换。

### 关系运算符：结果类型为`boolean`

| 运算符 | 用法      | 返回true的情况   |
| :----- | :-------- | :--------------- |
| `>`    | `op1>op2` | `op1`大于`op2`   |
| `>=`   | `op1>=op2`| `op1`大于等于`op2`|
| `<`    | `op1<op2` | `op1`小于`op2`   |
| `<=`   | `op1<=op2`| `op1`小于等于`op2`|
| `==`   | `op1==op2`| `op1`等于`op2`   |
| `!=`   | `op1!=op2`| `op1`不等于`op2` |

###  逻辑运算符：结果类型为`boolean`

| 运算符   | 用法        | 返回true的情况       |
| :------- | :---------- | :------------------- |
| `&&` 与  | `op1 && op2`| `op1`和`op2`都是`true` |
| `\|\|` 或| `op1\|\|op2`| `op1`或者`op2`是`true` |
| `!` 非   | `!op1`      | `op1`为`false`       |
| `^` 异或 | `op1^op2`   | `op1`和`op2`逻辑值不相同 |
####  位运算符

| 运算符 | 用法      | 操作           |
| :----- | :-------- | :------------- |
| `&`    | `op1 & op2` | 按位与         |
| `\|`    | `op1 \| op2` | 按位或         |
| `^`    | `op1 ^ op2` | 按位异或       |
| `~`    | `~op2`    | 按位求反       |
| `>>`   | `op1 >> op2` | 将 `op1` 右移 `op2` 个位 |
| `<<`   | `op1 << op2` | 将 `op1` 左移 `op2` 个位 |
| `>>>`  | `op1 >>> op2` | 将 `op1` 右移 `op2` 个位 (无符号的) |

**示例：**`byte a=106, b=7, flags=0x0f;`
求 `a & flags`, `a | flags`, `~a`

1) `a`: `01101010`
   `flags`: `00001111`

2) `a & flags = 10` (二进制: `00001010`)
   `a | flags = 111` (二进制: `01101111`)
   `~a =`           (二进制补码: `10010101`)

**计算机中的数据都是用补码表示**

已知补码,求原码:
补码为负数,求原码: 补码反 + 1
补码为正数,求原码: 补码

补码: `10010101`
原码: `-107` (`11101011`)

**在计算机科学中，从补码到原码的标准且清晰的方法就是：**

1.  如果补码是正数 (最高位是 0)，则原码就是其本身。
2.  如果补码是负数 (最高位是 1)：
    * **方法 A (推荐，逆运算):** 先将补码减 1，然后对结果的数值位（除了符号位）取反。
    * **方法 B (等价但可能引起歧义):** 先对补码（包括符号位）取反，然后加 1。这个操作得到的是对应正数的补码（也就是原码），然后你需要手动将符号位变为 1 才能得到负数的原码。

**让我们用方法 B 验证 `10010101` (一个负数的补码)：**

* 对 `10010101` 所有位取反：`01101010`
* 对 `01101010` 加 1：`01101011`
* 这个 `01101011` 是 `107` 的补码（也是原码）。
* 所以，原来的负数就是 `-107`。其原码就是将 `107` 的原码的符号位从 `0` 改成 `1`，即 `11101011`。

**例：**`byte a=10, b=7, c=-1, d=27, e=-50;`
求 `a<<1`, `b<<3`, `c<<2`, `a>>1`, `d>>3`, `e>>2`, `e>>>2`

1) 二进制表示（假设为8位 `byte` 类型）：
   `a`: `00001010` (10)
   `b`: `00000111` (7)
   `c`: `11111111` (-1 的补码)
   `d`: `00011011` (27)
   `e`: `11001110` (-50 的补码)
2) 位移运算结果：

* `a<<1` => `(00001010)₂ << 1` => `(00010100)₂`
    结果 `20` : `10 * 2¹`。

* `b<<3` => `(00000111)₂ << 3` => `(00111000)₂`
    结果 `56` : `7 * 2³`。

* `c<<2` => `(11111111)₂ << 2` => `(11111100)₂`
    结果 `-4` : `-1 * 2²`。

* `a>>1` => `(00001010)₂ >> 1` => `(00000101)₂`
    结果 `5` : `10 / 2¹`。

* `d>>3` => `(00011011)₂ >> 3` => `(00000011)₂`
    结果 `3` : `27 / 2³`。

* `e>>2` => `(11001110)₂ >> 2` => `(11110011)₂`
    结果 `-13` : `-50 / 2²`。

* `e>>>2` => `(11001110)₂ >>> 2` => `(00110011)₂`
    结果 `51` : `206 / 2²`。

###  其它运算符

1.  `?:` 运算符 `op1 ? op2 : op3;`
    示例：`(x < 10) ? x + 10 : x;`

2.  `[]` 运算符: 数组
    示例：`int[] a = new int[3];`

3.  `(数据类型)`: 强制类型转换
    示例：`int age = (int)32.4;`

4.  `new`: 创建一个类对象或数组。
    示例：`Account Tom = new Account();`
    `float[2] f = new float[2];` (此处 `float[2]` 在Java中通常写作 `float[] f = new float[2];`)

5.  `.` 点运算符: 访问对象或者类的成员方法或变量。
    示例：`Tom.userName = "tom"; Tom.withdraw(100);`

6.  `instanceof`:
    `op1 instanceof op2` : `op1` 对象是否是 `op2` 类的实例。
    示例：`Tom instanceof Account;`

### 运算符的优先级与结合性

| 类别             | 运算符                                | 结合性 |
| :--------------- | :------------------------------------ | :----- |
| postfix operators | `[]` `.` `(params)` `expr++` `expr--` | 左     |
| unary operators  | `++expr` `--expr` `+expr` `-expr` `~` `!` | 右     |
| creation or cast | `new` `(type)expr`                    |        |
| multiplicative   | `*` `/` `%`                           |        |
| additive         | `+` `-`                               |        |
| shift            | `<<` `>>` `>>>`                       |        |
| relational       | `<` `>` `<=` `>=` `instanceof`        |        |
| equality         | `==` `!=`                             |        |
| bitwise AND      | `&`                                   | 左     |
| bitwise exclusive OR | `^`                                   |        |
| bitwise inclusive OR | `|`                                   |        |
| logical AND      | `&&`                                  |        |
| logical OR       | `||`                                  |        |
| conditional      | `?:`                                  |        |
| assignment       | `=` `+=` `-=` `*=` `/=` `%=` `&=` `^=` `\|=` `<<=` `>>=` `>>>=` | 右     |
## 流程控制语句

顺序语句、分支语句、循环语句

### 空语句

`;` : 不进行任何操作。

###  标号语句

标识符: 配合 `break` 和 `continue` 语句
例如 `here:`

### 表达式语句 (在表达式后加`;`)

`a=10;`

###  复合语句 (块语句) : 一组语句用一对大括号封装起来。

```java
x=2;
y=4;
{ // 块语句开始
    int z;
    z=x;
    x=y;
    y=z;
} // 块语句结束
```
### if-then-else语句
`else` 与最近的 `if` 相匹配：

例：

```java
if (a > b) {
    if (b > c) {
        System.out.println("a>c");
    } else { // 这个 else 与最近的 if (b > c) 匹配
        System.out.println("b<c");
    }
}
```
### 2.8.7 `switch` 语句

```java
switch (expression) {
    case value_1:
        statements_1;
        // break; // 通常会有 break; 来防止穿透
    case value_2:
        statements_2;
        // break;
    ...
    case value_n-1:
        statements_n-1;
        // break;
    default:
        statements_n;
        // break; // default 块通常也建议加上 break;
}
```
``` java
switch (expression){
      case value_1:    statements_1;   break;
      case value_2:    statements_2;   break;
                     …
      case value_n-1: statements_n-1;break;
      default:             statements_n;  break;
     }
```
### while语句
``` java
while(expression)
    statement;
```
### do循环语句
```java
do{
    statement;
}while(expression);
```
### for循环语句
```java
for(initialization; expression;iteration)
    statement;
```
### break语句：应用于switch和循环语句
格式1：break;
格式2：break identifier;

**例**：判断数值number是否为素数。
```java
public boolean isPrime(int number){
    boolean prime=true;
    int limit=(int)Math.ceil(Math.sqrt(number));
    for(int i=2;i<limit;i++){
        if(number%i==0){
            prime=false;
            break;
        }
    }
    return prime;
}
```
**例**
例:
```java
for(int i=0;i<count;i++){
    ...
    for(int j=0;j<count;j++){
        ...
        for(int k=0;k<count;k++){
            ...
            break outside;
            ...
        }
    }
    ...
}
outside;
```
### continue语句:结束本次循环，转下一次循环
格式1：continue;
格式2：continue identifier;

例：显示1-1000内被3整除的整数。
```java
for(int i=1;i<=1000;i++){
    if(i%3!=0) continue;
    System.out.println(i);
}
```
**Notice:**
1 在while循环语句内，转去计算while语句括号中的逻辑表达式。
2 在do循环语句内，转去计算while后面的逻辑表达式。
3 在for循环语句内，去计算iteration语句，再计算expression逻辑表达式。

### return语句:终止方法的执行，并返回到调用者的位置
格式1：return; //返回void类型
格式2：return expression;

例:
```java
void printError(){
    System.out.println("Error");
    return;
}

public static long abs(long a){
    return (a<0)?-a:a;
}
```

## 数组
### 一维数组的声明与创建
1. **数组的声明**
格式：数据类型  arrayName[];
或：数据类型[] arrayName;
例：`int age[];`
`String[] name;`
`int a[3]; //编译出错。`
`int b[2]=new int[2]; //编译出错。`
2. **数组的创建**
格式：`new` 数据类型`[number];`
例：`age=new int[100];`
`name=new String[10];`
`int[] salary=new int[10];`
每个数组元素的初始值为默认值
int :0 float:0.0f char: `\u0000`; boolean:false;引用:null

### 一维数组的初始化
例：`int intArray[] = {10,20,30,40,50,60,70,80,90,100}`
`String[] name={"zhang","wang","li","zhao"}`
### 一维数组元素的访问
格式：数组名[下标]
例：`name[0]`、`intArray[4]`
notice:数组元素下标从0开始

数组长度：`数组名.length;`
例：`name.length;`
例：打印数组所有元素
```java
for(int i=0;i<=name.length-1;i++){
    System.out.println(name[i]);
}
```
### 一维数组的复制
1.**引用复制**
例：
```java
int first_Array[]={10,20,30,40,50,60};
int second_Array[];
second_Array=first_Array;
```
2. **arraycopy() 方法复制**
void arraycopy(object src, int srcPos, object dest, int destPos, int length)

**例**:
```Java
int[] array_src={5,10,15,20,25,30,35,40,45,50};
int[] array_dest=new int[10];
System.arraycopy(array_src,0,array_dest,0,10); // Added System. for completeness
```

### 二维数组的声明与创建
**1. 二维数组的声明**
格式：数据类型 数组名[][];
或：数据类型[][] 数组名;
例：`int age[][];`
`String[][] name;`
`int a[3][4]; //编译出错。`
`int b[2][3]=new int[2][3]; //编译出错。`

**2. 二维数组的创建**
格式：`new` 数据类型`[number1][number2];`
每个数组元素的初始值为默认值
例：`age=new int[2][3];`
`name=new String[10][20];`
例：`int[][] salary=new int[10][30];`

### 二维数组的初始化
例：`int[][] age= {{1,2,3},{4,5,6},{7,8,9}} ;`

The diagram shows a 3x3 grid representing the `age` array:
| 1 | 2 | 3 |  <-- age[0][2] (pointing to 3)
| 4 | 5 | 6 |  <-- age[1][1] (pointing to 5)
| 7 | 8 | 9 |  <-- age[2][2]数组 (pointing to 9)

### 二维数组元素的访问
格式：数组名[下标表达式1][下标表达式2]
例：`name[0][2]`、`intArray[1][3];`
```java
int[][] arr=new int[2][3];
for(int i=0;i<=1;i++){
    for(int j=0;j<=2;j++){
        arr[i][j]=i+j;
    }
}
```
### 数组长度 数组名.length
```java
int[][]  arr=new int[2][3];
for(int i=0;i<=arr.length-1;i++){
     for(int j=0;j<=arr[i].length-1;j++){
         arr[i][j]=i+j;
      }
}
```
## 字符串String:类

###  字符串直接量:双引号
“this is a String!”

### String类对象:声明、创建、初始化和引用
声明: `String 字符串变量;`
创建:` 字符串变量 = string_value;`  // string_value为字符串直接量、null、String类对象。
**例**:
```java
String s1,s2,s3;
s1="this is a string";
s2=null;
s3=s1;
String s4="this is a string";
```
**Notice:**
在java语言中,字符串直接量中的每个字符占用两个字节。Unicode
String类对象初始值为null;
## 基本输入输出
### 字符界面的基本输入输出(借助System类中的in/out成员变量)
**例1：**
接收用户通过键盘输入的一个字符，并将其输出
```java
import java.io.*;
public class SimpleCharInOut{
	public static void main(String[] args) 
	{
            char ch='\u0000';
            System.out.println("enter a character please:");
		try{
			ch=(char)System.in.read();
		}catch(IOException e){
			System.out.println("error");
		 }
    System.out.println("You have entered  a character:"+ch);
	}
}
```
1.  `System` 是一个系统类：
    支持键盘输入和屏幕显示的成员变量和成员方法。

2.  `out` 是 `System` 类的一个静态成员变量：标准输出流。
    `print()` 是 `out` 的一个成员方法。

3.  `in` 是 `System` 类的一个静态成员变量：标准输入流。
    `read()` 是 `in` 的一个成员方法，其功能是从输入流中读取一个字节的数据，并返回输入字符所对应的 ASCII 值。

4.  正常返回的整形数值界于 `0-255`，若读取到输入流的末尾将返回 `-1`，再经强制类型转换后再赋给相应变量 `ch`。

5.  当 `read` 方法的返回值不在 `-1~255` 内，说明出现异常，JVM 会抛出 `IOException` 异常。

**例2：**
接收用户通过键盘输入的一行字符，并将其输出
```java
import java.io.*;
public class ApplicationLineInOut{
   public static void main(String[] args){
         String string="";
	System.out.println("enter a string please:");
	     try{			
                         BufferedReader br=new BufferedReader(  
                                       new InputStreamReader(System.in));
		     string=br.readLine();			 
		}catch(IOException e){	                   
                         System.out.println("error");
                       }
	System.out.println("You have entered  a string:"+string);
	}
}
```
1.  `BufferedReader` 是一个输入缓冲区类，它提供了读取文本行的功能。

2.  `BufferedReader` 的缓冲区对应标准输入流 `System.in`，但没有指定缓冲区的大小，使用默认值。

3.  `readLine()` 是 `BufferedReader` 类的一个方法，其功能是从缓冲区中读取一行文本字符，并以 `String` 类型返回。

**如何接收整数？**
字符串转换成整数：`Integer.parseInt(String)`