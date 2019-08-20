# Python
*****
## 数据类型
* Number | example: 1,3,1.1  | initialize: n = 5                       
  > Python3 支持 int、float、bool、complex（复数）。 python3整数类型只有int 没有Python中的long

* String | example: "hellow word" 'xxx'    |     initialize:s = "Stirng"   
  > Python中的字符串用单引号 ' 或双引号 " 括起来，同时使用反斜杠 \ 转义特殊字符。不想转义在字符串前加r。Python中的字符串有两种索引方式，从左往右以0开始，从右往左以-1开始。

* List |  example: ['abc',123,"cab"]    | initialize : l = ['abc',123,"cab"]
  > 加号 + 是列表连接运算符，星号 * 是重复操作

* Tuple | example: ('abc',"cba",123)  |  initialize : t = ('abc',"cba",123)
  > 元组和列表很相似，不同的是元组中的元素不可修改。元组也可以使用+操作符进行拼接。一个元素后面要加逗号‘,’否则括号会被当作运算符使用。

* Set |   example: {'Tom','Rose'}  | initialize : s = {'Tom','Rose'}
  > 空集合的初始化只能用set()而不是{}

* Dictionary |   example: {"name":"Tom","age":18}  |   initialize : d = {"name":"Tom","age":18} 
  > key 必须唯一 

*****
## 算术运算
* \+      example: 1 + 2 = 3
  > 加法

* \-      example: 3 - 2 = 1
  > 减法

* \*      example: 3 * 2 = 6
  > 乘法

* /      example: 5 / 3 = 1.6666666666666667,35 / 5 = 7。0
  > 除法会自动装换为浮点数

* //      example: 5 // 3 = 1,-5.0 // 3.0 # => -2.0
  > 整除会自动向下取整

* %       example: 7 % 3 = 1
  > 模 或取余

*****
## 逻辑运算
* not     example: not True = False
  > 非

* and      example: True and False = False
  > 与

* or      example: False or True = True
  > 或

******
## 比较运算
* ==       example: 1 == 1 = true
  > 相等

* !=       example: 1 != 1 = false
  > 不等

* \>       example: 1 > 10 = False
  > 大于

* <       example: 1 < 10 = True
  > 小于

******
## 集合操作
* List
  ```py
  li = [4, 5, 6]
  new_li = [7,8]
  # 用append在列表最后追加元素
  li.append(7)   # =>[4,5,6,7]
  # 用pop从列表尾部删除
  li.pop()  # =>[4, 5, 6]
  # 列表存取跟数组一样
  li[0]   # => 4
  # 取出最后一个元素
  li[-1]  # => 6
  # 列表截取
  li[1:]  # => [5, 6]
  # 用del删除任何一个元素
  del li[1] # => [4,6]
  # 注意：li和other_li的值都不变
  li + other_li   # => [ 4, 6,7,8]
  # 用extend拼接列表
  li.extend(other_li)   # li现在是[4, 6,7,8]
  # 用in测试列表是否包含值
  6 in li   # => True
  # 用len取列表长度
  len(li)   # => 4
  ```
* Tuple
  ```py
  # 元组是不可改变的序列
  tup = (7, 8, 9)
  tup[0]   # => 7
  tup[0] = 3  # 抛出TypeError
  
  # 列表和元组的共同操作
  len(tup)   # => 3
  tup + (4, 5, 6)   # => (7, 8, 9, 4, 5, 6)
  tup[:2]   # => (7, 8)
  9 in tup   # => True
  # 将元组的各个元素赋值
  a, b, c = (1, 2, 3) 
  ```
* Set
  ```py
  set = {1, 1, 2, 2, 3, 4}
  other_set = {3, 4, 5, 6}
  # 添加元素
  set.add(5) # => {1, 1, 2, 2, 3, 4,5}
  # & 交集
  set & other_set   # => {3, 4, 5}
  # | 并集
  set | other_set   # => {1, 2, 3, 4, 5, 6}
  # - 补集
  set - other_set  # =>{1,2}
  # ^ 差集
  set ^ other_set  # => {1,2,6}
  # in 是否包含元素
  2 in set   # => True
  ```

