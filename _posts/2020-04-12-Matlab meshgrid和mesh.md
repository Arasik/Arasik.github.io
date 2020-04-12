---
layout: post
catogories:
  - Matlab
tags: Matlab
---

# Matlab meshgrid和mesh

```matlab
x=[1:3]
y=[4:5]
[m,n]=meshgrid(x,y)
mesh(m,n)
```

```
运行结果
m =

     1     2     3
     1     2     3


n =

     4     4     4
     5     5     5
```



从结果我们可以看出meshgrid的结果就像2个循环输出一样

```matlab
%m
for i=y
    for j=x
        fprintf('%d\t',j)
    end
    fprintf('\n')
end
% n
for i=y
    for j=x
        fprintf('%d\t',i)
    end
    fprintf('\n')
end
```



mesh用于绘制不是特别精细的三维曲面网格图。同一层面的线条用相同的颜色表示。

surf用于绘制比zhidao较光滑的三维曲面网格图。各线条之间的补面用颜色填充。