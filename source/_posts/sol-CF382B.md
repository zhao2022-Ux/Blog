---
title: CF382B Number Busters
date: 2024-06-19 17:24
tags: 题解
comments: true
categories: 洛谷题解
Katex: false
mathjax: true
---

### Description
题目传送门：[CF382B Number Busters](/problem/CF382B)。

### Analysis
> 两个人玩游戏，他们有 $a$，$b$，$w$，$x$，$c$ 五个数，每秒可执行一次操作，要使最终结果为 $c\le a$。操作如下：如果 $b\ge x$，则 $b=b-x$，同时 $c=c-1$；如果 $b<x$，则 $a=a-1$，$c=c-1$，$b=w-(x-b)$。求 $c\le a$  时已经走过的秒数。

题目已经说的很清楚了，按照模拟即可。

在 $c<a$ 时，执行以下操作：
+ $b \ge x$ 时，$b=b−1$，$c=c−1$。
+ $b < x$ 时，$a=a−1$，$c=c − 1$，$b=w−x+b$。

### Code
```cpp
#include <bits/stdc++.h>
using namespace std;

int main()
{
	typedef long long LL;
	
	LL a , b , w , x , c;
	cin >> a >> b >> w >> x >> c; //5个数字
	
	LL ans = 0; //最后的秒数
	
	while(c > a) //模拟
	{
		if(b >= x)
			b -= x , c --;
		
		else if(b < x)
			a -- , c -- , b = w - (x - b);
		
		ans ++; //秒数++
	}
	
	cout << ans << endl;
	return 0;
}
```