**位运算：**	

```python
# & 与
# | 或
# ! 非
# ^ 异或
# << 左移 n 位 乘2
# >> 右移 n 位 除2
```

**三目运算符：**

```python
x if x>y else y # 整个表达式返回一个数值
```

<b>其他运算符</b>

|  操作符  |  名称  |             示例             |
| :------: | :----: | :--------------------------: |
|   `in`   |  存在  |   `'A' in ['A', 'B', 'C']`   |
| `not in` | 不存在 | `'h' not in ['A', 'B', 'C']` |
|   `is`   |   是   |     `"hello" is "hello"`     |
| `not is` |  不是  |   `"hello" is not "hello"`   |

```python
# is 与 == 的区别
## 不可变对象类型
a = "hello"
b = "hello"
print(a is b, a == b)  # True True
print(a is not b, a != b)  # False False

## 可变对象类型
a = ["hello"]
b = ["hello"]
print(a is b, a == b)  # False True
print(a is not b, a != b)  # True False

## 1. 不可变对象类型共享内存, 一旦创建则该内存块的数值不可改变, 因此数值相同ID相同; 
## 2. 可变对象类型不共享内存, 数值相同, ID 未必相同; 
## 3. is判断两个东西是否完全一样, == 判断两个变量内容是否一样。
```

<b>运算符的优先级</b>

| 运算符            | 描述                     |
| ----------------- | ------------------------ |
| **                | 指数（最高优先级）       |
| ~+-               | 按位翻转，一元加号和减号 |
| * / % //          | 乘，除，取模和取整除）   |
| + -               | 加法减法                 |
| >> <<             | 右移，左移运算符         |
| &                 | 位‘AND’                  |
| ^\|               | 位运算符                 |
| <=<>>=            | 比较运算符               |
| <>==!=            | 等于运算符               |
| =%=/=//=-=+=*=**= | 赋值运算符               |
| is is not         | 身份运算符               |
| in not in         | 成员运算符               |
| not and or        | 逻辑运算符               |

**序列：**

```python
a = [1,2,3]
a.pop(0) #  = 1
a.pop(-1) # = 3
## 队列操作
```

**数据类型：**

Python 里面万物皆对象（object），整型也不例外，只要是对象，就有相应的属性 （attributes） 和方法（methods）。

```python
# 查看某一对象/类型的所有属性和方法
b = dir(int)
print(b) 
## 具体的属性和方法，应该查阅文档
```

**控制数据的精度：**

```python
import decimal
from decimal import Decimal 
decimal.getcontext() # 得到默认的精度
decimal.getcontext().prec = 4
c = Decimal(1) / Decimal(3)
```

**获取对象(实例)的类别信息：**

- `type()` 不会认为子类是一种父类类型，不考虑继承关系。
- `isinstance()` 会认为子类是一种父类类型，考虑继承关系。

```python
class A:
    pass
 
class B(A):
    pass
 
isinstance(A(), A)    # returns True
type(A()) == A        # returns True
isinstance(B(), A)    # returns True
type(B()) == A        # returns False
```

**条件语句：**

```python
if True:
    pass

if True:
    pass
elif True:
    pass
else: 
    pass
```

**Assert**

`assert`这个关键词我们称之为“断言”，当这个关键词后边的条件为 False 时，程序自动崩溃并抛出`AssertionError`的异常。

注意：当于try：exception一起使用时，会出现问题。

在进行单元测试时，可以用来在程序中置入检查点，只有条件为 True 才能让程序正常工作

**循环语句：**

```python
while 布尔表达式:
    代码块
else:
    代码块
    # 相当于是对循环进行一个收尾的操作, 防止出现问题。
```

当`while`循环正常执行完的情况下，执行`else`输出，如果`while`循环中执行了跳出循环的语句，比如 `break`，将不执行`else`代码块的内容。    

```python
dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
# for 循环用来遍历可迭代对象
for key, value in dic.items():
    print(key, value, sep=':', end=' ')
```

```python
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
```

当`for`循环正常执行完的情况下，执行`else`输出，如果`for`循环中执行了跳出循环的语句，比如 `break`，将不执行`else`代码块的内容，与`while - else`语句一样。

**enumerate函数：**

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
lst = list(enumerate(seasons))
print(lst)
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
lst = list(enumerate(seasons, start=1))  # 下标从 1 开始
print(lst)
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

**解析：**

```python
# 列表解析
# 字典解析
# 元组解析
# 集合
[ expr for value in collection [if condition] ]
{:}
()
{}
```

**异常处理：**

