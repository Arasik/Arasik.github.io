---
layout: post
catogories:
  - Matlab
tags: Matlab
---

# Matlab inline有什么用

```matlab
myfunc=inline('x*x','x')
myfunc(5)
```

inline()第一个参数是表达式，即具体方程

第二个指出方程的变量

然后就可以像调用函数一样调用myfunc