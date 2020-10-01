# 大纲

## 一个简单的Java应用程序

```java
public class FirstSample {
	public static void main(String[] args) {
		System.out.println("Hello, world!");
	}
}
```

关键字`public`: 访问修饰符（access modifier），控制程序其他部分对这段代码的访问级别。

关键字`class`: 

`FirstSample`: 类名。大写字母开头。源代码文件名需要和公有类名相同。

main方法：Java虚拟机从指定类的main方法开始执行。

语句: 调用`System.out`对象的`println`方法，输入参数是一个字符串



## 注释

```java
// 一种注释

/* 另一种注释 */

/**
 * 第三种注释，可以用来自动生成文档
 * @version 1.01 2020-02-20
 * @author Tom
 */
```

## 数据类型

Java是强类型语言，变量必须有类型。

基本类型(primitive type): 整型、浮点型、字符型、布尔型

### 整型

| 类型  | 存储需求 | 取值范围         |
| ----- | -------- | ---------------- |
| int   | 4字节    | -2^31 ~ 2^31 - 1 |
| short | 2字节    | -2^15 ~ 2^15 - 1 |
| long  | 8字节    | -2^63 ~ 2^63 - 1 |
| byte  | 1字节    | -2^8 ~ 2^8 - 1   |

### 浮点型

| 类型   | 存储需求 | 有效位数 |
| ------ | -------- | -------- |
| float  | 4字节    | 6~7位    |
| double | 2字节    | 15位     |

一般情况下使用double类型。

需要快速处理或存储大量数据时，使用float类型。

三个特殊浮点数值：

+ 正无穷大
+ 负无穷大
+ `NaN` (不是一个数字)

### char类型

表示单个字符，通常用来表示字符常量。

如'A'。

建议不要在程序中使用char类型。

### boolean类型

值: true或false。

用来判断逻辑条件。

整型值和布尔值直接不能相互转换。

## 变量

每个变量都具有一个类型（type）。

变量声明：

```java
double salary;
int vocatinDays;
long earthPopulation;
boolean done;
```

变量名对大小写敏感。

### 变量初始化

```java
int vocationDays;
vocationDays = 12;
```

或者

```java
int vocationDays = 12;
```

不能使用未初始化的变量。

### 常量

利用final关键字声明常量。

```java
final double CM_PER_INCH = 2.54;
```

常量只能被赋值一次，赋值后不能更改。

## 运算符

算术运算符：+， -， *， /，%

除法：

+ 参与/运算的两个操作数：都是整数，表示整数除法；否则表示浮点除法
+ 整数除0产生异常；浮点数除0得到无穷大或NaN结果。

### 自增与自减运算符

```java
int n = 12;
n++;  // 自增运算
n--;  // 自减运算
```

前缀与后缀方式：

```java
int m = 7;
int n = 7;
int a = 2 * ++m; // a为16，m为8
int b = 2 * n++; // b为14，n为8
```

### 关系运算符

==， !=, <, >, <=, >=

&&, ||, !

### 位运算符

& 与

| 或

^ 异或

~ 非

\>> 右移，符号位填充高位

\>>> 右移，0填充高位

<< 左移

### 数学函数与常量

求平方根

```java
double x = 4;
double y = Math.sqrt(x);
System.out.println(y);
```

幂运算

```java
double y = Math.pow(x, a);
```

常量

`Math.PI`

### 数值类型之间的转换

二元运算时先转换成同一类型再进行运算。

转换规则：

+ 其中一个操作数是double类型，另一个操作数转换为double类型；
+ 否则，其中一个操作数是float类型，另一个操作数转换为float类型；
+ 否则，其中一个操作数是long类型，另一个操作数转换为long类型；
+ 否则，两个操作数都被转为int类型

```java
byte a = 127;
byte b = 127;
int c = a + b;
System.out.println(c);
```

### 强制类型转换

cast

```java
double x = 9.997;
int nx = (int)x; // 强制转换将浮点数的小数部分截断
```

舍入运算，采用`Math.round`方法：

```java
double x = 9.997;
int nx = (int)Math.round(x); // Math.round返回的是long类型，仍然需要强制转换为int类型
```

### 括号与运算符优先级

