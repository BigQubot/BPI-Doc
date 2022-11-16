ure - 正则表达式
========================================

这个模块实现了相应 CPython 模块的一个子集，如下所述。有关更多信息，请参阅原始CPython文档: [re](https://docs.python.org/zh-cn/3/library/re.html#module-re)

该模块实现正则表达式操作。支持的正则表达式语法是CPython re 模块的一个子集（实际上是POSIX扩展正则表达式的子集）。

支持的操作符和特殊序列是:

``.``
匹配任何字符。

``[···]``
匹配字符集。支持单个字符和范围，包括负集(例如 [^a-c])。

``^``
匹配字符串的开头。

``$``
匹配字符串的结尾。

``?``
匹配零个或前面的子模式之一。

``*``
匹配零个或多个先前的子模式。

``+``
匹配一个或多个先前的子模式。

``??``
Non-greedy版本的 ? ，匹配0或1，偏好零。
``*?``
Non-greedy版本的 * ，匹配零个或多个，并偏好最短的匹配。
``+?``
Non-greedy版本的 + ，匹配一个或多个，并偏好最短的匹配。
``(···)``
分组。每个组都在捕获(它捕获的子字符串可以通过`match.group()`方法访问)。

`\d`

数字匹配。相当于 `[0-9]` 。

`\D`

非数字匹配。相当于 `[^0-9]` 。

`\s`

匹配空格。相当于 `[ \t-\r]` 。

`\S`

匹配非空格。相当于 `[^ \t-\r]` 。

`\w`

匹配”单词字符” (仅限ASCII)。\[相当于 `[A-Za-z0-9_]` 。

`\W`

匹配非“单词字符”（仅限ASCII）。相当于 `[^A-Za-z0-9_]` 。

`\`

转义字符。反斜杠后的任何其他字符（上面列出的字符除外）均按字面意义使用。例如，`\*` 是相当于文本 `*``（不作为 ``*` 运算符处理）。 请注意，`\r`, `\n` 等没有特别处理，将相当于字面字母 `r`, `n` 等。因此不建议将原始Python字符串（ `r""` ）用于常规表达。 例如，`r"\r\n"` 用作常规表达式等价于 `"rn"` 。若要匹配后跟LF的CR字符，请使用 `"\r\n"` 。

**不支持**：

*   重复次数 (`{m,n}`)
    
*   命名组 (`(?P<name>...)`)
    
*   非捕获组(`(?:...)`)
    
*   更高级的断言(`\b`, `\B`)
    
*   特殊字符转义，如 `\r`, `\n` \- 改用Python自己的转义
    
*   等等。

例子:
```python
import ure

# As ure doesn't support escapes itself, use of r"" strings is not recommended.
# 由于ure本身不支持转义，所以不推荐使用r""字符串

regex = ure.compile("[\r\n]")

regex.split("line1\rline2\nline3\r\n")

# 结果:
# ['line1', 'line2', 'line3', '', '']
```

函数
---------

```python
ure.compile(regex_str)
```
编译正则表达式，返回 `正则表达式对象`。

```python
match(regex_str, string)
```
将 正则表达式对象 与 `string` 匹配。匹配通常从字符串的起始位置进行。

```python
ure.search(regex_str, string)
```
在 `string` 中搜索 正则表达式对象 。与 `match` 不同，这将首先搜索与正则表达式相匹配的字符串（若正则表达式固定，则字符串为0）。

```python
ure.sub(regex_str, replace, string, count=0, flags=0)
```
编译 regex_str 并在 string 中搜索它，用 replace 替换所有匹配项，然后返回新字符串。

replace 可以是字符串或函数。如果是字符串，则可以使用格式为 `\<number>` 和 `\g<number>` 的转义序列扩展到相应的组（对于不匹配的组，则为空字符串）。 如果 replace 是一个函数，则它必须采用单个参数（匹配项）并应返回替换字符串。

如果指定了 count ，并且非零，那么在进行了相应次数的替换之后，替换将停止。忽略 flags 参数。

注意：此方法的可用性取决于 `MicroPython port` 。

```python
ure.DEBUG
```

标记值，显示有关已编译表达式的调试信息。



正则表达式对象
-------------

编译正则表达式。该类实例使用`ure.compile()`创建。

```python
regex.match(string)
regex.search(string)
regex.sub(replace, string, count\=0, flags\=0)
```
与模块级函数 `match()` 和 `search()` 相似。若将同一正则表达式应用于多个字符串，则使用该方法会大大提高效率。

```python
regex.split(string, max\_split\=\- 1)
```
使用正则表达式拆分字符串。若给定，则指定将拆分的最大数量。返回字符串列表（若指定，则可能会有多达 max\_split+1 个元素）。

## Match 对象

匹配由 `match()` 和 `search()` 方法返回的对象。 并传递给 `sub()` 中的替换函数。

```python
match.group(index)
```
返回匹配（子）字符串。若完全匹配 index 为0， 对于每个捕获组为1或更多。 仅支持数字组。

```python
match.groups()
```
返回一个包含该匹配组的所有子字符串的元组。

注意：此方法的可用性取决于 `MicroPython port` 。

```python
match.start(\[index\])
match.end(\[index\])
```
返回匹配的子字符串组的起始或结束的原始字符串中的索引。index 默认为整个组，否则将选择一个组。

注意：这些方法的可用性取决于 `MicroPython port` 。

```python
match.span(\[index\])
```
返回2元组 `(match.start(index), match.end(index))` 。

注意：此方法的可用性取决于 `MicroPython port` 。