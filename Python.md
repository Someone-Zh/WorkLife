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
* +      example: 1 + 2 = 3
> 加法

* -      example: 3 - 2 = 1
> 减法

* *      example: 3 * 2 = 6
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

* >       example: 1 > 10 = False
> 大于

* <       example: 1 < 10 = True
> 小于

******
## 集合操作
* List
```
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
```
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
```
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
```
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
```
# elif和else 都可有可无
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```

* while
```
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
```
# iter()创建迭代器
list=[1,2,3,4]
it = iter(list) 
# next()进行迭代
print(next(it))
# 把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 。StopIteration 异常用于标识迭代的完成

```



