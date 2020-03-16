---
layout: post
catogories:
  - Matlab
tags: Matlab
---

# Matlab中scatter画2维图

`scatter(`x,`y`)，x是横坐标，y是纵坐标

`scatter(`x,`y`,`sz`)，sz是散点圆的直径

`scatter(`x,`y`,`sz`,`c`)，c是散点的颜色

`scatter(___,`'filled')，用实心点代替空心点

`scatter(___,`Name,Value) ，通过附加name和value，添加散点属性，比如内外颜色

```matlab
x = linspace(0,3*pi,200);%0--3pi范围内取200个点
y = cos(x) + rand(1,200);
scatter(x,y)
x = linspace(0,3*pi,200);
y = cos(x) + rand(1,200);
c = linspace(1,10,length(x));%c也是一个200点的范围1--10的向量
scatter(x,y,[],c)
```

原博客http://blog.sina.com.cn/s/blog_d12747080102xra5.html