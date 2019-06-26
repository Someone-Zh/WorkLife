# C++ primer 笔记

## 1. 进入C++

### 1.1 main函数
* *分号则代表着语句的结束*
* *语句就是要执行的操作*
```c++
#include <iostream> // 引入需求文件   预处理器编译指令 #include
int main()   // 函数定义头
{           //  函数体开始
    using namespace std;   //声明使用的命名空间  编译指令using namespace
    cout << "is a simple C++ program" << endl;    // 使用iostream中的std::cout 进行输出   
    return 0;       //函数返回值
}           //函数体结束
```
### 1.2 注释
```c++
//这是注释
/* 
  这是注释
*/
```
### 1.3 预处理器与头文件
* *如上面提到的#include 就是预编译指令*
* *using namespace 也是一种预编译指令，但只有在头文件为C++风格头文件时才可以使用*
* *类似于iostream 这样的文件叫做包含文件 也叫做头文件* 

### 1.4 命名空间
* 命名空间 旨在编写大型大型程序以及将多个厂商的现有的代码组合起来的程序时更容易*
    > 由来：每个语言都有自己的包管理 而c++的包管理则是命名空间 当有两个已经封装完成的产品，每个产品都有一个 pay()函数时,并且同时引入两个产品时，则分不清楚改执行哪一个。

** *
## 2. 处理数据
### 2.1 程序要存储信息通常都需要三个基本信息
1. 信息存在哪里
2. 要存储什么信息
3. 信息是什么类型
  
### 2.2 变量名
1. 只能使用数字、字母和下划线
2. 第一个字母不可以为数字
3. 区分大小写字符
4. 不能使用c++关键字以两个下划线或者下划线加大写字母开头的名称被保留给实现（编译器及其使用的资源）使用，以一个下划线开头的名称被保留给实现，用作全局标识符。
5. c++对名称长度没限制,名称中所有字符都有意义，但是有些平台有限制。

### 2.3 整型
1. short 、int 、 long 、 long long 
> 1字节 = 8位   00000000 
> 8位 0 - 255 或 -128 - 127

### 2.4 无符号类型
1. 由unsigned修饰整型则为无符号类型
2. 例如：unsigned short 、unsigned long

### 2.5 三种进制写法
1. 1~9 开头 为10进制书写方式
2. 0 开头为 8进制
3. 0x 或者 0X 开头为16进制
> 不论书写格式为任何进制形式存储皆为2进制

### 2.6 char 类型：字符和小整数
1. 顾名思义 char类型为存储字符类型而设计的
2. 存储数字对于计算机来说不是什么难事，但是字符却是另一回事
3. 所以采用字母的数值编码来表示
4. 例如 ASCII符号集中的A则为65

### 2.7 signed char 和 unsigned char
1. 与int 不同 char在普通情况下既不是有符号也不是无符号,是否有符号由c++决定
2. 但如果char的某种特定行为对您来说特别重要,则可以显示的设置

### 2.8 wcha_t
1. 由于语言繁多可能某个字符是8位处理不了的，比如汉字
2. wcha_t 是一种整数类型，并且io操作为wcout、wcin 用于处理
  
### 2.9 char16_t  char32_t
1. 随着编程人员对字符集的了解越来越多，wcha_t 不能在满足需求
2. char16_t 、char32_t 都是为无符号的
3. char16_t 为16位  声明为 char16_t ch = u'q';
4. char32_t 为32位  声明为 char32_t ch = U'q';

### 2.10 bool
1. C++ 将非0解释为true ，0解释为false
> ANSI/ISO C++标准添加了bool类型，过去C++ 和C 一样没有布尔类型
> 例：
```C++
  bool falg = true; 
  int flag = true; //flag = 1
  int flag = false; // flag = 0
  bool flag = -100; // flag = true
  bool flag = 0; //flag = false
```

### 2.11 const 限定符
1. 声明一个不可修改的常量的标识符 如: const int MOUTH = 12；

### 2.12 浮点数
1. 一种书写方式为 6.678 第二种为E表示法  6.6E3 或者6.6E+3 为实际 6600  6.6E~3 为 0.0066
>  En为小数点右移n位 E~n为小数点左移n位  也就是浮点数的由来

