---
layout: post
categories:
  - python
tags: python
---



<h1> 
    Numpy(Numeric Python)
</h1>

```python
import numpy as np
aArray = np.ones((3,4))
print(aArray)
print(type(aArray))

t1 = np.arange(12)#类似于range函数 但是返回的是array对象
print(t1)
print(t1.shape)

t2=np.array([[1,2,3],[4,5,6]])
print(t2)
print(t2.shape)#输出t2的行数和列数 有几个值就是几维数组
```

python 本来的list类型 没有array快

```python
#encoding=utf-8
import numpy as np
def main():
    lst=[[1,3,5],[2,4,6]]
    np_lst=np.array(lst)
    print(np_lst)
    print("np_lst的类型是",type(np_lst))
    np_lst=np.array(lst,dtype=np.float)
    #bool int int8 int16 int32 int64 int128 uint...float...complex...
    print(np_lst)
    print(np_lst.shape)#输出行数和列数
    print("他的维度为=",np_lst.ndim)#输出他的维度
    print("他的数据类型为:",np_lst.dtype)
    print(np_lst.itemsize)#np中每个元素的占用大小
    print(np_lst.size)#np的元素个数
    k=np.zeros([3,4])#产生0
    print(k)
    print('ones=')
    k=np.ones((3,2))
    print(k)##产生多个1 可以用中括号也可以用圆括号
    k=np.random.rand(3,4)#产生随机数
    print('rand=')
    print(k)
    k=np.random.randint(1,10,3)#产生随机整数均匀分布的
    print('randint=')
    print(k)
    k=np.random.randn(2,4)#随机正态分布的
    print('randn=')
    print(k)
    k=np.random.choice([10,20,30,25])#从这个列表里面随便选
    print(k)
    k=np.random.beta(1,10,100)
    print(k)
    pass
'''Python pass 是空语句，是为了保持程序结构的完整性。
pass 不做任何事情，一般用做占位语句。'''
if __name__ == '__main__':
    main()
```



**第一种导入方式：**

```
import numpy1
```

这是导入了整个numpy模块，需要使用句点表示法访问需要的类。例如：

```
a = numpy.array([1,1])
```

**第二种导入方式：**

```
from numpy import *
```

这是导入了numpy模块的每个类，可以直接使用类，无需句点表示法。例如：

```
a = arrry([1,1])1
```

不推荐使用第二种导入方式，其没有明确地指出你使用了模块中的哪些类。并且，如果导入了一个与程序文件中其他东西同名的类，会引发难以发现的错误。



**numpy的矩阵操作和线性方程组**

```python
from numpy.linalg import *
import numpy as np
def main():
    lst=np.array([[1.,2.],
                  [3.,4.]])
    print("inv")
    print(inv(lst))#逆矩阵
    print("T:")
    print(lst.transpose())#转置
    print("Det:")
    print(det(lst))#行列式
    print(eig(lst))#求特征值和特征向量
    y=np.array([[5.],[7.]])
    print(solve(lst,y))#解线性方程组
if __name__ == '__main__':
    main()
```