| Operators            | Precedence                               |
| -------------------- | ---------------------------------------- |
| postfix              | `*expr*++ *expr*--`                      |
| unary                | `++*expr* --*expr* +*expr* -*expr* ~ !`  |
| multiplicative       | `* / %`                                  |
| additive             | `+ -`                                    |
| shift                | `<< >> >>>`                              |
| relational           | `< > <= >= instanceof`                   |
| equality             | `== !=`                                  |
| bitwise AND          | `&`                                      |
| bitwise exclusive OR | `^`                                      |
| bitwise inclusive OR | `|`                                      |
| logical AND          | `&&`                                     |
| logical OR           | `||`                                     |
| ternary              | `? :`                                    |
| assignment           | `= += -= *= /= %= &= ^= |= <<= >>= >>>=` |

来源： https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html 

## 字符串

Java字符串是Unicode字符序列。

Java没有内置的字符串类型，提供了String类。

```java
String e = "";
String greeting = "Hello";
```

### 子串

String类的substring方法:

```java
String greeting = "Hello";
String s = greeting.substring(0, 3);
```

结果是`Hel`

### 拼接

使用+号拼接:

```java
String greeting = "Hello";
String name = " John";
String s = greeting + name;
System.out.println(s);
```

输出结果：`Hello John`



字符串与非字符串拼接时，后者被转换为字符串:

```java
String name = " John";
int age = 23;
String s = name + age;
System.out.println(s);
```

输出结果：` John23`

### 不可变字符串

String类没有提供修改字符串的方法

String类对象称为不可变字符串

### 检测字符串是否相等

使用equals方法:

```java
s.equals(t)
```

s或t可以是字符串常量或变量:

```java
"Hello".equals(greeting)
```

不能使用==判断两个字符串是否相等!它只检测两个字符串是否在同一位置

### 构建字符串

每次拼接字符串都产生一个新的String对象，效率低。

多次拼接构建字符串可以采用StringBuilder类。

```java
StringBuilder builder = new StringBuilder(); // 创建构造器
builder.append("John is "); // 拼接字符串常量
builder.append('a');        // 拼接单个字符
String description = " good boy.";
builder.append(description);// 拼接字符串变量 
String s = builder.toString(); // 转换成字符串

System.out.println(s);
```

## 输入输出

### 读取输入

构造Scanner对象，并与System.in关联

```java
Scanner in = new Scanner(System.in);
```

使用nextLine方法读取一行:

```java
System.out.println("What's your name?");
String name = in.nextLine();
```

使用next方法读取一个单词:

```java
System.out.println("Are you a boy or a girl?");
String gender = in.next();
```

使用nextInt读取一个整数，使用nextDouble读取一个浮点数：

```java
System.out.println("How old are you?");
int age = in.nextInt();
```

完整代码：

```java
Scanner in = new Scanner(System.in);

// read one line
System.out.println("What's your name?");
String name = in.nextLine();

// read one word
System.out.println("Are you a boy or a girl?");
String gender = in.next();

// read one integer
System.out.println("How old are you?");
int age = in.nextInt();

System.out.println("Hello, " + name + ", you are a " + age + " year's old " + gender);
```

### 格式化输出

printf方法:

```java
double x = 10000/3.0;
System.out.printf("%8.2f", x);
```

输出结果：`3333.33`

| Converter | Flag | Explanation                                                  |
| --------- | ---- | ------------------------------------------------------------ |
| d         |      | A decimal integer.                                           |
| f         |      | A float.                                                     |
| n         |      | A new line character appropriate to the platform running the application. You should always use `%n`, rather than `\n`. |
| tB        |      | A date & time conversion—locale-specific full name of month. |
| td, te    |      | A date & time conversion—2-digit day of month. td has leading zeroes as needed, te does not. |
| ty, tY    |      | A date & time conversion—ty = 2-digit year, tY = 4-digit year. |
| tl        |      | A date & time conversion—hour in 12-hour clock.              |
| tM        |      | A date & time conversion—minutes in 2 digits, with leading zeroes as necessary. |
| tp        |      | A date & time conversion—locale-specific am/pm (lower case). |
| tm        |      | A date & time conversion—months in 2 digits, with leading zeroes as necessary. |
| tD        |      | A date & time conversion—date as %tm%td%ty                   |
|           | 08   | Eight characters in width, with leading zeroes as necessary. |
|           | +    | Includes sign, whether positive or negative.                 |
|           | ,    | Includes locale-specific grouping characters.                |
|           | -    | Left-justified..                                             |
|           | .3   | Three places after decimal point.                            |
|           | 10.3 | Ten characters in width, right justified, with three places after decimal point. |