### 2.13 浮点类型
1. float  声明为  1.7f 或者 1.7F
2. double   默认书写  都是为double 类型
3. long double  声明为  1.7L  或者1.7l
> 这些类型是按照他们表示的有效位和允许的指数最小范围来描述的

### 2.14 算数运算符
1. \+ 运算符对操作数进行加法运算
2. \- 运算符从第一个数中减去第二个数
3. \* 运算符将操作数相乘
4. / 运算符用第一个数除以第二个数
5. % 运算符求模

** *
## 3. 复合类型
### 3.1 数组
1. 声明数组为  数组类型  数组名[元素数量] 例 short mouths[12]
2. 数组的初始化为 int card[4] = {1,2,3,4}  C++11中也可以省略=

> 数组是一种数据数据格式，能够存储多个同类型的值。
> 数组之所以为复合类型是因为他是使用其他类型来创建的（因为’派生‘被用来描述类的关系）

### 3.2 字符串
1. char cat[8] = {'f','a','t','a','s','s','a','\0'};
2. char cat[8] = "fatassa";
3. cahr cat[] = "fatassa";
4. string str = "this";
> C++98 添加了string 类扩展了C++库

### 3.3 结构体
1. struct structName { type... }
2. 由关键字struct声明 标识符structName是这个数据格式的名称 
```c++
#include <iostream>
using namspace std;
struct student
{
  int age;
  int height;
  char name[20];
};
int main()
{
  student t = {
    18,
    180,
    "liSan"
  };
  cout << t.age << t.name << t.height;
  return 0 ;
}
```
### 3.4 共用体
1. 每次只能存储一个值
2. 常用于节约内存
```C++
#include <iostream>
using namspace std;
union student
{
  int age;
  long height;
  double pip;
};
int main()
{
  student stu;
  stu.age = 18;
  stu.height = 14.32; // age丢失
  return 0 ;
}
```
### 3.5 枚举 
```C++
  //声明枚举
  enum color = {red,black=100,orange,yellow};
  // 如果只使用常量并不实例化
  enum {red,black=100,orange,yellow};
```
### 3.6 指针和自由存储空间
1. & 为地址运算符 获取变量的内存地址
2. 声明为 int *  p_int;
3. 一定要在对指针应用解除引用运算符之前，将指针初始化为一个确定的、适当的地址。
4. 使用new运算符来分配内存地址（malloc也可以但是不推荐）
5. 使用delete 释放内存 （删除内存引用但不会删除指针）
6. 释放数组的内存 为 delete [] point
7. 数组指针的加减为位置的加减
8. 指针访问其值中对应的元素要用箭头运算费用 ->
** *
## 4. 循环
### 4.1 for循环
1. 包括 循环的初始化部分 int i =0;  循环检测 i < 5 和循环更新 i++
2. i++  为先用值  然后自增  ++i 为先自增 在用值  -- 同理 （语句结束后自增）
   
```C++
  for (int i = 0; i < 5 ; i++)
  {
    cout << "loop" ;
    doSomeoneThing();
  }
  //一条语句可以没有大括号
  for (int i = 0; i < 5 ; i++)
    cout << "looping" ;
```
### 4.2 while 循环
1. while就是没有初始化部分和更新部分的for循环
```C++ 
  int i = 0;
  while (i < 5)
  {
    cout << "loop";
    i++;
  }
```
### 4.3 do while 循环
1. do while 是出口循环  先执行循环体在判断条件
### 4.4 基于范围的for循环
1. C++11 新增 可以遍历 数组（或者容器类） 的每个元素进行遍历
   ```C++
    int  pice[5] = {1,2,3,4,5};
    for (int x : pice)
      cout << x << endl;
   ```
### 4.5 类型别名
1. 使用预处理器 如 #define aliasName typeName 将会在编译时用typeName替换aliasName
2. 第二种 typedef typeName aliasName 在运行时使用
 ** *
## 5. 分支与逻辑运算
### 5.1 if语句

