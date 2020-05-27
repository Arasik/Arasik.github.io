---
layout: post
categories:
  - C++
tags: C++
---

# include< > 和 include” ” 的区别

**一、#include< >**

　　#include< > 引用的是编译器的类库路径里面的头文件。

　　假如你编译器定义的自带头文件引用在 C:\Keil\c51\INC\ 下面，则 #include<stdio.h> 引用的就是 C:\Keil\c51\INC\stdio.h 这个头文件，不管你的项目在什么目录里， C:\Keil\c51\INC\stdio.h 这个路径就定下来了，一般是引用自带的一些头文件，如： stdio.h、conio.h、string.h、stdlib.h 等等。

**二、#include" "**

　　#include" " 引用的是你程序目录的相对路径中的头文件。

　　假如你的项目目录是在 D:\Projects\tmp\ ，则 #include"my.h" 引用的就是 D:\Projects\tmp\my.h 这个头文件，一般是用来引用自己写的一些头文件。如果使用 #include" " ，它是会先在你项目的当前目录查找是否有对应头文件，如果没有，它还是会在对应的引用目录里面查找对应的头文件。例如，使用 #include "stdio.h" 如果在你项目目录里面，没有 stdio.h 这个头文件，它还是会定位到 C:\Keil\c51\INC\stdio.h 这个头文件的。