异常就是运行期检测到的错误。计算机语言针对可能出现的错误定义了异常类型，某种错误引发对应的异常时，异常处理程序将被启动，从而恢复程序的正常运行。

## 1. Python 标准异常总结

- BaseException：所有异常的 **基类**
- Exception：常规异常的 **基类**
- StandardError：所有的内建标准异常的基类
- ArithmeticError：所有数值计算异常的基类
- FloatingPointError：浮点计算异常
- <u>OverflowError</u>：数值运算超出最大限制
- <u>ZeroDivisionError</u>：除数为零
- <u>AssertionError</u>：断言语句（assert）失败
- <u>AttributeError</u>：尝试访问未知的对象属性
- EOFError：没有内建输入，到达EOF标记
- EnvironmentError：操作系统异常的基类
- IOError：输入/输出操作失败
- <u>OSError</u>：操作系统产生的异常（例如打开一个不存在的文件）
- WindowsError：系统调用失败
- <u>ImportError</u>：导入模块失败的时候
- KeyboardInterrupt：用户中断执行
- LookupError：无效数据查询的基类
- <u>IndexError</u>：索引超出序列的范围
- <u>KeyError</u>：字典中查找一个不存在的关键字
- <u>MemoryError</u>：内存溢出（可通过删除对象释放内存）
- <u>NameError</u>：尝试访问一个不存在的变量
- UnboundLocalError：访问未初始化的本地变量
- ReferenceError：弱引用试图访问已经垃圾回收了的对象
- RuntimeError：一般的运行时异常
- NotImplementedError：尚未实现的方法
- <u>SyntaxError</u>：语法错误导致的异常
- IndentationError：缩进错误导致的异常
- TabError：Tab和空格混用
- SystemError：一般的解释器系统异常
- <u>TypeError</u>：不同类型间的无效操作
- <u>ValueError</u>：传入无效的参数
- UnicodeError：Unicode相关的异常
- UnicodeDecodeError：Unicode解码时的异常
- UnicodeEncodeError：Unicode编码错误导致的异常
- UnicodeTranslateError：Unicode转换错误导致的异常

异常体系内部有层次关系，Python异常体系中的部分关系如下所示：


![](https://img-blog.csdnimg.cn/20200710131404548.png)



---
## 2. Python标准警告总结

- Warning：警告的基类
- DeprecationWarning：关于被弃用的特征的警告
- FutureWarning：关于构造将来语义会有改变的警告
- UserWarning：用户代码生成的警告
- PendingDeprecationWarning：关于特性将会被废弃的警告
- RuntimeWarning：可疑的运行时行为(runtime behavior)的警告
- SyntaxWarning：可疑语法的警告
- ImportWarning：用于在导入模块过程中触发的警告
- UnicodeWarning：与Unicode相关的警告
- BytesWarning：与字节或字节码相关的警告
- ResourceWarning：与资源使用相关的警告

**Try except 异常处理**

try 语句按照如下方式工作：
- 首先，执行`try`子句（在关键字`try`和关键字`except`之间的语句）
- 如果没有异常发生，忽略`except`子句，`try`子句执行后结束。
- 如果在执行`try`子句的过程中发生了异常，那么`try`子句余下的部分将被忽略。如果异常的类型和`except`之后的名称相符，那么对应的`except`子句将被执行。最后执行`try - except`语句之后的代码。
- 如果一个异常没有与任何的`except`匹配，那么这个异常将会传递给上层的`try`中。

```python
try:
    int("abc")
    s = 1 + '1'
    f = open('test.txt')
    print(f.read())
    f.close()
except OSError as error:
    print('打开文件出错\n原因是：' + str(error))
except TypeError as error:
    print('类型出错\n原因是：' + str(error))
except ValueError as error:
    print('数值出错\n原因是：' + str(error))

# 数值出错
# 原因是：invalid literal for int() with base 10: 'abc'
```

```python
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
finally:
    无论如何都会被执行的代码

不管`try`子句里面有没有发生异常，`finally`子句都会执行。



【例子】如果一个异常在`try`子句里被抛出，而又没有任何的`except`把它截住，那么这个异常会在`finally`子句执行后被抛出。

```

```python
try:
    检测范围
except:
    出现异常后的处理代码
else:
    如果没有异常执行这块代码
    
使用`except`而不带任何异常类型，这不是一个很好的方式，我们不能通过该程序识别出具体的异常信息，因为它捕获所有的异常。

try:
    检测范围
except(Exception1[, Exception2[,...ExceptionN]]]):
   发生以上多个异常中的一个，执行这块代码
else:
    如果没有异常执行这块代码
```

**raise**

```python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    
# An exception flew by!
```