```C++
  if (bool)
  {
    dosome;
  }
  else if ( bool )
  {
    dosome;
  }else
  {
    dosome;
  }
  //只有一条语句可以省略大括号
  if ( bool )
    do some;
  else if (bool)
    do some;
  else
    do some;
```
### 5.2 逻辑运算符 
1. 逻辑或OR （||）   一真则真
2. 逻辑与AND （&&）  一假则假
3. 逻辑非NOT (NOT)  真则假 假则真

### 5.3 条件运算符
1. 如果expression1 的值为ture 则表达式的值为 expression2 否则为 expression3  
```C++
  expression1?expression2 : expression3  
```
### 5.4 switch 语句
1. switch 能够容易的从大型列表中进行选择。
2. 如果不使用break 则会顺序执行所有语句。
3. 处理的只能输整数（char），无法处理浮点数。
```C++
  switch (integer - expression)
  {
    case label1:statement(s)
    case lable2:statement(s)
    ...
    default    :statement(s)
  }
```

### 5.5 break 和 continue
1. break 用于打破 代码块 并向下执行。
2. continue 用于结束此次循环 并进行下一次循环。

** *
## 6. 函数
### 6.1 函数定义
1. 可以有多个参数,用逗号隔开。
```C++
returnType functionName(parameterList)
{
  statement(s)
  return returnType;
}
```
### 6.2 函数原型
1. 函数使用之前一定要声明函数原型。
2. 目的是将返回类型和参数类型和个数通知编译器。
3. 原型的定义可以只有参数类型，参数名只是占位符。
```C++
double cube(double x);
int main()
{
  double x = cube(2);
  return 0;
}
double cube(double x)
{
  returb x * x * x;
}
```
### 6.3 指针和const
1. 下面的声明指出 pt 指向的是 const int 的指针， *pt 更改age的值或出现错误，但是通过age更改没问题。
```c++
int age = 39;
const int * pt = &age;
```
2. 可以将const 变量赋值给指向const的指针。但是将const的地址赋给常规指针却是不可以的。
```c++
const float eartch = 9.80;
const float * pe = &eartch;  // valid

const float eartch = 1.63;

float * pe = &eartch; //invalid
```
### 6.4 C-风格字符串作为参数
1. 支持char 数组   char 指针 用引号括起来的字符串常量
### 6.5 函数指针
1. 声明一个函数指针原型.
```c++
retutnType (* fun) (int);
```
### 6.6 内联函数
> 加快程序执行速度，增加内存占用。
1. 可以在函数声明前加上关键字inline。
2. 也可以在函数定义前加上关键字inline。
### 6.7 引用变量
1. 声明引用
```c++
  int age =18;
  int & fa = age;
```
2. 传引用参数 则为同一个变量 即同一个地址。
3. c++11 新增右值引用   int && i = 2.0 * j +5;
### 6.8 默认参数
1. void left(type name = value)
2.  默认参数能使用不同的参数数目调用同一个函数
### 6.9 函数重载（多态）
1. 函数重载能使用多个同名函数。
2. 关键是函数的参数列表---也称为函数特征标。如果两个函数的参数数目和类型相同，同时参数排列顺序也相同，则他们的函数特征标相同。

### 6.10 函数模板（泛型）
1. 第一行指出要创建一个模板，并将类型命名为AnyType。
2. 关键字 template 和 typename 是必须的。
3. 在c++98 添加关键字typename之前C++使用class来创建模板。
4. 模板可以重载。
5. 模板的局限性：比如指针的加减等等。
```c++
template <typename AnyType>
void Swap(AnyType &a,AnyType &b)
{
  statement
}
```
### 6.11 实例化和具体化
1. 在代码中包含函数模板本身并不会生成函数定义，它只是用于生成函数定义的一种方案。
2. 编译器使用模板为特定类型生成函数定义，也就是模板的实例，也称为隐式实例化。
3. 显示实例化是直接命令编译器去创建指定类型的实例。如：template void Swap<int> (int,int)
### 6.12 decltype(C++11)
1. 声明  decltype (expression) var;
2. 为了确认 expression结果的类型

