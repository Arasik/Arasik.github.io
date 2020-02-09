---
layout: post
categories:
  - C++
tags: C++
---

<h1>C++简单模板template</h1>

需要多个对不同类型使用同一种算法的函数，可以使用模板。通过将类型作为参数传递给模板，可使编译器生成该类型的函数。

```c++
#include <iostream>
template <typename T>
double add(T a,T b){//模板
    return a+b;
}
template <class T>
void Swap(T &a,T &b){//模板
    T temp=a;
    a=b;
    b=temp;
}
int main() {
    using namespace std;
    double x=1;
    double y=2;
    cout<<add(x,y)<<endl;
    Swap(x,y);
    cout<<x<<" "<<y<<endl;
    return 0;
}

```

模板也有很多局限性，比如当T是数组的时候下面的操作将无法执行

```c++
x=y;
```

还有当 x 和y为不同类型的时候

```c++
char x;
double y;
add(x,y);
```

这样会出错