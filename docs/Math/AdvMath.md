# AdvMath

高等数学

## 方向导数
顾名思义，方向导数就是某个方向上的导数：

<table><tr>
	<td>
		<center><img width="60%" src="Pics/math/1.png"/></center>
		<center>方向</center>
	</td>
	<td>
		<center><img width="60%" src="Pics/math/2.png"/></center>
		<center>函数f(x,y)在这个方向上的图像</center>
	</td>
</tr></table>

我们知道一元函数中导数就是该点切线斜率；

函数f(x,y)的A点在这个方向上也是有切线的，其切线的斜率就是方向导数：

<table><tr>
	<td>
		<center><img width="60%" src="Pics/math/3.png"/></center>
		<center>一元导数（全导数）</center>
	</td>
	<td>
		<center><img width="70%" src="Pics/math/4.png"/></center>
		<center>方向导数（偏导数）</center>
	</td>
</tr></table>

## 梯度
很显然，A点不止一个方向，而是360°都有方向，且每个方向都有方向导数：

<table><tr>
	<td>
		<center><img width="50%" src="Pics/math/5.png"/></center>
	</td>
	<td>
		<center><img width="80%" src="Pics/math/6.png"/></center>
	</td>
</tr></table>

这就引出了梯度的定义：

> **梯度:** 是一个矢量，其方向上的方向导数最大，其大小正好是此最大方向导数.

严格的数学定义：

<div align=center><img width="50%" src="Pics/math/7.png"/></div>

具有一阶连续偏导数，意味着可微。可微意味着函数f(x,y)在各个方向的切线都在同一个平面上，也就是切平面：

<div align=center><img width="50%" src="Pics/math/8.png"/></div>

实际应用中我们通常需要去寻找所有方向导数中梯度的最大值 (所有方向导数中会存在并且只存在一个最大值)，