** *
## 7. 内存模型和命名空间
### 7.1 单独编译
1. 可以单独编译一些文件，然后链接成可执行文件。
2. 程序一般分为三个部分
   * 头文件：包含结构声明和使用这些结构的函数原型。
   * 源代码文件：包含与结构有关的函数的代码。
   * 源代码文件：包含调用与结构相关的函数的代码。
3. 头文件一般包含：
   * 函数原型
   * 使用#define或者const定义的符号常量
   * 结构声明
   * 类声明
   * 模板声明
   * 内联函数
4. 在同一个文件中只能包含同一个头文件一次。防止多重定义使用#ifndef 符号常量 ... #endif
### 7.2 存储的持续性、作用域、和连接性
1. C++使用三种（C++11使用四种）不同的方案存储数据。
   * 自动存储持续性：在函数定义中声明的变量包括函数参数。 作用域：局部
   * 静态存储持续性：在函数定义外定义的变量和使用关键字static定义的变量  连接性：外部（其他文件），内部（当前文件），无（当前函数或者代码块）
   * 线程存储持续性（C++11）：使用关键字thread_local声明的变量
   * 动态存储持续性：使用new 运算符分配的变量
2. C 语言寄存器变量由register声明 在C++中只是auto的声明
3. 静态变量默认0值初始化
4. 引用声明 extern
5. cv-限定符 即 const和volatile
   * volatile 表明即使程序代码没有对内存单元镜像修改，其值也可能变化。
6. mutable：指明结构或者类即使为const其中被修饰的成员仍然可以修改。
7. const 修饰外部变量 会默认变为内部的变量，如果想要定义外部的常量 则需要指定extern const int  var = 1；
### 7.3 名称空间
1. 名称空间的术语
   * 声明区域：可以声明的区域
   * 潜在作用域：变量的潜在作用域从声明点开始到其声明区域结尾。
2. 名称空间是开放的，比如下面就是将choose添加到jill中已有的名称列表之中。
```c++
namespace jill{
  char * choose(const char *);
  double fetch;
}
```
3. 使用名称空间来限定名称需要使用域操作符 ::
4. 有两种机制来简化对名称空间中名称的使用
   * using 声明 如: using jill::fetch;
   * using 编译 如：using namespace jill;
5. 名称空间可以嵌套
** *
## 8. 对象和类
### 8.1 类的声明
1. 类由 关键字 class 声明。
2. 关键字 private 和 public 描述了类的访问控制。（还有 protected）
3. 类的成员访问控制默认为 private
4. 定义时使用域操作符::
5. 类中方法可以访问私有成员
6. 同一个类的多个对象有各自的数据，但是共享成员函数。
```C++
#ifndef STOCK00_H_
#define STOCK00_H_

#include <string>
class Stock
{
  private:
    std::string company;
    long shares;
    double share_val;
    double total_val;
    void set_tot (){ total_val = shares * share_val }
  public:
    void acquire (const std::string & co,long n ,double pr);
    void buy (long num, double price);
    void sell (long num , double price);
    void update(ouble price);
    void show();
};
#endif
```
### 8.2 类的构造函数和析构函数
1. 构造函数名称与类名相同
2. 构造函数用于创建对象并执行
3. 不存在返回类型
4. 调用构造函数
    * 显示调用 Stock food = Stock(params...);
    * 隐式调用 Stock food(params...);
5. 函数如果没有定义任何构造函数编译器则会提供默认构造函数
6. 析构函数用于在对象过期时完成清理工作
7. 析构函数的书写
   ```C++
    Stock::~Stock()
    {
      statement
    }
   ```
### 8.3 this 指针
1. 每个成员函数都一个this指针，this指针指向调用对象。

### 8.4 作用域枚举
1. 传统枚举当存在相同枚举量时，编译器会报错。因为他们位于相同作用域内。
2. C++11 提供了一种新枚举,其作用域为类或者结构，由于操作符访问。
   * enum class egg { small , Medium ,Large , XLarge}
   * enum struct egg { small , Medium ,Large , XLarge}

