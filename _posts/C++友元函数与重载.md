---
layout: post
categories:
  - C++
tags: C++
---

<h1>C++友元函数与重载</h1>

在讲友元函数之前我们要说说重载的一些局限性，来看看下面的这个例子

```c++
Time Time::operator*(double mult)const{
    ....//具体实现方法就不写了
}
A=B*2.75;//A and B both Time class
A=2.75*B;
```

第一个赋值操作可以正常运行，他使用重载将B和2.75向乘，即

```c++
A=B.operator*(2.75);
```

但是第二赋值操作将无法执行。

其中一个解决方案就是用非成员函数

```c++
Time operator*(double mult,const Time &t);
```

但是这就引出了一个问题，在非成员函数中我们不能访问对象的私有成员，至少常规非成员函数不能访问，然而，有一类特殊的非成员函数可以访问类的私有成员，这就是友元函数。

对上面的例子我们就可以用下面的例子解决

```c++
friend Time operator*(double mult,const Time &t);
```

1）必须在类的说明中说明友元函数，说明时以关键字friend开头，后跟友元函数的函数原型，友元函数的说明可以出现在类的任何地方，包括在private和public部分；
2）注意友元函数不是[类的成员函数](https://www.baidu.com/s?wd=类的成员函数&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)，所以友元函数的实现和普通函数一样，在实现时不用"::"指示属于哪个类，只有成员函数才使用"::"作用域符号；

<h3>重载<<运算符</h3>

如果单纯使用重载的话会出现

```c++
trip<<cout;
```

这种令人迷惑的情况。

如果修改iostream文件是一个危险的主意，这时候友元就有用了。

```c++
void operator<<(ostream & os,const Time &t){
	os<<t.hours<<"hours"<<t.minutes<<"minutes";
}
```

这样就可以使用

```c++
cout<<trip;
```

但是这样还有一个问题

```c++
cout<<"trip time"<<trip<<"tuseday\n";
```

这条语句是不能执行的原因在于iostream中要求<<运算符左边是一个ostream对象，所以我们应该改成返回指向ostream对象的引用

```c++
ostream & operator<<(ostream &os,const Time &t){
	os<<t.hours<<"hours"<<t.minutes<<"minutes";
	return os;
}
```

下面是练习写的例子

```c++
//
// Created by kisara on 2020/2/2.
//

#ifndef OPERATOR_OVERLOAD_CHARACTERS_H
#define OPERATOR_OVERLOAD_CHARACTERS_H

class character {
private:
    char c;

public:
    character();
    character(char c);
    char getc()const ;
    character operator+(const character &a)const ;//类和类相加
    void show();
    friend character operator +(int x,const character &c2);//友元
};


#endif //OPERATOR_OVERLOAD_CHARACTERS_H

```

```c++
#include <iostream>
#include "characters.h"
character::character() {
    this->c='0';
}
character::character(char c) {
    this->c=c;
}
character character::operator+(const character &a) const {
    character temp;
    temp.c=a.c+this->c-'a';
    return temp;
}
void character::show() {
    std::cout<<this->c;
}
char character::getc() const {
    return this->c;
}
character operator +(int x,const character &c2){//友元
    character temp;
    temp.c=x+c2.c;
    return temp;
}
```

```c++
#include <iostream>
#include "characters.h"
char operator +(const char x, const character &c){//非成员函数重载
    char temp;
    temp=x+c.getc()-'a';
    return temp;
}


int main() {
    character p=character('b');
    character q=character('f');
    character w=p+q;
    p=3+p;
//    std::cout<<p;
    p.show();
    w.show();
    return 0;
}

```