来源： https://docs.oracle.com/javase/tutorial/java/data/numberformat.html 



可以用静态String.format方法创建格式化字符串：

```java
String name = "John";
int age = 24;
String message = String.format("Hello, %s. You are %d years old", name, age);
System.out.println(message);
```



### 文件输入输出

读取文件，用File对象构造一个Scanner对象:

```java
Scanner in = new Scanner(new File("file.txt"));
```

就可以采用Scanner方法进行读取



写入文件，构造PrintWriter对象，以文件名为参数:

```java
PrintWriter out = new PrintWriter("text.txt");
out.println("Hello, my name is Jessica.");
out.println("I am a 24 years old girl.");
out.close();
```

## 控制流程

### 块作用域

块(block)是指由花括号括起来的若干条java语句。

块确定了变量的作用域。

块可以嵌套。

```java
public static void main(String[] args) 
{
    int n;
    {
        int k;
    } // k只在括号内能被访问到
}
```

不能在嵌套的两个块中声明同名的变量。

```java
public static void main(String[] args) 
{
    int n;
    {
        int k;
        int n; // 报错： Duplicate local variable n
    } 
}
```

### 条件语句

格式：

`if (condition) statement`

或

```
if (condition)
{
	statement1
	statement2
	...
}
```

例子：

```java
if (yourSales >= target)
{
    performance = "Satisfactory";
    bonus = 100;
}
```



if-else条件：

`if (condition) statement1 else statement2`

例子：

```java
if (yourSales >= target)
{
    performance = "Satisfactory";
    bonus = 100;
}
else
{
    performance = "Unsatisfactory";
    bonus = 0;
}
```



if-else if-...-else条件：

例子：

```java
if (yourSales >= 2*target)
{
    performance = "Excellent";
    bonus = 1000;
}
else if (yourSales >= 1.5*target)
{
    performance = "Fine";
    bonus = 500;
}
else if (yourSales >= target)
{
    performance = "Satisfactory";
    bonus = 100;
}
else
{
    performance = "Unsatisfactory";
    bonus = 0;
}
```

### 循环

while循环：

`while (condition) statement`

例子：

```java
while (balance < goal)
{
    balance += payment;
    double interest = balance * intetrestRate / 100;
    balance += interest;
    years++;
}
System.out.println("years: " + years);
```



先执行语句，再检查条件，可以用do-while循环：

`do statement while (condition);`

例子：

```java
do
{
    balance += payment;
    double interest = balance * intetrestRate / 100;
    balance += interest;
    years++;
    
    // ask if ready to retire and get input
}
while(input.equals("N"));
```

### for循环

```
for (int i = 1; i <= 10; i++)
{
	System.out.println(i);
}
```

注意，for语句内部定义的循环变量，不能在循环体之外使用

### 多重选择: switch语句

```java
Scanner in = new Scanner(System.in);
System.out.println("Select an option: 1, 2, 3, 4");
int choise = in.nextInt();
switch (choice)
{
    case 1:
        // ...
        break;
    case 2:
        // ...
        break;
    case 3:
        // ...
        break;
    case 4:
        // ...
        break;
    default:
        // ...
        break;
}
```

switch语句逐项匹配标签，直到遇到break; 没有匹配的标签，执行default字句。

case标签必须是整数或枚举常量。

不建议使用switch语言。(break容易忘，易出错)

### 中断控制流程

break跳出循环语句

```java
while (years <= 100)
{
    balance += payment;
    double interest = balance * intetrestRate / 100;
    balance += interest;
    if (balance >= goal) break;
    years++;
}
```

continue跳到最内层循环的首部，或跳到for循环的更新部分

```java
Scanner in = new Scanner(System.in);
while (sum < goal)
{
    System.out.print("Enter a number:");
    n = in.nextInt();
    if (n < 0) continue;
    sum += n;
}
```

```java
for (count = 1; count <= 100; count++)
{
    System.out.print("Enter a number:");
    n = in.nextInt();
    if (n < 0) continue;
    sum += n;
}
```

##  大数值

`BigInteger`实现任意精度整数运算

`BigDecimal`实现任意精度浮点数运算

使用`valueOf`静态方法将普通数值转换为大数值

使用`add`，`multiply`等方法进行运算

```java
BigInteger a = BigInteger.valueOf(100);
BigInteger b = BigInteger.valueOf(200);
BigInteger c = a.add(b);
System.out.println("c is " + c);
```

