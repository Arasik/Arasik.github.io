---
layout: post
catogories:
  - Matlab
tags: Matlab
---

# Matlab solve,fsolve和dsolve

## solve (符号解)

1.syms 指出符号变量

2.eqn用来储存方程

3.注意（eqn，x）中x是说明eqn这个方程中x为变量。

```matlab
syms x m a
eqn=-x^2-x+2*a*x-2*m
m=solve(eqn,x)% 符号解
```

## solve 解方程

```matlab
syms x y;
eq1=x+2*y-8
eq2=3*x+5*y-4
s=solve(eq1,eq2,x,y)
s.x调出x的解
s.y调出y的解
```

solve 函数的局限性

1. 对于非多项式方程，只能求出一个解
2. 对于稍许复杂的方程，求解结果出现很大误差
3. 求解复杂的多项式方程时，可能会产生错误的求解结果
4. 求解复杂的多项式方程时，可能无法求解，且非常耗时
5. 求解超越方程时，只能返回一个解；
6. 求解超越方程时，可能返回错误解；

## fsolve (数值解)

直接求解，代码如下：

```
x=fsolve(@(x)sin(x)-0.5,[1 3])%此处采用匿名函数法@(x)
```

其中1和3分别是设定的两个初值，一般设定在解附近，若不知道

解，也可随意设置，如果解不知最优，会有一定影响.options不填则默认。

非线性方程组的求解

对于非线性方程组F(X)=0，用fsolve函数求其数值解。fsolve函数的调用格式为：

```matlab
   X=fsolve('fun',X0,option)
```



* 其中X为返回的解，fun是用于定义需求解的非线性方程组的函数文件名，X0是求根过程的初值，option为最优化工具箱的选项设定。最优化工具箱提供了20多个选项，用户可以使用optimset命令将它们显示出来。如果想改变其中某个选项，则可以调用optimset()函数来完成。例如，Display选项决定函数调用时中间结果的显示方式，其中‘off’为不显示，‘iter’表示每步都显示，‘final’只显示最终结果。optimset(‘Display’,‘off’)将设定Display选项为‘off’。
  ————————————————
  版权声明：本文为CSDN博主「xmjdh」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
  原文链接：https://blog.csdn.net/lqhbupt/article/details/18009015

* fsolve可以求解方程(组) 的实数根和复数根
  fsolve采用迭代的数值算法，速度快
  给定不同的初值，可以求得不同的根(局部寻根)
  初值给的不好，可能导致求解失败
  关于初值如何给定的问题
  a) 一元/ 二元方程(组)，通过图解法，可以得到根的个数，并粗略地估计出根的值，用做fsolve的初值
  b) 根据方程组中变量的实际意义，合适地给出初值。例如，时间/ 长度/ 质量等物理量，应该大于0
  c) 通过更多的练习和经验积累，自然会见多识广
  ————————————————
  版权声明：本文为CSDN博主「powerlwj」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
  原文链接：https://blog.csdn.net/Power1_Power2/article/details/82893867

```matlab
[m,fv,ef]=fsolve(@(x)3*x^4+4*x^3-20*x+5,0)
```



​	**其中fv为真实值与拟合值之间的差**

## dsolve

dsolve函数用于求常微分方程组的精确解，也称为常微分方程的符号解。如果没有初始条件或边界条件，则求出通解；如果有，则求出特解。

```matlab
syms u(t) 
Du=diff(t)
dsolve(diff(u)==t)
```

https://blog.csdn.net/lynn15600693998/article/details/86597068