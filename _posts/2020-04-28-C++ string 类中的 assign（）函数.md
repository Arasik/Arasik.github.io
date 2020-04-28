---
layout: post
categories:
  - C++
tags: C++
---

# C++ string和vector assign（）函数

C++ string 类的成员函数，用于拷贝、赋值操作，它们允许我们顺次地把一个 string 对象的部分内容拷贝到另一个 string 对象上。

# 函数原型

```
string &operator=(const string &s);　　  　　　　　　　　　　　把字符串s赋给当前字符串
string &assign(const char *s);　　　　　　　　　　　　　　　　　用c类型字符串s赋值
string &assign(const char *s,int n);　　　　　　　　　　　　　 用c字符串s开始的n个字符赋值
string &assign(const string &s);　　　　　　　　　　　　　　　  把字符串s赋给当前字符串
string &assign(int n,char c);　　　　　　　　　　　　　　　　　 用n个字符c赋值给当前字符串
string &assign(const string &s,int start,int n);　　　　　　 把字符串s中从start开始的n个字符赋给当前字符串
string &assign(const_iterator first,const_itertor last);　　把first和last迭代器之间的部分赋给字符串
```

函数以下列方式赋值：

　　用str为字符串赋值；

　　用str的开始num个字符为字符串赋值；

　　用str的子串为字符串赋值,子串以index索引开始，长度为len；

　　用num个字符ch为字符串赋值。

# 成员函数

```
void assign(input_iteratorstart,input_iteratorend );
void assign( size_type num, constTYPE&val );
```

assign() 函数要么将区间[start, end)的元素赋到当前vector,或者赋num个值为val的元素到vector中.这个函数将会清除掉为vector赋值以前的内容。

## vector中的使用

函数原型：

```c++
void assign(const_iterator first,const_iterator last);
void assign(size_type n,const T& x = T());
```

功能：

将区间[first,last)的元素赋值到当前的vector容器中，或者赋n个值为x的元素到vector容器中，这个容器会清除掉vector容器中以前的内容。

例如

```c++
vector<int> v2={};
v2.assign(5,0);
for(int i=0;i<v2.size();i++){
cout<<v2[i]<<" ";
}
结果：0 0 0 0 0
```

