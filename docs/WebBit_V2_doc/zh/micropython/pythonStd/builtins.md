builtin - 内建函数
================================

此处描述了所有内置函数和异常。它们也可通过 ``builtins`` 模块获取。

Functions and types
-------------------

```python
abs()

all()

any()

bin()

class bool()

class bytearray()

class bytes()
#参考CPython文档：https://docs.python.org/zh-cn/3/library/functions.html#bytes

callable()

chr()

classmethod()

compile()

class complex()

delattr(obj, name)
#参数名应该是一个string，这个函数从obj给出的对象中删除命名属性.

class dict()

dir()

divmod()

enumerate()

eval()

exec()

filter()

class float()

class frozenset()

getattr()

globals()

hasattr()

hash()

hex()

id()

input()

class int()
    from_bytes(bytes, byteorder)
    #在MicroPython中， `byteorder` 参数必须是位置的（这与CPython兼容）


    to_bytes(size, byteorder)
    #在MicroPython中， `byteorder` 参数必须是位置的（这与CPython兼容）
    

isinstance()

issubclass()

iter()

len()

class list()

locals()

map()

max()

class memoryview()

min()

next()

class object()

oct()

open()

ord()

pow()

print()

property()

range()

repr()

reversed()

round()

class set()

setattr()

class slice()
#slice内置函数是slice对象的类型.

sorted()

staticmethod()

class str()

sum()

super()

class tuple()

type()

zip()
```

Exceptions
----------

```python
exception AssertionError

exception AttributeError

exception Exception

exception ImportError

exception IndexError

exception KeyboardInterrupt

exception KeyError

exception MemoryError

exception NameError

exception NotImplementedError

exception OSError
#参考CPython文档： ``OSError`` . MicroPython不实现 ``errno``  属性，而是使用标准方式访问异常参数： ``exc.args[0]`` .

exception RuntimeError

exception StopIteration

exception SyntaxError

exception SystemExit
#参考CPython文档： ``SystemExit`` .

exception TypeError
#参考CPython文档： ``SystemExit`` .

exception ValueError

exception ZeroDivisionError
```