* Dictionary
  ```py
  dict = {"one": 1, "two": 2, "three": 3}
  # 用 keys() 获得所有的键。 返回的是迭代器 要用list()初始化
  list(dict.keys()) # => "one","two","three"
  # 用 values() 获取所有值，同上
  list(dict.values())   # => [3, 2, 1]
  # in只能检测键是否在字典中 
  "one" in filled_dict   # => True
  1 in filled_dict   # => False
  # 用[]取值 不存在则或报错
  dict["one"]   # => 1
  # 用get来避免KeyError
  dict.get("one")   # => 1
  dict.get("four")   # => None
  # 也可以设置不存在的默认值
  dict.get("one", 4)   # => 1
  dict.get("four", 4)   # => 4
  # 字典赋值
  dict["four"] = 4  # => {"one": 1, "two": 2, "three": 3,"four":4}
  dict.update({"four":4}) #  => {"one": 1, "two": 2, "three": 3,"four":4}
  # setdefault() 当键不存在的时候才设置
  dict.setdefault("five",5) # {"one": 1, "two": 2, "three": 3,"four":4,"five":5}
  # 用del删除
  del dict["five"] # => {"one": 1, "two": 2, "three": 3,"four":4}
  ```

******
## 流程控制与条件控制
* if
  ```py
  # elif和else 都可有可无
  if condition_1:
      statement_block_1
  elif condition_2:
      statement_block_2
  else:
      statement_block_3
  ```

* while
  ```py
  # else 可以有也可以没有
  while condition:
      block
  else
      do
  # 同上 for可以遍历任何序列 
  for variable in sequence:
      doSomeThing
  else:
      doSomeThing
  ```

*******
## 迭代器与生成器

* 迭代器
  ```py
  # iter()创建迭代器
  list=[1,2,3,4]
  it = iter(list) 
  # next()进行迭代
  print(next(it))
  # 把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 。StopIteration 异常用于标识迭代的完成
  ```
* 生成器
  ```py
  # 使用了 yield 的函数被称为生成器，生成器返回的为迭代器
  def fibonacci(n): # 生成器函数 - 斐波那契
      a, b, counter = 0, 1, 0
      while True:
          if (counter > n): 
              return
          yield a
          a, b = b, a + b
          counter += 1
  f = fibonacci(10) # f 是一个迭代器，由生成器返回生成
  ```
******
## 函数与模块
* 函数
  ```py
  # 一般格式 return 可以没有
  def 函数名（参数列表）:
      函数体
      return 结果
  ```
* 函数参数
  > 函数参数分 必需参数,关键字参数,默认参数,不定长参数。
  ```py
  # 必须参数 实际调用必须填写
  def name(str):
      ...
  # 关键字参数
  def name(str):
      ...
  name(str="Tom")
  # 默认参数
  def name(str,age=18):
      ...
  # 不定长参数 参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。
  def name(str,*girl):
      ...
  # 还有一种不定长参数 参数会以字典的形式导入
  def name(str,**girl):
      ...
  ```
* 匿名函数
  ```py
  # lambda 函数的语法只包含一个语句
  lambda [arg1 [,arg2,.....argn]]:expression
  
  ```
* 作用域
  > Python 中只有模块（module），类（class）以及函数（def、lambda）才会引入新的作用域，其它的代码块（如 if/elif/else/、try/except、for/while等）是不会引入新的作用域的
  > L （Local） 局部作用域
  > E （Enclosing） 闭包函数外的函数中
  > G （Global） 全局作用域
  > B （Built-in） 内置作用域（内置函数所在模块的范围）
  ```py
  g_count = 0  # 全局作用域
  def outer():
      o_count = 1  # 闭包函数外的函数中
      def inner():
          i_count = 2  # 局部作用域
  ```
  > 当内部作用域想修改外部作用域的变量时，就要用到global和nonlocal关键字了。
  ```py
  # 不使用global则默认是局部变量 不使用全局变量
  num = 1
  def fun1():
      global num  # 需要使用 global 关键字声明
  # 如果要修改嵌套作用域（enclosing 作用域，外层非全局作用域）中的变量则需要 nonlocal 关键字
  def outer():
    num = 10
    def inner():
        nonlocal num   # nonlocal关键字声明
        num = 100
        print(num)
    inner()
    print(num)
  ```
