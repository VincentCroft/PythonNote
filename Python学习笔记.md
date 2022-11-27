# Python学习笔记

## 1.Python 编程基础

### 1.1Python 注释规则

注释（Comments）用来向用户提示或解释某些代码的作用和功能，它可以出现在代码中的任何位置。[Python](http://c.biancheng.net/python/) 解释器在执行代码时会忽略注释，不做任何处理，就好像它不存在一样。

在调试（Debug）程序的过程中，注释还可以用来临时移除无用的代码。

Python 支持两种类型的注释，分别是单行注释和多行注释

#### 一.Python 单行注释

Python 使用井号`#`作为单行注释的符号，语法格式为：

> \# 注释内容

注意：从井号`#`开始，直到这行结束为止的所有内容都是注释。Python 解释器遇到`#`时，会忽略它后面的整行内容

**Tips：**

（1）说明多行代码的功能时一般将注释放在代码的上一行，例如：

```python
#使用print输出字符串
print("Hello World!")
print("C语言中文网")
print("http://c.biancheng.net/python/")
#使用 print输出数字
print(100)
print( 3 + 100 * 2)
print( (3 + 100) * 2 )
```

（2）说明单行代码的功能时一般将注释放在代码的右侧，例如：

```python
print("http://c.biancheng.net/python/")  #输出Python教程的地址
print( 36.7 * 14.5 )  #输出乘积
print( 100 % 7 )  #输出余数
```

#### 二.Python 多行注释

多行注释指的是一次性注释程序中多行的内容（包含一行）。

Python 使用三个连续的单引号'''或者三个连续的双引号"""注释多行内容，具体格式如下：

```python
'''
使用 3 个单引号分别作为注释的开头和结尾
可以一次性注释多行内容
这里面的内容全部是注释内容
'''
```

或者

```py
"""
使用 3 个双引号分别作为注释的开头和结尾
可以一次性注释多行内容
这里面的内容全部是注释内容
"""
```

注意：多行注释通常用来为 Python 文件、模块、类或者函数等添加版权或者功能描述信息。

#### 三.注释注意事项

1) Python 多行注释不支持嵌套，所以下面的写法是**错误**的：

```python
'''
外层注释
    '''
    内层注释
    '''
'''
   
```

2. 不管是多行注释还是单行注释，当注释符作为字符串的一部分出现时，就不能再将它们视为注释标记，而应该看做正常代码的一部分，例如：

```py
print('''Hello,World!''')
print("""http://c.biancheng.net/cplus/""")
print("#是单行注释的开始")
```

以下为以上代码的运行结果：

```
Hello,World!
http://c.biancheng.net/cplus/
#是单行注释的开始
```

> 解读：
>
> 对于前两行代码，Python 没有将这里的三个引号看作是多行注释，而是将它们看作字符串的开始和结束标志。
>
> 对于第 3 行代码，Python 也没有将井号看作单行注释，而是将它看作字符串的一部分。

### 1.2Python 缩进规则

[Python](http://c.biancheng.net/python/) 采用代码缩进和冒号（ : ）来区分代码块之间的层次。

在 Python 中，对于类定义、函数定义、流程控制语句、异常处理语句等，行尾的冒号和下一行的缩进，表示下一个代码块的开始，而缩进的结束则表示此代码块的结束。

> 注意：Python 中实现对代码的缩进，可以使用空格或者 Tab 键实现。但无论是手动敲空格，还是使用 Tab 键，通常情况下都是采用 4 个空格长度作为一个缩进量（默认情况下，一个 Tab 键就表示 4 个空格）。

例子：下面这段 Python 代码中

```python
height=float(input("输入身高：")) #输入身高
weight=float(input("输入体重：")) #输入体重
bmi=weight/(height*height)       #计算BMI指数
#判断身材是否合理
if bmi<18.5:
    #下面 2 行同属于 if 分支语句中包含的代码，因此属于同一作用域
    print("BMI指数为："+str(bmi)) #输出BMI指数
    print("体重过轻")
if bmi>=18.5 and bmi<24.9:
    print("BMI指数为："+str(bmi)) #输出BMI指数
    print("正常范围，注意保持")
if bmi>=24.9 and bmi<29.9:
    print("BMI指数为："+str(bmi)) #输出BMI指数
    print("体重过重")
if bmi>=29.9:
    print(BMI指数为："+str(bmi)) #输出BMI指数
    print("肥胖")
```

**Python 对代码的缩进要求非常严格，同一个级别代码块的缩进量必须一样，否则解释器会报 SyntaxError 异常错误。例如，对上面代码做错误改动，将位于同一作用域中的 2 行代码，它们的缩进量分别设置为 4 个空格和 3 个空格，如下所示：**

```python
if bmi<18.5:
    print("BMI指数为："+str(bmi)) #输出BMI指数
   print("体重过轻")
```

可以看到，第二行代码和第三航代码本来属于同一作用域，但我们手动修改了各自的缩进量，这会导致 SyntaxError 异常错误，如下图所示。

![](http://c.biancheng.net/uploads/allimg/190624/1-1Z624120Z3360.jpg)

对于 Python 缩进规则，初学者可以这样理解，Python 要求属于同一作用域中的各行代码，它们的缩进量必须一致，但具体缩进量为多少，并不做硬性规定。

### 1.3Python 编码规范

![](http://c.biancheng.net/uploads/allimg/190624/1-1Z62414494a07.jpg)

对比上图的两段代码你会发现，它们所包含的代码时完全相同的，但很明显，右侧的代码编写格式看上去比左侧的代码段更加规整，阅读起来也会比较轻松、畅快，因为它遵循了最基本的 Python 代码编写规范。

Python 采用 PEP 8 作为编码规范，其中 PEP 是 Python Enhancement Proposal（Python 增强建议书）的缩写，8 代表的是 Python 代码的样式指南。下面仅给大家列出 PEP 8 中初学者应严格遵守的一些编码规则：

> 1.每个 import 语句只导入一个模块，尽量避免一次导入多个模块，例如：

```python
#推荐
import os
import sys
#不推荐
import os,sys
```

> 2.不要在行尾添加分号，也不要用分号将两条命令放在同一行，例如：

```python
#不推荐
height=float(input("输入身高：")) ; weight=fioat(input("输入体重：")) ;
```

> 3.建议每行不超过 80 个字符，如果超过，建议使用小括号将多行内容隐式的连接起来，而不推荐使用反斜杠 \ 进行连接。例如，如果一个字符串文本无法实现一行完全显示，则可以使用小括号将其分开显示，代码如下：

```python
#推荐
s=("C语言中文网是中国领先的C语言程序设计专业网站，"
"提供C语言入门经典教程、C语言编译器、C语言函数手册等。")
#不推荐
s="C语言中文网是中国领先的C语言程序设计专业网站，\
提供C语言入门经典教程、C语言编译器、C语言函数手册等。"
```

**注意：此编程规范适用于绝对大多数情况，但以下 2 种情况除外**

- **导入模块的语句过长。**
- **注释里的 URL。**

> 4.使用必要的空行可以增加代码的可读性，通常在顶级定义（如函数或类的定义）之间空两行，而方法定义之间空一行，另外在用于分隔某些功能的位置也可以空一行。比如说，在上图右侧这段代码中，if 判断语句同之前的代码多实现的功能不同，因此这里可以使用空行进行分隔。

> 5.通常情况下，在运算符两侧、函数参数之间以及逗号两侧，都建议使用空格进行分隔。

### 1.4Python 标识符命名规范

简单地理解，标识符就是一个名字，就好像我们每个人都有属于自己的名字，它的主要作用就是作为变量、函数、类、模块以及其他对象的名称。

[Python](http://c.biancheng.net/python/) 中标识符的命名不是随意的，而是要遵守一定的命令规则，比如说：

1. 标识符是由字符（A~Z 和 a~z）、下划线和数字组成，但第一个字符不能是数字。
2. 标识符不能和 Python 中的保留字相同。
3. Python中的标识符中，不能包含空格、@、% 以及 $ 等特殊字符。

> 下面所列举的标识符是合法的：

```python
UserID
name
mode12
user_age
```

> 下面所列举的标识符不合法：

```
4word    #不能以数字开头
try          #try是保留字，不能作为标识符
$money #不能包含特殊字符
```

4.在 Python 中，标识符中的字母是严格区分大小写的，也就是说，两个同样的单词，如果大小格式不一样，多代表的意义也是完全不同的。比如说，下面这 3 个变量之间，就是完全独立、毫无关系的，它们彼此之间是相互独立的个体。

```python
number = 0
Number = 0
NUMBER = 0
```

5.Python 语言中，以下划线开头的标识符有特殊含义，例如：

- 以单下划线开头的标识符（如 _width），表示不能直接访问的类属性，其无法通过 from...import* 的方式导入
- 以双下划线开头的标识符（如__add）表示类的私有成员
- 以双下划线作为开头和结尾的标识符（如 __init__），是专用标识符

> **因此，除非特定场景需要，应避免使用以下划线开头的标识符。**
>
> **另外需要注意的是，Python 允许使用汉字作为标识符，例如:**
>
> ```python
> C语言中文网 = "http://c.biancheng.net"
> ```

6.标识符的命名，除了要遵守以上这几条规则外，不同场景中的标识符，其名称也有一定的规范可循

> - **当标识符用作模块名时，应尽量短小，并且全部使用小写字母，可以使用下划线分割多个字母，例如 game_mian、game_register 等。**
> - **当标识符用作包的名称时，应尽量短小，也全部使用小写字母，不推荐使用下划线，例如 com.mr、com.mr.book 等。**
> - **当标识符用作类名时，应采用单词首字母大写的形式。例如，定义一个图书类，可以命名为 Book。**
> - **模块内部的类名，可以采用 "下划线+首字母大写" 的形式，如 _Book;**
> - **函数名、类中的属性名和方法名，应全部使用小写字母，多个单词之间可以用下划线分割；**
> - **常量命名应全部使用大写字母，单词之间可以用下划线分割；**

### 1.5Python 关键字

保留字是 [Python](http://c.biancheng.net/python/) 语言中一些已经被赋予特定意义的单词，这就要求开发者在开发程序时，不能用这些保留字作为标识符给变量、函数、类、模板以及其他对象命名。

Python 包含的保留字可以执行如下命令进行查看：

```python
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

Python 保留字一览表

| and   | as   | assert | break    | class  | continue |
| ----- | ---- | ------ | -------- | ------ | -------- |
| def   | del  | elif   | else     | except | finally  |
| for   | from | False  | global   | if     | import   |
| in    | is   | lambda | nonlocal | not    | None     |
| or    | pass | raise  | return   | try    | True     |
| while | with | yield  |          |        |          |

> **注意：由于 Python 是严格区分大小写的，保留字也不例外。所以，我们可以说 if 是保留字，但 IF 就不是保留字。**

***如果使用 Python 中的保留字作为标识符，则解释器会提示“invalid syntax” 的错误信息。***

### 1.6Python 内置函数

[Python](http://c.biancheng.net/python/) 解释器自带的函数叫做内置函数，这些函数可以直接使用，不需要导入某个模块。

> 概念：
>
> 将使用频繁的代码段封装起来，并给它起一个名字，以后使用的时候只要知道名字就可以，这就是函数。函数就是一段封装好的、可以重复使用的代码，它使得我们的程序更加模块化，不需要编写大量重复的代码

**注意：内置函数和标准库函数是不一样的。**

ython 解释器也是一个程序，它给用户提供了一些常用功能，并给它们起了独一无二的名字，这些常用功能就是内置函数。Python 解释器启动以后，内置函数也生效了，可以直接拿来使用。

Python 标准库相当于解释器的外部扩展，它并不会随着解释器的启动而启动，要想使用这些外部扩展，必须提前导入。Python 标准库非常庞大，包含了很多模块，要想使用某个函数，必须提前导入对应的模块，否则函数是无效的。

内置函数是解释器的一部分，它随着解释器的启动而生效；标准库函数是解释器的外部扩展，导入模块以后才能生效。一般来说，内置函数的执行效率要高于标准库函数。

Python 解释器一旦启动，所有的内置函数都生效了；而导入标准库的某个模块，只是该模块下的函数生效，并不是所有的标准库函数都生效。

内置函数的数量必须被严格控制，否则 Python 解释器会变得庞大和臃肿。一般来说，只有那些使用频繁或者和语言本身绑定比较紧密的函数，才会被提升为内置函数。

| **内置函数表** |
| -------------- |

| abs()         | delattr()   | hash()       | memoryview() | set()          |
| ------------- | ----------- | ------------ | ------------ | -------------- |
| all()         | dict()      | help()       | min()        | setattr()      |
| any()         | dir()       | hex()        | next()       | slicea()       |
| ascii()       | divmod()    | id()         | object()     | sorted()       |
| bin()         | enumerate() | input()      | oct()        | staticmethod() |
| bool()        | eval()      | int()        | open()       | str()          |
| breakpoint()  | exec()      | isinstance() | ord()        | sum()          |
| bytearray()   | filter()    | issubclass() | pow()        | super()        |
| bytes()       | float()     | iter()       | print()      | tuple()        |
| callable()    | format()    | len()        | property()   | type()         |
| chr()         | frozenset() | list()       | range()      | vars()         |
| classmethod() | getattr()   | locals()     | repr()       | zip()          |
| compile()     | globals()   | map()        | reversed()   | __import__()   |
| complex()     | hasattr()   | max()        | round()      |                |

> **注意：不要使用内置函数的名字作为标识符使用（例如变量名、函数名、类名、模板名、对象名等），虽然这样做 Python 解释器不会报错，但这会导致同名的内置函数被覆盖，从而无法使用。**

例子：

```python
>>> print = "http://c.biancheng.net/python/"  #将print作为变量名
>>> print("Hello World!")  #print函数被覆盖，失效
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    print("Hello World!")
TypeError: 'str' object is not callable
```

