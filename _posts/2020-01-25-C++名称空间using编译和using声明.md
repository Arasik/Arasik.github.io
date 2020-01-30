---
layout: post
categories:
  - C++
tags: C++
---



<h1> C++名称空间using编译和using声明</h1>
```c++
namespace jack{
    double bucket(double n){}
    double fetch;
    struct hill{};
}
namespace jill{
    double fetch;
    double bucket(double n){}
    struct hill{};
}
```

using 编译直接导入名称空间：

```c++
using namespace jack;
```

using 声明导入指定名称：

```c++
using jack::fetch;
```

一般来说使用using 声明比使用using 编译指令更安全，这是由于它只导入指定的名称，当有局部变量与该名称冲突时，编译器就会发出指示，而using编译导入整个名称空间时会局部变量会覆盖名称空间版本，而编译器不会发出警告，另外，名称空间的开放性意味着名称空间的名称可能分散在多个地方，这使得难以准确知道添加了哪些名称。