### 8.5 运算符重载
1. 运算符重载函数格式为：operator（argument-list）如：operator +（）重载加运算符
2. 类重载（）运算符后可以进行函数方式使用，如 operator ()();

### 8.6 友元
1. 友元有三种
   * 友元函数
   * 友元类
   * 友元成员函数
2. 友元函数允许和成员函数一样访问类的成员。
3. 创建友元函数是在类的声明里加上友元函数的声明，并在前方加上关键字friend

### 8.7 类的自动转换和强制转换
1. 兼容类型可以自动转换比如 int double 但是大精度转小精度会出现精度丢失
2. 不兼容的类型C++不会自动转换类型，需要自己手动强制转换。
3. 当构造函数如 a(b) 时，可以写为  a a = b; 这样的隐式转换
4. 使用explicit 关闭隐式转换
5. 其他隐式转换情况
   * 将对象初始化为构造函数的参数时
   * 将构造函数参数类型赋予对象时
   * 将构造函数参数类型传递给对象参数的函数时
   * 返回值为对象的函数试图返回对象参数的类型时
6. 将其他类型转换为类时使用构造函数来实现隐式转换，将类转换为其他类型时需要定义转换函数
   * operator typeName();
7. C++提供的特殊成员函数
   * 默认构造函数
   * 默认析构函数
   * 复制构造函数
   * 赋值运算符
   * 地址运算符
   * 移动构造函数
   * 移动赋值运算符
8. 函数参数传递也会触发复制构造函数，函数结束会调用析构函数。
9. 静态成员函数需要用类加域操作符调用。
10. new 和 delete 必须兼容,new 和 delete new[] 和 delete[]。
11. C++11 新增关键字nullptr 表示空指针
12. 使用new运算符返回对象指针。

** *
## 9. 多态
### 9.1 基类与派生类
1. 从一个类派生出另一个类，原始类就叫做基类。新的类叫派生类。
2. 派生类继承类基类的数据成员和方法。
3. 派生类不能直接访问基类的私有成员。
4. 会先创建基类在创建派生类。
5. 派生类构造函数应通过成员初始化列表将基类信息传给基类构造函数。
6. 成员初始化列表
   ```C++
    className::className(type1 x,type2 y):baseClass(x,y){}
   ```
7. 三种继承方式
   * 公有继承：is-a
   * 保护继承
   * 私有继承：has-a
8. 实现多态共有继承的两种方式
   * 在派生类中重新定义
   * 使用虚方法

### 9.2 虚函数
1. 在基类的方法声明中使用关键字virtual可使该方法在基类以及所有派生类中是虚的。
2. 如果使用指向对象的指针或者引用来调用虚函数，程序将使用为对象类型定义的方法，而不使用指针或引用类型定义的方法，也称为动态联编或晚期联编。
3. 如果定义的类被用作基类，则应在派生类中重新定义的方法声明为虚的。
4. 纯虚函数声明的结尾处为 = 0;
5. 当类包含纯虚函数时，则不能创建该类的对象。

### 9.3 访问控制 protected
1. 对于非派生类来说 protected和private的功能是一样的，但是对派生类来说，在基类中为protected的在派生类中是可以访问的。

### 9.4 多重继承（MI）
1. 多重继承可能会存在多个子对象问题。通过类型转换或虚基类解决。
2. 在类的继承声明中使用virtual关键字声明虚基类。
3. 虚基类使得从多个类（基类相同）派生出的对象只继承一个基类对象。
4. MI的构造函数除非采用虚基类的默认构造函数，不然必须显式地调用虚基类的构造函数，但是如果不是虚基类则会出现错误。
5. MI可能会导致函数调用的二义性。
   * 可以使用域操作符来确定具体调用。
   * 在类中重新定义。

### 9.5 类模板
1. 类模板的使用声明为 Stack<int> stack;
2. 默认类型模板参数：如 template <class T1, class T2 = int> class too时，可以声明为 too<double,double> 或者too\<double\>。
3. 将模板用作模板参数 template \<template \<typename T> class Thing> 这样的模板只能参数为模板类。
4. 类模板的友元函数
   * 非模板友元函数 friend void fun();
   * 约束模板友元函数  friend void fun<T>();
   * 非约束模板友元函数  template <typename C ,typename D> friend void fun(C & c,D & d);