* 模块
  > 模块是一个包含所有你定义的函数和变量的文件
* 导入
  ```py
  #!/usr/bin/python3
  # 导入模块
  import sys 
  # 导入模块并别名
  import sys as s
  # 导入模块中的子模块
  from libs import lib1,lib2 
  ```
******
## 面上对象
* 类
  > 两个下划线__ 声明的属性和方法为私有的
  > 类的专有方法
  * \_\_init__ : 构造函数，在生成对象时调用
  * \_\_del__ : 析构函数，释放对象时使用
  * \_\_repr__ : 打印，转换
  * \_\_setitem__ : 按照索引赋值
  * \_\_getitem__: 按照索引获取值
  * \_\_len__: 获得长度
  * \_\_cmp__: 比较运算
  * \_\_call__: 函数调用
  * \_\_add__: 加运算
  * \_\_sub__: 减运算
  * \_\_mul__: 乘运算
  * \_\_truediv__: 除运算
  * \_\_mod__: 求余运算
  * \_\_pow__: 乘方

  ```py
  #!/usr/bin/python3
  class NewClass: #用class 声明一个类
      """一个简单的类实例"""
      i = 12345  # 定义类的属性
      __weight = 0 # 定义类的私有属性
      def f(self):   #定义类的方法  和正常函数的区别是类的方法区别是必须包含self(类的示例)
          return 'hello world'
      def __init__(self):   # 类的构造函数
          self.i = 12345
  # 实例化类
  x = NewClass()
  # 调用示例属性和方法
  print("NewClass 类的属性 i 为：", x.i)
  print("NewClass 类的方法 f 输出为：", x.f())
  ```
* 继承
  > 若是基类中有相同的方法名，方法在子类中未找到时，从左到右查找基类中是否包含方法。
  ```py
  #!/usr/bin/python3  
  class className(BaseClass): # 单继承
  class className(BaseClass1,BaseClass2,BaseClass3): # 多继承
  ```
## 错误和异常
* 异常
  > except可以使多个以元组形式捕捉也可以是多个except,如果不填写异常类型则捕捉所有异常
  > raise 为抛出异常
  > else 可以没有  当没有异常时会执行饿else语句
  > finally 不论是否出现异常都会执行finally语句
  ```py
  import sys
  try:
      f = open('myfile.txt')
      s = f.readline()
      i = int(s.strip())
  except OSError as err:
      print("OS error: {0}".format(err))
  except （ValueError,NameError):
      print("Could not convert data to an integer.")
  except:
      print("Unexpected error:", sys.exc_info()[0])
      raise
  else:
      print('no error')
  finally:
      f.close()
    ```
* 预定义的资源关闭
  > 使用
  ```py
  with open("myfile.txt") as f:
  ```
* 自定义异常
  >自定义异常需要直接或者间接继承Exception
  ```py
  class MyError(Exception):
        def __init__(self, value):
            self.value = value
        def __str__(self):
            return repr(self.value)
  ```
******
## decorator
* 函数装饰器
 > 装饰模式的语法糖
  ```py
  # 装饰器模式
  def log(func):
      def buildFunc():
          logging.warn("%s is running" % func.__name__)
          func()   # 把 foo 当做参数传递进来时，执行func()就相当于执行foo()
      return buildFunc
  def foo():
      print('i am foo')

  foo = log(foo)  # 因为log() 返回的是装饰过的方法  所以foo相当于 buildFunc()
  foo() 
  # @语法糖
  def log(func):
      def buildFunc():
        logging.warn("%s is running" % func.__name__)
        func()   # 把 foo 当做参数传递进来时，执行func()就相当于执行foo()
        return buildFunc
  @log
  def foo():
      print('i am foo')
  foo() # 和装饰器模式一样 只是由 @语法糖 帮你完成了  
  # 带参数的 装饰
  def log(func):
      def builcFunc(name):
          logging.warn("%s is running" % func.__name__)
          func(name)
          return buildFunc

  @log
  def foo(name):
      print("i am " + name)
  # 不定个数参数
  def log(func):
      def builcFunc(*args,**kvargs):
          logging.warn("%s is running" % func.__name__)
          func(name)
          return buildFunc
  @log
  def foo(name,age=None,sex=None):
      print("i am " + name) 
  ```
