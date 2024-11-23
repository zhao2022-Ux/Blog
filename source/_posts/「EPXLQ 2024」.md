---
title: 「EPXLQ 2024」银辉描淡的石桥
date: 2024-06-12 20:06
tags: 题解
comments: true
categories: 个人记录
Katex: false
mathjax: true
---

### Description
题目传送门：[「EPXLQ 2024」银辉描淡的石桥](/problem/T460119)。

排序后计算 $\text{rank}$ 后输出即可。在此之前，可以先完成[此题](/problem/B3968)。

### Analysis
+ 先来解决输出 `Hahahai!` 的问题。

定义变量 $flag$，先设置为都相同（`true`），在定义 $front$ 变量取头数据。后面输入时比较，如果发现不同的数据后，设 $flag$ 为 `false`。

判断部分代码如下：
```cpp
if(a[i].score != front)
{
	flag = false;
}
```

+ 再来解决排序的问题。

先定义结构体，有两个参数：编号和成绩。接下来输入边输边存编号 `a[i].number = i`，后面写好自定义排序，定义映射类型（~~主打一个方便~~）的变量存 $\text{rank}$ 后输出即可。

存 $\text{rank}$ 的代码如下：
```cpp
for(int i = 1 ; i <= n ; i ++)
{
	Rank[a[i].number] = i;
}
```
解释一下就是 $Rank[$ 这个人的学号 $]=$ 这个人的名次（$a$ 已经从大到小排过序）。

### Code
```cpp
#include <bits/stdc++.h>
using namespace std;

struct node
{
	int score;
	int number;
}a[100001];

map <int , int> Rank;
bool flag = true;

bool cmp(node x , node y)
{
	return x.score > y.score;
}

int main()
{
	int n;
	cin >> n;
	
	cin >> a[1].score;
	a[1].number = 1;
	int front = a[1].score;
	
	for(int i = 2 ; i <= n ; i ++)
	{
		cin >> a[i].score;
		a[i].number = i;
		
		if(a[i].score != front)
		{
			flag = false;
		}
	}
	
	if(flag)
	{
		cout << "Hahahai!";
		return 0;
	}
	
	sort(a + 1 , a + n + 1 , cmp);
	
	for(int i = 1 ; i <= n ; i ++)
	{
		Rank[a[i].number] = i;
	}
	
	for(map <int , int> :: iterator it = Rank.begin() ; it != Rank.end() ; it ++)
	{
		cout << it->second << " ";
	}
	return 0;
}
```