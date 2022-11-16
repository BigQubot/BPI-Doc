math - 数学运算函数
=====================================

这个模块实现了相应 CPython 模块的一个子集，如下所述。有关更多信息，请参阅原始CPython文档:[math](https://docs.python.org/zh-cn/3/library/math.html#module-math).

该 ``math`` 模块提供了一些处理浮点数的基本数学函数.

*注意:* 在pyboard上，浮点数具有32位精度.


Functions
---------

```python
acos(x)
```
  返回的反余弦值 ``x``.

```python
acosh(x)
```
   返回反双曲余弦值 ``x``.

```python
asin(x)
```
   R返回反正弦 ``x``.

```python
asinh(x)
```
   返回反双曲正弦 ``x``.

```python
atan(x)
```
   返回反正切 ``x``.

```python
atan2(y, x)
```
   返回反正切的主值 ``y/x``.

```python
atanh(x)
```
  返回反双曲正切值 ``x``.

```python
ceil(x)
```
   返回一个整数， ``x`` 向正无穷大舍入.
   

```python
copysign(x, y)
```
   回来 ``x`` 的标志 ``y`` .

```python
cos(x)
```
   返回余弦 ``x``.

```python
cosh(x)
```
   返回的双曲余弦值 ``x``.

```python
degrees(x)
```
   返回弧度 ``x`` 转换为度数.

```python
erf(x)
```
   返回错误函数 ``x``

```python
erfc(x)
```
   返回互补误差函数  ``x``.

```python
exp(x)
```
   返回指数 ``x``.

```python
expm1(x)
```
   返回 ``exp(x) - 1``.

```python
fabs(x)
```
   返回绝对值 ``x``.

```python
floor(x)
```
   返回一个整数， ``x`` 向负无穷大舍入。

```python
fmod(x, y)
```
   归还剩下的 ``x/y``.

```python
frexp(x)
```
将浮点数分解为尾数和指数。返回的值是元组 ``(m, e)`` 这样 ``x == m * 2**e`` 
完全正确。如果 ``x == 0`` ，则函数返回 ``(0.0,0)`` ，否则``0.5 <= abs(m) < 1``.

```python
gamma(x)
```
   返回的伽玛函数 ``x``.

```python
isfinite(x)
```
   如果 ``x`` 是有限,则返回 ``True``.

```python
isinf(x)
```
   如果 ``x`` 是无限,则返回 ``True``.

```python
isnan(x)
```
   如果 ``x`` 不是数字,则返回 ``True``.

```python
ldexp(x, exp)
```
   返回 ``x * (2**exp)``.

```python
lgamma(x)
```
   返回伽玛函数的自然对数 ``x``.

```python
log(x)
```
   返回自然对数 ``x``.

```python
log10(x)
```
  返回基数为10的对数 ``x``.

```python
log2(x)
```
  返回基数为2的对数 ``x``.

```python
modf(x)
```
   返回一个由两个浮点数组成的元组，它是数字的分数和不可分割的部分 `` x`` .两个返回值都具有相同的符号 ``x`` .

```python
pow(x, y)
```
   返回  ``x `` 的 ``y`` 次方.

```python
radians(x)
```
   返回 ``x`` 度转换为弧度.

```python
sin(x)
```
   回归正弦 ``x``.

```python
sinh(x)
```
  返回双曲线的正弦曲线 ``x``.

```python
sqrt(x)
```
  返回平方根  ``x``.

```python
tan(x)
```
   返回正切值 ``x``.

```python
tanh(x)
```
   返回双曲正切值 ``x``.

```python
trunc(x)
```
  返回一个整数， ``x`` 向0舍入.

Constants
---------

``e`` 自然对数的底

``pi`` 圆周长与直径之比