5. typedef 也可以用于模板别名。
```C++
template <class T>
class Stack 
{
  private:
    enum {MAX = 10};
    T items[MAX];
    int top;
  public:
    Stack();
    bool isempty();
    bool isfull();
    bool push(const T & item);
    bool pop(T & item);
}

template <class T>
Stack<T>::Stack()
{
  top = 0;
}
template <class T>
bool Stack<T>::isempty()
{
  return top == 0;
}
```
### 9.6 友元
1. 友元类的声明为 friend class classname;
2. 友元成员函数的声明为 friend void fclass::fun();

** *
## 10. 异常
### 10.1 异常机制
1. 对异常处理有三种方式
   * 引发异常
   * 使用处理程序捕获异常
   * 使用try 块
2. throw 语句用于抛出错误，导致程序沿调用顺序后退，直到找到包含try块的函数。
3. catch块点类似有函数的定义，表明这是一个处理程序。
4. char *s 表明改程序与字符串异常匹配。
5. 异常也可以抛出类作为异常信息。
```C++
  try
  {
    statement
  }
  catch (const char * s)
  {
    
  }
```

### 10.2 异常规范
1. C++98新增的异常规范为: void fun() throw([exception]);
2. C++11支持一种特殊的异常规范:void fun() noexcept; 指明函数不会引发异常。

### 10.3 exception 类
1. exception 中的what()为虚函数。
2. 继承exception类可以编写自己的异常体系。
3. stdexcept头文件定义了logic_error和runtime_error类，他们都是从exception派生的。

** *
## 11. RTTI
### 11.1 RTTI工作原理
1. C++有三个支持RTTI的元素。
   * 如果可能的话，dynamic_cast 运算符将使用一个指向基类的指针来生成一个指向派生类的指针。否则返回0.
   * typeid 运算符返回一个指出对象类型的值。
   * type_info 结构存储了有关特定类型的信息。
2. 只能将RTTI用于包含虚函数的类层次结构，原因在于只有对这种类层次结构才应该将派生对象的指针的地址赋给基类指针。

### 11.2  dynamic_cast
1. 如果pm 为空指针则说明pg无法转换成superb。
2. 用于引用时无法转换则抛出bad_cast 异常。
```C++
  superb * pm = dynamic_cast<superb *>(pg);
```

### 11.3  typeid 运算符 
1. typeid 用于确定两个对象是否为同种类型。
2. typeid 运算符返回一个对type_info的引用。
```C++
  typeid(obj) == typeid(* p)
```

*** *
## 12. 类型转换运算符
### 12.1 dynamic_cast
1. 仅当ph为Low的可访问基类，才会成功赋值，否则为空指针。
```C++
  pl = dynamic_cast<Low *> ph;
```
### 12.2 const_cast
1. 用于执行只有一种用途的类型转换。即改变值为const或volatile
```C++
  const_cast< type-name > (expression);
  const High * pbar;
  pb = const_cast< High *>(pbar); //删除const属性
```
### 12.3 static_cast
1. 仅当type-name 可以隐式的转换为expression 所属的类型或expression可被隐式转换为type-name所属的类型时才合法。
```C++
  static_cast< type-name > (expression);
```
### 12.4 reinterpret_cast
1. 用于天生危险的类型转换
```C++
  reinterpret_cast< type-name > (expression);
```

****
## 13. 智能指针模板
### 13.1 auto_ptr
1. 自动智能指针会在函数结束时自动删除指针地址和动态内存。
2. 两个auto_ptr 指向一个对象会存在问题。

### 13.2 unique_ptr
1. 行为模式和auto_ptr相同。
2. 采用建立所有权概念，即只有一个智能指针拥有对象，赋值会转让所有权。

### 13.3 shared_ptr
1. 行为模式和auto_ptr相同。
2. 采用引用计数模式，即当计数为0时才会调用delete。

