---
layout: post
categories:
	- 数据结构与算法
tag: 数据结构与算法
---



# 		单源最短路（dijikstra算法）

> 百度百科定义中：给定一个带权[有向图](https://baike.baidu.com/item/%E6%9C%89%E5%90%91%E5%9B%BE/1852743)G=（V,E），其中每条边的权是一个实数。另外，还给定V中的一个顶点，称为源。现在要计算从源到其他所有各顶点的[最短路径](https://baike.baidu.com/item/%E6%9C%80%E7%9F%AD%E8%B7%AF%E5%BE%84/6334920)长度。这里的长度就是指路上各边权之和。这个问题通常称为单源最短路径   问题。

dijikstra算法是一种图算法，其中有用到BFS的思想。他和最小生成树有相同之处，但实际解决的是不同的问题。

我们还是先看个图 我们假定从V1 出发寻找到 其他各个点的最小的代价,然后在算法程序实现的过程中我们会经常用到优先队列

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-%E5%8E%9F%E5%9B%BE2.png"/>

从V1出发 则到V1点的距离为0,表示为（V1,0)  vis[V1]=1   

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-1.png" width="400px"/><img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-queue1.png" width="400px"/>

把V1的邻接点放到队列中  （V5,5) ,(V2,15)  V5的权重最小所以在优先队列中排在最前面

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-2%205.jpg" width="500px"/><img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-qq2.png" width="300px"/>

然后弹出队列第一个元素(V5,5) 则V1到V5的距离为5,vis[v5]=1,继续把为V5的邻接点V4,V6放到队列里面(V4,7),(V6,11) 

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-4%206.jpg" width="500px"/><img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-qq3.png" width="300px"/>

继续弹出V4，vis[V4]=1,把(V2,11) (V6,8)放入优先队列

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-queue4.png" width="500px"/>

接着弹出(v6,8),vis[V6]=1,放入(v3,11)

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-3.jpg" width="500px"/><img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-queue5.png" width="300px"/>

接着弹出(V3,11),vis[V2]=1,放入(v2,21)

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-queue6.png" width="500px"/>

最后弹出(V2,11) vis[V2]=1,到这里从V1出发到所有点的最小代价都算出来了。后面的点由于比原来的距离大所以不用更新。

<img src="https://rpzoss.oss-cn-chengdu.aliyuncs.com/Public/8-16-2019-queue7.png" width="500px"/>

最后我们来做个模板题看看实际的代码实现。

https://www.luogu.org/problem/P4779

### 题目描述

给定一个 N*N* 个点，M*M* 条有向边的带非负权图，请你计算从 S*S* 出发，到每个点的距离。

数据保证你能从 S*S* 出发到任意点。

### 输入格式

第一行为三个正整数 N, M, S*N*,*M*,*S*。 第二行起 M*M* 行，每行三个非负整数 u_i, v_i, w_i*u**i*,*v**i*,*w**i*，表示从 u_i*u**i* 到 v_i*v**i* 有一条权值为 w_i*w**i* 的边。

### 输出格式

输出一行 N*N* 个空格分隔的非负整数，表示 S*S* 到每个点的距离。

### 输入输出样例

输入 #1

```
4 6 1
1 2 2
2 3 2
2 4 1
1 3 5
3 4 3
1 4 4
```

输出 #1

```
0 2 4 3
```

给一个大佬的标程

```c++
#include <bits/stdc++.h>
using namespace std;
#define INF 0x7fffffff
const int maxn=500010;
struct edge{
	int w,to,next;
};
edge e[maxn];
int vis[maxn],dis[maxn],head[maxn];
int n,m,s,cnt;
void add_edge(int u,int v,int d)  //链式前向星存图 
{
	cnt++;
	e[cnt].w=d;
	e[cnt].to=v;
	e[cnt].next=head[u];
	head[u]=cnt;
}
struct node{
	int dis;
	int pos;
	bool operator<(const node &x)const   //在优先队列从小到大排序 
	{
		return x.dis<dis;
	}
};
priority_queue<node> q;  //创建一个优先队列 
void dijkstra()
{
	node a;
	a.dis=0;
	a.pos=s;
	dis[s]=0;
	q.push(a);
	while(!q.empty())  	  //把符号的放入队列 直到队列为空 
	{
		a=q.top();
		q.pop();
		int x=a.pos,d=a.dis;
		if(vis[x]) continue;
		vis[x]=1;
		for(int i=head[x];i;i=e[i].next)  //遍历该点的邻接点 
		{
			int y=e[i].to;
			if(dis[y]>dis[x]+e[i].w)
			{
				dis[y]=dis[x]+e[i].w;
				if(!vis[y])
				{
					q.push((node) {dis[y],y});

				}
			}
		}
	}
}
int main()
{
	cin>>n>>m>>s;
	for(int i=0;i<=n;i++) dis[i]=INF; //把每个距离初始化为无穷大
	for(int i=0;i<m;i++)
	{
		int a,b,c;
		cin>>a>>b>>c;
		add_edge(a,b,c);
	}
	dijkstra();
	for(int i=1;i<=n;i++)
	cout<<dis[i]<<' ';
	return 0;
}
```

笔者能力有限，讲解不到位可以看看大佬讲的思路https://www.bilibili.com/video/av25829980