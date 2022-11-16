uheapq - 堆队列算法
=====================================

这个模块实现了相应 CPython 模块的一个子集，如下所述。有关更多信息，请参阅原始CPython文档: [heapq](https://docs.python.org/zh-cn/3/library/heapq.html#module-heapq)

T该模块实现堆队列算法。

堆队列只是一个以某种方式存储其元素的列表。

函数
---------

```python
heappush(heap, item)
```
将 ``item`` 载入 ``heap`` 中。

```python
heappop(heap)
```
从 ``heap`` 中提取首个项，并返回。若堆为空，则引发Index错误。

```python
heapify(x)
```
将列表 ``x`` 转换为一个堆。此为就地操作。
