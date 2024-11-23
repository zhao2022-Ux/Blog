---
title: A+B
---

# 思路
设$f_1=A,f_2=B,f_n(n>2)=f_{n-1}+f_{n-2},$则$f_3$就是ANSWER $A+B$。
# 推导
设 $q^n=q^{n-1}+q^{n-2},$ 解得$(q≠0)q_1=\frac{1+\sqrt{5}}{2},q_2=\frac{1-\sqrt{5}}{2}$。\
再设$\begin{cases}
  f_n=aq_1^{n-1}+bq_2^{n-1} \\
  f_1=A,f_2=B
\end{cases}$\
代入，即得$\begin{cases}
  a+b=A \\
  a(\frac{1+\sqrt{5}}{2})+b(\frac{1-\sqrt{5}}{2})=B
\end{cases}$\
解二元一次方程组得$\begin{cases}
  a=\frac{B-A(\frac{1-\sqrt{5}}{2})}{\sqrt{5}} \\
  b=\frac{A(\frac{1+\sqrt{5}}{2})-B}{\sqrt{5}}
\end{cases}$\
再代入得$f_n=\frac{1}{\sqrt{5}}((B-A(\frac{1-\sqrt{5}}{2}))(\frac{1+\sqrt{5}}{2})^{n-1}+(A(\frac{1+\sqrt{5}}{2})-B)(\frac{1-\sqrt{5}}{2})^{n-1})$
# 解答
将 $n=3$ 代入 $f_n=\frac{1}{\sqrt{5}}((B-A(\frac{1-\sqrt{5}}{2}))(\frac{1+\sqrt{5}}{2})^{n-1}+(A(\frac{1+\sqrt{5}}{2})-B)(\frac{1-\sqrt{5}}{2})^{n-1})$\
得
$
\begin{aligned}
A+B &= f_3\\
	&= \frac{1}{\sqrt{5}}((B-A(\frac{1-\sqrt{5}}{2}))(\frac{1+\sqrt{5}}{2})^{2}+(A(\frac{1+\sqrt{5}}{2})-B)(\frac{1-\sqrt{5}}{2})^{2})\\
    &= \frac{1}{\sqrt{5}}((B-A(\frac{1-\sqrt{5}}{2}))(\frac{3+\sqrt{5}}{2})+(A(\frac{1+\sqrt{5}}{2})-B)(\frac{3-\sqrt{5}}{2}))
\end{aligned}
$
# 实现
只要计算$\frac{1}{\sqrt{5}}((B-A(\frac{1-\sqrt{5}}{2}))(\frac{3+\sqrt{5}}{2})+(A(\frac{1+\sqrt{5}}{2})-B)(\frac{3-\sqrt{5}}{2}))$,就可以得到 P1001 的AC。

# 代码

```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
{
	double a,b,c=sqrt(5);
	cin>>a>>b;
	printf("%.0lf",((b-a*(1.0-c)/2.0)*(3.0+c)/2.0+((a*(1.0+c)/2.0-b)*(3.0-c)/2))/c);
}
```