## 数组

数组是一种数据结构，是存储同一类型数值的集合

可以通过整型下标访问数组的每一个值

声明数组变量：指定数组类型(`type[]`)和变量名

`int[] a`

初始化数组：

`int[] a = new int[100];`

通过下标访问数组:

```java
int[] a = new int[100];
for (int i = 0; i < 100; i++)
    a[i] = i;
```

可以用`array.length`来获取数组中的元素个数

```java
for (int i = 0; i < a.length; i++)
    System.out.println(a[i]);
```

一旦创建了数组就不能改变其大小

### for each循环

`for (variable : collection) statement`

如：

```java
for (int element : a)
    System.out.println(element);
```

可以用`Arrays.toString(a)`打印数组中的所有值

### 数组初始化及匿名数组

```java
int[] smallPrimes = {2,3,5,7,11,13}; // 不需要使用new
```

初始化一个匿名数组：

```java
new int[]{17,19,23,29,31,37};
```

### 数组拷贝

允许将一个数组变量拷贝给另一个数组变量：两个变量将引用同一个数组

```java
int[] smallPrimes = {2,3,5,7,11,13}; 
int[] luckyNumbers = smallPrimes;
luckyNumbers[5] = 12; // smalPrimes[12]也变成12
```

将数组中所有值也拷贝到一个新数组中，使用`Arrays.copyOf`方法：

```java
int[] copiedLuckyNumbers = Arrays.copyOf(luckyNumbers, luckyNumbers.length);
```

第2个参数是新数组的长度。

可以用下面的方法来增加数组的大小：

```java
luckyNumbers = Arrays.copyOf(luckyNumbers, 2 * luckyNumbers.length);
```

### 数组排序

使用`Arrays.sort`进行数组排序

```java
int[] numbers = new int[10];
for (int i = 0; i < numbers.length; i++) {
    numbers[i] = (int)(Math.random() * numbers.length);
}
System.out.println("Numbers:" + Arrays.toString(numbers));
Arrays.sort(numbers);
System.out.println("Numbers after sort:" + Arrays.toString(numbers));
```

### 多维数组*

二维数组声明：`double[][] balances;`

初始化： `balances = new double[NYEARS][NRATES];`

简单初始化：

```java
int[][] magicSquare = 
{
    {16, 3, 2, 4},
    {6, 10, 5, 8},
    {8, 3, 2, 19},
    {4, 5, 8, 20}
};
System.out.println(Arrays.deepToString(magicSquare));
```

可以用`Arrays.deepToString`打印二维数据的值

逐个初始化：

```java
final int NROWS = 4;
final int NCOLS = 3;
double[][] square = new double[NROWS][NCOLS];
for (int i = 0; i < square.length; i++) {
    for (int j = 0; j < square[i].length; j++) {
        square[i][j] = Math.random();
    }
}

for (double[] rows : square) {
    for (double e : rows) {
        System.out.printf("%10.2f", e);
    }
    System.out.println();
}
```



一个例子：

```java
final int NYEARS = 10;
final int NRATES = 6;		
double[] interestRates = {0.1, 0.11, 0.12, 0.13, 0.14, 0.15};
double[][] balances = new double[NYEARS][NRATES];

// 初始余额设置为10000
for (int j = 0; j < balances[0].length; j++) {
    balances[0][j] = 10000.0;
}

// 设置每一年的余额
for (int i = 1; i < balances.length; i++) {
    for (int j = 0; j < balances[i].length; j++) {
        // 上一年的余额
        double oldBalance = balances[i-1][j];
        // 计算利息
        double interest = oldBalance * interestRates[j];
        // 计算当年余额
        balances[i][j] = oldBalance + interest;
    }
}

// 打印利息
for (int j = 0; j < interestRates.length; j++) {
    System.out.printf("%9.0f%%", 100 * interestRates[j]);
}
System.out.println();

// 打印余额表
for (double[] yearBalances : balances) {
    for (double b : yearBalances) {
        System.out.printf("%10.2f", b);
    }
    System.out.println();
}
```

### 不规则数组*

Java实际上没有多维数组，只有一维数组。多维数组实际上是‘数组的数组’。

创建一个不规则数组：

```java
final int NMAX = 5;
int[][] odds = new int[NMAX+1][];

for (int i = 0; i <= NMAX; i++) {
    odds[i] = new int[i];
}
```

