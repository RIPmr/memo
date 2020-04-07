<html>

<head>
<meta http-equiv=Content-Type content="text/html; charset=x-cp20936">
<meta name=Generator content="Microsoft Word 15 (filtered)">
<style>
<!--
 /* Font Definitions */
 @font-face
	{font-family:宋体;
	panose-1:2 1 6 0 3 1 1 1 1 1;}
@font-face
	{font-family:"Cambria Math";
	panose-1:2 4 5 3 5 4 6 3 2 4;}
@font-face
	{font-family:Calibri;
	panose-1:2 15 5 2 2 2 4 3 2 4;}
@font-face
	{font-family:幼圆;
	panose-1:2 1 5 9 6 1 1 1 1 1;}
@font-face
	{font-family:微软雅黑;
	panose-1:2 11 5 3 2 2 4 2 2 4;}
@font-face
	{font-family:新宋体;
	panose-1:2 1 6 9 3 1 1 1 1 1;}
@font-face
	{font-family:Verdana;
	panose-1:2 11 6 4 3 5 4 4 2 4;}
@font-face
	{font-family:"\@幼圆";
	panose-1:2 1 5 9 6 1 1 1 1 1;}
@font-face
	{font-family:"\@宋体";
	panose-1:2 1 6 0 3 1 1 1 1 1;}
@font-face
	{font-family:"\@微软雅黑";
	panose-1:2 11 5 3 2 2 4 2 2 4;}
@font-face
	{font-family:"\@新宋体";
	panose-1:2 1 6 9 3 1 1 1 1 1;}
 /* Style Definitions */
 p.MsoNormal, li.MsoNormal, div.MsoNormal
	{margin:0cm;
	margin-bottom:.0001pt;
	text-align:justify;
	text-justify:inter-ideograph;
	font-size:10.5pt;
	font-family:"Calibri","sans-serif";}
h2
	{margin-right:0cm;
	margin-left:0cm;
	font-size:18.0pt;
	font-family:宋体;
	font-weight:bold;}
p
	{margin-right:0cm;
	margin-left:0cm;
	font-size:12.0pt;
	font-family:"Calibri","sans-serif";}
@page WordSection1
	{size:595.3pt 841.9pt;
	margin:72.0pt 90.0pt 72.0pt 90.0pt;
	layout-grid:15.6pt;}
div.WordSection1
	{page:WordSection1;}
 /* List Definitions */
 ol
	{margin-bottom:0cm;}
ul
	{margin-bottom:0cm;}
-->
</style>

</head>

<body lang=ZH-CN link=blue vlink="#954F72" style='text-justify-trim:punctuation'>

<div class=WordSection1 style='layout-grid:15.6pt'>

<p class=MsoNormal><b><span style='font-size:20.0pt;font-family:幼圆;background:
#D9D9D9'>光栅化算法<span lang=EN-US>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></b></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span style='font-family:宋体'>数值微分法（</span><span
lang=EN-US>Digital Differential Analyzer</span></b><b><span style='font-family:
宋体'>，</span><span lang=EN-US>DDA</span></b><b><span style='font-family:宋体'>）</span></b></p>

<p class=MsoNormal><span style='font-family:宋体'>一种直接从直线的微分方程生成直线的方法</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>通过给定直线的端点</span><span
lang=EN-US>P<sub>0</sub>(x<sub>0</sub>, y<sub>0</sub>)</span><span
style='font-family:宋体'>，</span><span lang=EN-US>P<sub>1</sub>(x<sub>1</sub>, y<sub>1</sub>)</span><span
style='font-family:宋体'>，可以得到直线的微分方程：</span></p>

<p class=MsoNormal><span lang=EN-US><img width=298 height=76 id="图片 1"
src="CG/CG_algorithms/image001.png"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>当</span><span lang=EN-US><span
style='position:relative;top:3.0pt'><img width=13 height=15 id="对象 2"
src="CG/CG_algorithms/image002.png"></span></span><span style='font-family:
宋体'>无限小，能够计算得到精确的直线：</span></p>

<p class=MsoNormal><span lang=EN-US><img width=137 height=77 id="图片 3"
src="CG/CG_algorithms/image003.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>但因为设备精度有限，实际取：</span></p>

<p class=MsoNormal><span lang=EN-US><img width=186 height=37 id="图片 4"
src="CG/CG_algorithms/image004.jpg"></span></p>

<p class=MsoNormal><span style='font-family:宋体'>即另下一个画的点在最大位移方向上走一步</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US><img width=553 height=295 id="图片 5"
src="CG/CG_algorithms/image005.jpg"></span></p>

<p class=MsoNormal><span style='font-family:宋体'>情况一：斜率</span><span lang=EN-US>&lt;0</span><span
style='font-family:宋体'>，在</span><span lang=EN-US>X</span><span
style='font-family:宋体'>方向上位移较大</span></p>

<p class=MsoNormal><span style='font-family:宋体'>情况二：斜率</span><span lang=EN-US>&gt;0</span><span
style='font-family:宋体'>，在</span><span lang=EN-US>Y</span><span
style='font-family:宋体'>方向上位移较大</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>优点：</span></b><span
style='font-family:宋体'>直观、易实现</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>缺点：</span></b><span
style='font-family:宋体'>有浮点数和浮点运算，效率不高</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>中点</span><span lang=EN-US>Bresenham</span></b><b><span
style='font-family:宋体'>算法</span></b></p>

<p class=MsoNormal><span style='font-family:宋体'>设</span><span lang=EN-US>A</span><span
style='font-family:宋体'>为</span><span lang=EN-US>CD</span><span
style='font-family:宋体'>边的中点，若</span><span lang=EN-US>B</span><span
style='font-family:宋体'>点在</span><span lang=EN-US>A</span><span
style='font-family:宋体'>点上方，选择</span><span lang=EN-US>D</span><span
style='font-family:宋体'>点；否则，选</span><span lang=EN-US>C</span><span
style='font-family:宋体'>点</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
width=177 height=137 id="图片 6" src="CG/CG_algorithms/image006.png"
alt="IMG_256"></span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>误差表达式</span><span lang=EN-US>:</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>ε(x<sub>i+1</sub>)=BC-AC=(y<sub>i+1</sub>-y<sub>ir</sub>)-0.5</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>递推式：</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>ε(x<sub>i+2</sub>)=(y<sub>i+2</sub>-y<sub>(i+1)r</sub>)-0.5
= y<sub>i</sub>+1+m-y<sub>(i+1)r</sub>-0.5</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>当</span><span lang=EN-US
style='font-size:12.0pt;font-family:"微软雅黑","sans-serif";color:#4D4D4D;
background:white'>ε(x<sub>i+1</sub>)≥0</span><span style='font-family:宋体'>时，选</span><span
lang=EN-US>D</span><span style='font-family:宋体'>点，</span><span lang=EN-US
style='font-size:12.0pt;font-family:"微软雅黑","sans-serif";color:#4D4D4D;
background:white'>y<sub>(i+1)r</sub>&nbsp;= y<sub>ir</sub>+1</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>ε(x<sub>i+2</sub>)= y<sub>i</sub>+1+m-y<sub>ir</sub>-1-0.5=ε(x<sub>i+1</sub>)+m-1</span></p>

<p class=MsoNormal><span style='font-family:宋体'>当</span><span lang=EN-US
style='font-size:12.0pt;font-family:"微软雅黑","sans-serif";color:#4D4D4D;
background:white'>ε(x<sub>i+1</sub>)</span><span style='font-size:12.0pt;
font-family:"微软雅黑","sans-serif";color:#4D4D4D;background:white'>&#65124;<span
lang=EN-US>0</span></span><span style='font-family:宋体'>时，选</span><span
lang=EN-US>C</span><span style='font-family:宋体'>点，</span><span lang=EN-US
style='font-size:12.0pt;font-family:"微软雅黑","sans-serif";color:#4D4D4D;
background:white'>y<sub>(i+1)r</sub>&nbsp;= y<sub>ir</sub></span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>ε(x<sub>i+2</sub>)= y<sub>i</sub>+1+m</span><span
style='font-family:"Arial","sans-serif";color:#4F4F4F;background:white'>－<span
lang=EN-US>y<sub>ir</sub>-0.5=ε(x<sub>i+1</sub>)+m</span></span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体;color:#4F4F4F;background:white'>初始值：</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>ε(x<sub>s+1</sub>)=BC-AC=m-0.5</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:"Arial","sans-serif";color:#4F4F4F;
background:white'>为了运算中不含实型数，同时不影响不等式的判断，将方程两边同乘一正整数。</span></p>

<p class=MsoNormal><span style='font-family:"Arial","sans-serif";color:#4F4F4F;
background:white'>令方程两边同乘<span lang=EN-US>2</span>&middot;Δ<span lang=EN-US>x</span>，即<span
lang=EN-US>d=2</span>&middot;Δ<span lang=EN-US>x</span>&middot;ε，则：</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体;color:#4F4F4F;background:white'>初始值：</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>d&nbsp;=&nbsp;2&middot;Δy-Δx</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体;color:#4F4F4F;background:white'>递推式：</span></p>

<div align=center>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0
 style='background:white;border-collapse:collapse;border:none'>
 <tr>
  <td width=553 style='width:414.55pt;border:solid #DDDDDD 1.0pt;padding:6.0pt 6.0pt 6.0pt 6.0pt'>
  <p class=MsoNormal align=left style='text-align:left;line-height:16.5pt'><span
  style='font-family:"Arial","sans-serif";color:#4F4F4F'>初始 　　　 </span><span
  lang=EN-US style='font-family:"Arial","sans-serif";color:#4F4F4F;background:
  white'>d&nbsp;=&nbsp;2&middot;Δy-Δx</span></p>
  </td>
 </tr>
 <tr>
  <td width=553 style='width:414.55pt;border:solid #DDDDDD 1.0pt;border-top:
  none;background:#F7F7F7;padding:6.0pt 6.0pt 6.0pt 6.0pt'>
  <p class=MsoNormal align=left style='text-align:left;line-height:16.5pt'><span
  style='font-family:"Arial","sans-serif";color:#4F4F4F'>当<span lang=EN-US>d<sub>
  </sub>≥ 0</span>：<span lang=EN-US>&nbsp;&nbsp; d = d + 2(</span></span><span
  lang=EN-US style='font-family:"Arial","sans-serif";color:#4F4F4F;background:
  white'>Δy-Δx</span><span lang=EN-US style='font-family:"Arial","sans-serif";
  color:#4F4F4F'>)</span></p>
  <p class=MsoNormal align=left style='text-align:left;line-height:16.5pt'><span
  lang=EN-US style='font-family:"Arial","sans-serif";color:#4F4F4F'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  y++; x++;</span></p>
  </td>
 </tr>
 <tr style='height:55.75pt'>
  <td width=553 style='width:414.55pt;border:solid #DDDDDD 1.0pt;border-top:
  none;padding:6.0pt 6.0pt 6.0pt 6.0pt;height:55.75pt'>
  <p class=MsoNormal align=left style='text-align:left;line-height:16.5pt'><span
  style='font-family:"Arial","sans-serif";color:#4F4F4F'>否则：　　　<span
  lang=EN-US>d = d + 2</span></span><span lang=EN-US style='font-family:"Arial","sans-serif";
  color:#4F4F4F;background:white'>Δy</span></p>
  <p style='margin:0cm;margin-bottom:.0001pt;line-height:16.5pt'><span
  lang=EN-US style='font-size:10.5pt;font-family:"Arial","sans-serif";
  color:#4F4F4F'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  x++;</span></p>
  </td>
 </tr>
</table>

</div>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial","sans-serif";
color:#4F4F4F;background:white'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>另一种思想的</span><span
lang=EN-US>Bresenham</span></b><b><span style='font-family:宋体'>算法</span></b></p>

<p class=MsoNormal><span style='font-family:宋体'>采用递推步进的办法，令每次最大变化方向的坐标步进一个象素，同时另一个方向的坐标依据误差判别式的符号来决定是否也要步进一个像素</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>首先讨论当</span><span lang=EN-US>0</span><span
style='font-family:宋体'>≤</span><span lang=EN-US>m</span><span style='font-family:
宋体'>≤</span><span lang=EN-US>1</span><span style='font-family:宋体'>时</span><span
lang=EN-US>:</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
width=291 height=151 id="图片 7" src="CG/CG_algorithms/image007.png"
alt="IMG_256"></span></p>

<p class=MsoNormal><span style='font-family:宋体'>由上图，在</span><span lang=EN-US>x=x<sub>i</sub>+1</span><span
style='font-family:宋体'>处，直线上点的</span><span lang=EN-US>y</span><span
style='font-family:宋体'>值是</span><span lang=EN-US>y=m(x<sub>i</sub>+1)+b</span><span
style='font-family:宋体'>，该点离象素点</span><span lang=EN-US>(x<sub>i</sub>+1</span><span
style='font-family:宋体'>，</span><span lang=EN-US>y<sub>i</sub>)</span><span
style='font-family:宋体'>和象素点</span><span lang=EN-US>(x<sub>i</sub>+1</span><span
style='font-family:宋体'>，</span><span lang=EN-US>y<sub>i</sub>+1)</span><span
style='font-family:宋体'>的距离分别是</span><span lang=EN-US>d1</span><span
style='font-family:宋体'>和</span><span lang=EN-US>d2</span><span
style='font-family:宋体'>：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>d<sub>1 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </sub>=
&nbsp;&nbsp;&nbsp;&nbsp; y-y<sub>i&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </sub>=
&nbsp;&nbsp;&nbsp;&nbsp; m(x<sub>i</sub>+1)+b-y<sub>i</sub></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>d<sub>2 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </sub>=
&nbsp;&nbsp;&nbsp;&nbsp; (y<sub>i</sub>+1)-y&nbsp;&nbsp;&nbsp;&nbsp; = &nbsp;&nbsp;&nbsp;&nbsp; (y<sub>i</sub>+1)-m(x<sub>i</sub>+1)-b</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>两个距离差：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>dist = d<sub>1</sub>-d<sub>2</sub>=2m(x<sub>i</sub>+1)-2y<sub>i</sub></span><span
style='font-family:宋体'>＋</span><span lang=EN-US>2b-1</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>由此距离差可知：</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>(1)</span><span style='font-family:宋体'>当此值为正时，</span><span
lang=EN-US>dist &gt; 0, d<sub>1</sub> &gt; d<sub>2</sub></span><span
style='font-family:宋体'>，说明直线上理论点离</span><span lang=EN-US>(x<sub>i</sub>+1</span><span
style='font-family:宋体'>，</span><span lang=EN-US>y<sub>i</sub>+1)</span><span
style='font-family:宋体'>象素较近，下一个象素点应取</span><span lang=EN-US>(x<sub>i</sub>+1</span><span
style='font-family:宋体'>，</span><span lang=EN-US>y<sub>i</sub>+1)</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>(2)</span><span style='font-family:宋体'>当此值为负时，</span><span
lang=EN-US>dist &lt; 0, d<sub>1</sub> &lt; d<sub>2</sub></span><span
style='font-family:宋体'>，说明直线上理论点离</span><span lang=EN-US>(x<sub>i</sub>+1</span><span
style='font-family:宋体'>，</span><span lang=EN-US>y<sub>i</sub>)</span><span
style='font-family:宋体'>象素较近，则下一个象素点应取</span><span lang=EN-US>(x<sub>i</sub>+1</span><span
style='font-family:宋体'>，</span><span lang=EN-US>y<sub>i</sub>)</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>(3)</span><span style='font-family:宋体'>当此值为零时，说明直线上理论点离上、下两个象素点的距离相等，取哪个点都行，假设算法规定这种情况下取</span><span
lang=EN-US>(x<sub>i</sub>+1</span><span style='font-family:宋体'>，</span><span
lang=EN-US>y<sub>i</sub>+1)</span><span style='font-family:宋体'>作为下一个象素点</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>于是我们定义一个误差值ξ表示这个距离差</span><span
lang=EN-US>:</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>ξ</span><sub><span
lang=EN-US>i </span></sub><span lang=EN-US>= △x&middot;(d<sub>1</sub>-d<sub>2</sub>) =
2△y&middot;x<sub>i </sub>- 2△x&middot;y<sub>i </sub>+ c</span></p>

<p class=MsoNormal><span style='font-family:宋体'>式中，为了消除浮点数运算，且实际上判定下一个像素点位置仅用到</span><span
lang=EN-US>dist</span><span style='font-family:宋体'>的符号，所以乘以</span><span
lang=EN-US>△x</span><span style='font-family:宋体'>，ξ</span><sub><span
lang=EN-US>i </span></sub><span lang=EN-US>= dist * △x</span><span
style='font-family:宋体'>将</span><span lang=EN-US>m=△y/△x</span><span
style='font-family:宋体'>变为整数</span></p>

<p class=MsoNormal><span lang=EN-US>△x = (x<sub>2</sub>-x<sub>1</sub>)&gt;0</span><span
style='font-family:宋体'>，因此ξ</span><sub><span lang=EN-US>i</span></sub><span
style='font-family:宋体'>与</span><span lang=EN-US>dist = (d<sub>1</sub>-d<sub>2</sub>)</span><span
style='font-family:宋体'>有相同的符号</span></p>

<p class=MsoNormal><span style='font-family:宋体'>这里</span><span lang=EN-US>△y = y<sub>2</sub>-y<sub>1</sub></span><span
style='font-family:宋体'>，</span><span lang=EN-US>m = △y/△x</span><span
style='font-family:宋体'>，</span><span lang=EN-US>c = 2△y+△x&middot;(2b-1)</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>接下来计算误差判别递推式，用于基于当前点得到下一个点的位置：</span></p>

<p class=MsoNormal><span style='font-family:宋体'>首先将ξ</span><sub><span
lang=EN-US>i</span></sub><span style='font-family:宋体'>中的下标</span><span
lang=EN-US>+1</span><span style='font-family:宋体'>得到下一个误差值：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>ξ</span><sub><span
lang=EN-US>i+1 </span></sub><span lang=EN-US>= 2</span><span style='font-family:
宋体'>△</span><span lang=EN-US>y</span><span style='font-family:宋体'>&middot;</span><span
lang=EN-US>x<sub>i </sub>+ 1 - 2</span><span style='font-family:宋体'>△</span><span
lang=EN-US>x</span><span style='font-family:宋体'>&middot;</span><span lang=EN-US>y<sub>i
</sub>+ 1 + c</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>△ξ</span><span
lang=EN-US> = </span><span style='font-family:宋体'>ξ</span><sub><span
lang=EN-US>i+1 </span></sub><span lang=EN-US>- </span><span style='font-family:
宋体'>ξ</span><sub><span lang=EN-US>i </span></sub><span lang=EN-US>= 2△y-2△x&middot;(y<sub>i</sub>+1-y<sub>i</sub>)</span></p>

<p class=MsoNormal><span style='font-family:宋体'>于是ξ</span><sub><span
lang=EN-US>i+1 </span></sub><span lang=EN-US>= </span><span style='font-family:
宋体'>ξ</span><sub><span lang=EN-US>i </span></sub><span lang=EN-US>+<sub> </sub>2△y-2△x&middot;(y<sub>i</sub>+1-y<sub>i</sub>)</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>接下来计算误差初始值，假设直线的起始端点刚好在某一个像素点上，即满足：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>y<sub>1</sub>=mx<sub>1</sub>+b</span></p>

<p class=MsoNormal><span style='font-family:宋体'>代入ξ</span><sub><span
lang=EN-US>i </span></sub><span lang=EN-US>= △x&middot;(d<sub>1</sub>-d<sub>2</sub>) =
2△y&middot;x<sub>i </sub>- 2△x&middot;y<sub>i </sub>+ c</span><span style='font-family:宋体'>即可得到误差初值：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>ξ</span><sub><span
lang=EN-US>1</span></sub><span lang=EN-US>=2</span><span style='font-family:
宋体'>△</span><span lang=EN-US>y-</span><span style='font-family:宋体'>△</span><span
lang=EN-US>x</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>于是利用误差判别式即可得到如下算法：</span></p>

<div align=center>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0
 style='background:white;border-collapse:collapse;border:none'>
 <tr>
  <td width=553 style='width:414.55pt;border:solid #DDDDDD 1.0pt;padding:6.0pt 6.0pt 6.0pt 6.0pt'>
  <p class=MsoNormal align=left style='text-align:left;line-height:16.5pt'><span
  style='font-family:"Arial","sans-serif";color:#4F4F4F'>初始 　　　 ξ<sub><span
  lang=EN-US>1 </span></sub><span lang=EN-US>= 2△y - △x</span></span></p>
  </td>
 </tr>
 <tr>
  <td width=553 style='width:414.55pt;border:solid #DDDDDD 1.0pt;border-top:
  none;background:#F7F7F7;padding:6.0pt 6.0pt 6.0pt 6.0pt'>
  <p class=MsoNormal align=left style='text-align:left;line-height:16.5pt'><span
  style='font-family:"Arial","sans-serif";color:#4F4F4F'>当ξ<sub><span
  lang=EN-US>i </span></sub><span lang=EN-US>≥ 0</span>：<span lang=EN-US>&nbsp;
  y++; x++;<br>
  </span>　　　　　　ξ<sub><span lang=EN-US>i+1 </span></sub><span lang=EN-US>= </span>ξ<sub><span
  lang=EN-US>i </span></sub><span lang=EN-US>+ 2(△y - △x)</span></span></p>
  </td>
 </tr>
 <tr style='height:36.5pt'>
  <td width=553 style='width:414.55pt;border:solid #DDDDDD 1.0pt;border-top:
  none;padding:6.0pt 6.0pt 6.0pt 6.0pt;height:36.5pt'>
  <p style='margin:0cm;margin-bottom:.0001pt;line-height:16.5pt'><span
  style='font-size:10.5pt;font-family:"Arial","sans-serif";color:#4F4F4F'>否则：　　　<span
  lang=EN-US>x++;&nbsp;<br>
  </span>　　　　　　ξ<sub><span lang=EN-US>i + 1</span></sub><span lang=EN-US> = </span>ξ<sub><span
  lang=EN-US>i</span></sub><span lang=EN-US> + 2</span>△<span lang=EN-US>y</span></span></p>
  </td>
 </tr>
</table>

</div>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>方向修正：</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>现在我们修正公式（在线段起点区分线段方向）以适应对任何方向及任何斜率线段的绘制。如下图所示，线段的方向可分为八种，从原点出发射向八个区。由线段按图中所示的区域位置可决定</span><span
lang=EN-US>xi+1</span><span style='font-family:宋体'>和</span><span lang=EN-US>yi+1</span><span
style='font-family:宋体'>的变换规律。</span></p>

<p class=MsoNormal style='text-indent:21.05pt'><span style='font-family:宋体'>容易证明：当线段处于①、④、⑧、⑤区时，以</span><span
lang=EN-US>|</span><span style='font-family:宋体'>△</span><span lang=EN-US>x|</span><span
style='font-family:宋体'>和</span><span lang=EN-US>|</span><span style='font-family:
宋体'>△</span><span lang=EN-US>y|</span><span style='font-family:宋体'>代替前面公式中的△</span><span
lang=EN-US>x</span><span style='font-family:宋体'>和△</span><span lang=EN-US>y</span><span
style='font-family:宋体'>，当线段处于②、③、⑥、⑦区时，将公式中的</span><span lang=EN-US>|</span><span
style='font-family:宋体'>△</span><span lang=EN-US>x|</span><span
style='font-family:宋体'>和</span><span lang=EN-US>|</span><span style='font-family:
宋体'>△</span><span lang=EN-US>y|</span><span style='font-family:宋体'>对换，则上述两公式仍有效。</span></p>

<p class=MsoNormal style='text-indent:21.05pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'><img width=435 height=229 id="图片 8"
src="CG/CG_algorithms/image008.gif"></span></p>

<p class=MsoNormal style='text-indent:21.05pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span style='font-family:宋体'>优点：</span></b></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>第</span><span lang=EN-US>i+1</span><span
style='font-family:宋体'>步的判别变量ξ</span><sub><span lang=EN-US>i+1</span></sub><span
style='font-family:宋体'>仅与第</span><span lang=EN-US>i</span><span
style='font-family:宋体'>步的判别变量ξ</span><sub><span lang=EN-US>i</span></sub><span
style='font-family:宋体'>、直线的两个端点坐标分量差</span><span lang=EN-US>△x</span><span
style='font-family:宋体'>和</span><span lang=EN-US>△y</span><span
style='font-family:宋体'>有关，消除了浮点运算，运算中只含有整数相加和乘</span><span lang=EN-US>2</span><span
style='font-family:宋体'>运算，而乘</span><span lang=EN-US>2</span><span
style='font-family:宋体'>可利用算术左移一位来完成，因此这个算法速度快并易于硬件实现。</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>改进的</span><span lang=EN-US>Bresenham</span></b><b><span
style='font-family:宋体'>算法</span></b></p>

<p class=MsoNormal><span style='font-family:宋体'>利用相似三角形，每次画点后平移直线段，判定画的点偏上还是偏下时总是使用最大的相似三角形的宽高（△</span><span
lang=EN-US>x, </span><span style='font-family:宋体'>△</span><span lang=EN-US>y</span><span
style='font-family:宋体'>）</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
width=233 height=166 id="图片 9" src="CG/CG_algorithms/image009.jpg"
alt="IMG_256">&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; <img width=233
height=168 id="图片 10" src="CG/CG_algorithms/image010.jpg" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:63.0pt;text-indent:21.0pt'><span
lang=EN-US style='font-size:12.0pt;font-family:宋体'>(a)  &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; (b)</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
width=233 height=168 id="图片 11" src="CG/CG_algorithms/image011.jpg"
alt="IMG_256">&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; <img width=231
height=172 id="图片 12" src="CG/CG_algorithms/image012.jpg" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:63.0pt;text-indent:21.0pt'><span
lang=EN-US style='font-size:12.0pt;font-family:宋体'>(c)  &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; (d)</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(a)<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><span
style='font-family:宋体'>：初始情况，假设直线第一个点刚好落在某一像素点上，则判断下一个点偏上还是偏下只需判断黄色线段与蓝色线段的比值，蓝色线段长于黄色时，画偏上的点，否则偏下；而基于相似三角形原理，我们实际只需判断整条线段的△</span><span
lang=EN-US>x/2&lt;</span><span style='font-family:宋体'>△</span><span lang=EN-US>y</span><span
style='font-family:宋体'>时（实际直线上的下一个点的纵坐标位置超过虚拟网格点纵向的</span><span lang=EN-US>1/2</span><span
style='font-family:宋体'>）即可确定要画的下一个点偏上，如图</span><span lang=EN-US>(b)</span></p>

<p class=MsoNormal><span lang=EN-US>(c) </span><span style='font-family:宋体'>：判断再下一个点时，不能再像判断第一个顶点一样直接使用相似原理，因为实际直线上的点不在格点上，所以我们平移直线的第一个点到刚才确定的第二个点，但这会带来误差，误差即为</span><span
lang=EN-US>(d)</span><span style='font-family:宋体'>中的蓝色长线段，记为</span><span
lang=EN-US>err</span><span style='font-family:宋体'>，而蓝色长线段是我们扩大后的误差部分，所以原来的蓝色短线段部分误差就是</span><span
lang=EN-US>err/</span><span style='font-family:宋体'>△</span><span lang=EN-US>x</span><span
style='font-family:宋体'>；所以我们每次平移直线后都要减掉这一段因为平移带来的误差，沿</span><span lang=EN-US>y</span><span
style='font-family:宋体'>轴向上平移一格时带来的误差是</span><span lang=EN-US>+dx</span><span
style='font-family:宋体'>，沿</span><span lang=EN-US>x</span><span
style='font-family:宋体'>轴向右平移一格时带来的误差是</span><span lang=EN-US>-dy</span><span
style='font-family:宋体'>（详细计算过程在下面说明）。所以除了第二个顶点，判断以后的顶点位置我们都需要用△</span><span
lang=EN-US>x/2&lt;</span><span style='font-family:宋体'>△</span><span lang=EN-US>y-err</span><span
style='font-family:宋体'>来判断下一点的纵坐标是否</span><span lang=EN-US>+1</span><span
style='font-family:宋体'>。</span></p>

<p class=MsoNormal><span style='font-family:宋体'>以上讨论的是△</span><span lang=EN-US>x&gt;</span><span
style='font-family:宋体'>△</span><span lang=EN-US>y</span><span style='font-family:
宋体'>的情况，△</span><span lang=EN-US>y&gt;</span><span style='font-family:宋体'>△</span><span
lang=EN-US>x</span><span style='font-family:宋体'>的情况类似。</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>计算</span><span lang=EN-US>err:</span></b></p>

<p class=MsoNormal><span style='font-family:宋体'>考察直线方程：</span></p>

<p class=MsoNormal><span lang=EN-US>y = k * x + b, k = dy/dx</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>变换成一般式，即：</span></p>

<p class=MsoNormal><span lang=EN-US>dy * x &#8211; dx * y + C = 0, C = dx * b</span></p>

<p class=MsoNormal><span style='font-family:宋体'>注意</span><span lang=EN-US>dx,dy</span><span
style='font-family:宋体'>皆为常量，是线段横坐标的变化量和纵坐标的变化量，与上文相符</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>横坐标正向平移一个单位长度的直线方程：</span></p>

<p class=MsoNormal><span lang=EN-US>dy * x &#8211; dx * y + C + err= 0</span></p>

<p class=MsoNormal><span style='font-family:宋体'>其中，</span><span lang=EN-US>err
= -dy</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>转换为纵截距差的形式：</span></p>

<p class=MsoNormal><span lang=EN-US>y = k * x + b + (err/dx) , k = dy/dx</span></p>

<p class=MsoNormal><span style='font-family:宋体'>可见线段平移后，纵截距差恰好是上文中所述的</span><span
lang=EN-US>err/dx</span><span style='font-family:宋体'>，而且我们计算出了横坐标平移一个单位长度后，</span><span
lang=EN-US>err =-dy</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>同理，纵坐标正向平移一个单位长度的直线方程：</span></p>

<p class=MsoNormal><span lang=EN-US>dy * x &#8211; dx * y + C + err= 0</span></p>

<p class=MsoNormal><span style='font-family:宋体'>其中，</span><span lang=EN-US>err
= +dx</span><span style='font-family:宋体'>。</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>优点：</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>既避免了浮点运算又简化了传统</span><span
lang=EN-US>Bresenham</span><span style='font-family:宋体'>的代码实现</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>缺点：</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>不易理解</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>代码实现（</span><span
lang=EN-US>DDA</span></b><b><span style='font-family:宋体'>）：</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:blue'>void</span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:#2B91AF'>Line</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>::CalcVerts_DDA(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> increx, increy,
x, y;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> steps;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; x = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>; y = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (abs(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) &gt; abs(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>)) steps = abs(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>else</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> steps = abs(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; increx =
(</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>)(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) / steps;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; increy =
(</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>)(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) / steps;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>for</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> i = 0; i &lt;=
steps; i++) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:green'>// put result
points</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:#C00000'>drawPoint(x,
y);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; x
+= increx;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; y
+= increy;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; }</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>}</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>代码实现（</span><span
lang=EN-US>Bresenham</span></b><b><span style='font-family:宋体'>）：</span></b></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:blue'>void</span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:#2B91AF'>Line</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>::CalcVerts_Bresenham(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> dx, dy, s1, s2,
interchange;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; dx =
abs(</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>); dy = abs(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; s1 = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> &gt; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> ? 1 : -1;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; s2 = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> &gt; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> ? 1 : -1;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (dy &gt; dx) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; swap(dx,
dy);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; interchange
= 1;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; } </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>else</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> interchange =
0;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> p = 2 * dy -
dx;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>for</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> i = 0, j = 0; i
&lt;= dx; i++) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:#C00000'>drawPoint(x1,
y1);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:#C00000'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (p &gt;= 0) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (interchange ==
0) </span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> + s2;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>else</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> + s1;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; p
= p - 2 * dx;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; }</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (interchange ==
0) </span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> + s1;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>else</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> + s2;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; p
= p + 2 * dy;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; }</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>}</span></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span style='font-family:宋体'>代码实现（</span><span
lang=EN-US>AdvanceBresenham</span></b><b><span style='font-family:宋体'>）：</span></b><span
lang=EN-US style='font-size:10.0pt;font-family:宋体'>(<a
href="http://members.chello.at/easyfilter/bresenham.html">http://members.chello.at/easyfilter/bresenham.html</a>)</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:blue'>void</span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:#2B91AF'>Line</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>::CalcVerts_Bresenham(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x0</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y0</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> dx = abs(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x0</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>), sx = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x0</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> &lt; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> ? 1 : -1;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> dy = abs(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> - </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y0</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>), sy = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y0</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> &lt; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> ? 1 : -1;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> err = (dx &gt;
dy ? dx : -dy) / 2, e2;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>for</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (;;) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:#C00000'>drawPoint(x0,
y0);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x0</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> == </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>x1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> &amp;&amp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y0</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> == </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>y1</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>break</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; e2
= err;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (e2 &gt; -dx) {
err -= dy; </span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:gray'>x0</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'> += sx; }</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (e2 &lt; dy) {
err += dx; </span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:gray'>y0</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'> += sy; }</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; }</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>}</span></p>

<p class=MsoNormal><b><span style='font-size:18.0pt;font-family:宋体'>画圆法</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span style='font-family:宋体'>八分画圆法</span></b></p>

<p class=MsoNormal><span style='font-family:宋体'>利用圆的简单方程或极坐标方程画八分之一圆然后对称得到整圆</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=542 height=205
id="图片 52" src="CG/CG_algorithms/image013.png"></span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>代码实现（极坐标法）：</span></b></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:blue'>void</span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'> CalcCircle(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> m_Radius, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> m_Theta, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>bool</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> close = </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>false</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (m_Theta &lt;
0.0001f) m_Theta = 0.0001f;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
knotList.Clear();</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:green'>//
calc new circle</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>for</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> theta = 0;
theta &lt; 2 * Mathf.PI; theta += m_Theta) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> x = m_Radius *
Mathf.Cos(theta);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> z = m_Radius *
Mathf.Sin(theta);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>
(Mathf.Abs(theta - 2 * Mathf.PI) &lt; 0.01f) </span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:blue'>continue</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Vector3 res = </span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:blue'>new</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'> Vector3(x, 0, z);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
knotList.Add(res);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
}</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (close)
knotList.Add(knotList[0]);</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>}</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><b><span lang=EN-US>Bresenham</span></b><b><span
style='font-family:宋体'>画圆法</span></b></p>

<p class=MsoNormal><span style='font-size:9.5pt;font-family:新宋体;color:black'>借助中点<span
lang=EN-US>Bresenham</span>画线的思想以及根据圆的特点，首先将圆平移到原点位置，然后我们只需要画出<span lang=EN-US>1/8</span>的圆弧<span
lang=EN-US>(</span>第一象限上斜率绝对值小于<span lang=EN-US>1</span>的那八分圆<span lang=EN-US>)</span>，根据对称翻转，就可以绘制出一整个圆</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>*</span><span style='font-size:9.5pt;font-family:新宋体;color:black'>圆在某点的斜率是该点处切线斜率</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-size:9.5pt;font-family:新宋体;color:black'>构造判别式：</span></b></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=373 height=185
id="图片 56" src="CG/CG_algorithms/image014.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-size:9.5pt;font-family:新宋体;color:black'>误差项两种情况：</span></b></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=373 height=184
id="图片 57" src="CG/CG_algorithms/image015.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=372 height=143
id="图片 58" src="CG/CG_algorithms/image016.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=371 height=217
id="图片 60" src="CG/CG_algorithms/image017.jpg"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>最后根据</span><span
lang=EN-US> Bresenham </span><span style='font-family:宋体'>算法的递推方法，推算出当</span><span
lang=EN-US>P</span><span style='font-family:宋体'>大于</span><span lang=EN-US>0</span><span
style='font-family:宋体'>或者小于</span><span lang=EN-US>0</span><span
style='font-family:宋体'>两种更新方法。然后算出第一个点</span><span lang=EN-US>P<sub>0</sub></span><span
style='font-family:宋体'>为</span><span lang=EN-US>1.25&#8722;r</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><b><span style='font-family:宋体'>为了避免浮点数的运算，我们把所有的结果扩大两倍。再限制圆形半径不得小于</span><span
lang=EN-US>2</span></b><b><span style='font-family:宋体'>，</span><span
lang=EN-US>P<sub>0</sub></span></b><b><span style='font-family:宋体'>就可以近似为</span><span
lang=EN-US>3&#8722;2r</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=544 height=698 id="图片 61" src="CG/CG_algorithms/image018.png"
alt="IMG_256"></span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:9.5pt;font-family:新宋体;color:black'>然后根据对称原理，在每计算得到一个点后，画其他<span
lang=EN-US>7</span>个对称点：</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=208 height=176
id="图片 63" src="CG/CG_algorithms/image019.jpg">X&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:12.0pt;font-family:宋体'><img border=0 width=199
height=186 id="图片 55" src="CG/CG_algorithms/image020.png" alt="IMG_256"></span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-size:9.5pt;font-family:新宋体;color:black'>最后还要根据圆的中心坐标将圆平移回正确位置：</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>代码实现（中点</span><span
lang=EN-US>Bresenham</span></b><b><span style='font-family:宋体'>）：</span></b></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:blue'>void</span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:#2B91AF'>Circle</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>::CalcVerts_Bresenham(</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:#2B91AF'>Vector2</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>centerPos</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>, </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>float</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>radius</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> x, y, p;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; x = 0; y
= </span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>radius</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; p = 3 -
2 * </span><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:gray'>radius</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'>;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>for</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> i = 0; x &lt;=
y; x++) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:green'>// put result
points</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; point_count
+= 16;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:green'>// remember to
do offset &amp; do symmetry</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> swp = 2;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>while</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (swp--) {</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; std::swap(x,
y);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>for</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> j = -1; j &lt;=
1; j += 2)</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>for</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>int</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> k = -1; k &lt;=
1; k += 2)</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:red'>drawPoint(x * j +
centerPos.x, y * k + centerPos.y);</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; }</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>if</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> (p &gt;= 0) p
+= 4 * (x - y--) + 10;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; </span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:blue'>else</span><span
lang=EN-US style='font-size:9.5pt;font-family:新宋体;color:black'> p += 4 * x + 6;</span></p>

<p class=MsoNormal align=left style='text-align:left'><span lang=EN-US
style='font-size:9.5pt;font-family:新宋体;color:black'>&nbsp;&nbsp;&nbsp; }</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>}</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><b><span lang=EN-US>Bresenham</span></b><b><span
style='font-family:宋体'>椭圆</span></b></p>

<p class=MsoNormal><span style='font-family:宋体'>和画圆不同，画椭圆时为四分对称而非八分对称，且在画第一象限部分时，需要将椭圆分为上下两个部分，两部分以椭圆法向</span><span
lang=EN-US>X</span><span style='font-family:宋体'>分量与</span><span lang=EN-US>Y</span><span
style='font-family:宋体'>分量相同的点（椭圆上斜率为</span><span lang=EN-US>-1</span><span
style='font-family:宋体'>的点）</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=164 height=34 id="图片 65"
src="CG/CG_algorithms/image021.jpg">&nbsp; <img border=0 width=250
height=32 id="图片 66" src="CG/CG_algorithms/image022.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=191 height=175
id="图片 64" src="CG/CG_algorithms/image023.jpg">&nbsp; &nbsp;<img border=0
width=340 height=176 id="图片 67" src="CG/CG_algorithms/image024.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=414 height=217
id="图片 68" src="CG/CG_algorithms/image025.jpg"></span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(1)
</span><span style='font-family:宋体'>输入椭圆的长半轴</span><span lang=EN-US>a</span><span
style='font-family:宋体'>和短半轴</span><span lang=EN-US>b</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(2)
</span><span style='font-family:宋体'>计算初始值</span><span lang=EN-US>d, x=0, y=b</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(3)
</span><span style='font-family:宋体'>绘制</span><span lang=EN-US>(x,y)</span><span
style='font-family:宋体'>及另外三个对称点</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(4)
</span><span style='font-family:宋体'>判断</span><span lang=EN-US>d</span><span
style='font-family:宋体'>的符号，更新</span><span lang=EN-US>d,x,y</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(5)
</span><span style='font-family:宋体'>判断是否进入椭圆下半部分，若是，转</span><span lang=EN-US>(6);</span><span
style='font-family:宋体'>否则重复</span><span lang=EN-US>(3)</span><span
style='font-family:宋体'>和</span><span lang=EN-US>(4)</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(6)
</span><span style='font-family:宋体'>基于上半部分最后的点</span><span lang=EN-US>(x,y)</span><span
style='font-family:宋体'>计算下半部分的</span><span lang=EN-US>d</span><span
style='font-family:宋体'>的初值</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(7)
</span><span style='font-family:宋体'>绘制</span><span lang=EN-US>(x,y)</span><span
style='font-family:宋体'>及另外三个对称点</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(8)
</span><span style='font-family:宋体'>判断</span><span lang=EN-US>d</span><span
style='font-family:宋体'>的符号，更新</span><span lang=EN-US>d,x,y</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:0cm'><span lang=EN-US>(9)
</span><span style='font-family:宋体'>当</span><span lang=EN-US>y&gt;0</span><span
style='font-family:宋体'>时，重复</span><span lang=EN-US>(7)</span><span
style='font-family:宋体'>和</span><span lang=EN-US>(8)</span><span
style='font-family:宋体'>，否则算法结束</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>误差项与递推式推导：</span></b></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=419 height=142
id="图片 69" src="CG/CG_algorithms/image026.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=422 height=157
id="图片 70" src="CG/CG_algorithms/image027.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=423 height=159
id="图片 71" src="CG/CG_algorithms/image028.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>当</span><span lang=EN-US>2a<sup>2</sup>(y-0.5)&gt;2b<sup>2</sup>(x+1)</span></b><b><span
style='font-family:宋体'>时，转入下半部分计算：</span></b></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=424 height=189
id="图片 72" src="CG/CG_algorithms/image029.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=427 height=185
id="图片 73" src="CG/CG_algorithms/image030.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=430 height=135
id="图片 74" src="CG/CG_algorithms/image031.jpg"></span></p>

<p class=MsoNormal><b><span style='font-size:20.0pt;font-family:幼圆;background:
#D9D9D9'>多边形填充算法<span lang=EN-US>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></b></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>X</span></b><b><span style='font-family:
宋体'>扫描线算法</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>需要注意的问题及解决方案：</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US>（1）</span><span
style='font-family:宋体'>如果多个多边形相邻的话，它们可能会共享一条边，那么共享边可能会被绘制两次：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US><img border=0
width=243 height=181 id="图片 75" src="CG/CG_algorithms/image032.jpg"><img
border=0 width=245 height=179 id="图片 76" src="CG/CG_algorithms/image033.jpg"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>解决方案：每个多边形只拥有它左边的像素，即采用左闭右开的原则，如果边是水平的话，则只拥有底边。（左闭右开，下闭上开）</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US><img border=0
width=242 height=175 id="图片 77" src="CG/CG_algorithms/image034.jpg"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US>（2）</span><span
style='font-family:宋体'>若采用</span><span lang=EN-US>Bresenham</span><span
style='font-family:宋体'>直线绘制算法，可能会出现一些像素超出边所在的范围：</span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span style='font-family:宋体'>解决方案：在计算完扫描线与边的交点后，会形成一条条的首尾相连的线段，用</span><span
lang=EN-US>xLeft</span><span style='font-family:宋体'>表示左端点，</span><span
lang=EN-US>xRight</span><span style='font-family:宋体'>表示右端点，</span><span
lang=EN-US>xLeft</span><span style='font-family:宋体'>和</span><span lang=EN-US>xRight</span><span
style='font-family:宋体'>是实数，取大于等于</span><span lang=EN-US>xLeft</span><span
style='font-family:宋体'>的最小整数</span><span lang=EN-US>xNewLeft</span><span
style='font-family:宋体'>，取小于等于</span><span lang=EN-US>xRight</span><span
style='font-family:宋体'>的最大整数</span><span lang=EN-US>xNewRight</span><span
style='font-family:宋体'>，则绘制像素范围是</span><span lang=EN-US>[xNewLeft</span><span
style='font-family:宋体'>，</span><span lang=EN-US>xNewRight)</span><span
style='font-family:宋体'>，如果</span><span lang=EN-US> xNewRight &lt; xRight</span><span
style='font-family:宋体'>，则右端也封闭。</span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US>（3）</span><span
style='font-family:宋体'>水平扫描线与端点发生相交的情况</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>若直接将与扫描线相交的交点两两配对进行填色，有些地方会出现错误的填色结果，我们需要将扫描线与端点相交的情况特殊化处理：</span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span lang=EN-US><img border=0
width=373 height=197 id="图片 78" src="CG/CG_algorithms/image035.jpg"></span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>解决方案：忽略任何一条与水平边的相交计算；如果交点是边的上端点，则把该端点忽略（如果发现与线段的交点，如果线段本身在交点</span><span
lang=EN-US>/</span><span style='font-family:宋体'>扫描线以下则不计数，反之，线段本身在扫描线上则计数</span><span
lang=EN-US>+1</span><span style='font-family:宋体'>）</span></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US style='color:red'>Y</span></b><b><span
style='font-family:宋体;color:red'>向连贯性算法</span></b></p>

<p class=MsoNormal><b><span lang=EN-US style='color:red'>(</span></b><span
lang=EN-US style='font-size:12.0pt;font-family:宋体'><a
href="https://blog.csdn.net/wodownload2/article/details/52154207">https://blog.csdn.net/wodownload2/article/details/52154207</a></span><b><span
lang=EN-US style='color:red'>)</span></b></p>

<p class=MsoNormal><b><span style='font-family:宋体'>数据结构</span></b><span
style='font-family:宋体'>：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>一条边的记录包含了三个数据部分及一个指针：</span>
</p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>(1) </span><span style='font-family:宋体'>该边</span><span lang=EN-US>y</span><span
style='font-family:宋体'>的最大值</span><span lang=EN-US>y; </span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>(2) </span><span style='font-family:宋体'>该边底端的</span><span
lang=EN-US>x</span><span style='font-family:宋体'>坐标</span><span lang=EN-US>xi; </span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>(3) </span><span style='font-family:宋体'>该边的斜率的倒数</span><span
lang=EN-US>1/m</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:31.5pt'><span
style='font-family:宋体'>（即每次</span><span lang=EN-US>x</span><span
style='font-family:宋体'>方向上直线的增量，因为扫描线的增量为</span><span lang=EN-US>y</span><span
style='font-family:宋体'>方向每次</span><span lang=EN-US>+1</span><span
style='font-family:宋体'>）</span><span lang=EN-US>; </span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>(4) </span><span style='font-family:宋体'>以及下一个边记录地址的指针</span><span
lang=EN-US>;</span></p>

<p class=MsoNormal style='margin-left:42.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>例：</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US style='font-size:12.0pt;font-family:宋体'><img border=0 width=328
height=293 id="图片 79" src="CG/CG_algorithms/image036.png" alt="IMG_256"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>对于下面的多边形为其建立边表（即对每一条扫描线建立</span><span
lang=EN-US>AET</span></b><b><span style='font-family:宋体'>）：</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=542 height=290 id="图片 80" src="CG/CG_algorithms/image037.png"
alt="IMG_256"></span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>建立边表的方法：</span></b> </p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>1</span><span style='font-family:宋体'>）与</span><span lang=EN-US>x</span><span
style='font-family:宋体'>轴平行的边不计入；</span> </p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>2</span><span style='font-family:宋体'>）交点的取舍：扫描线与多边形顶点处的交点个数</span><span
lang=EN-US> = </span></p>

<p class=MsoNormal style='margin-left:84.0pt;text-indent:26.25pt'><span
style='font-family:宋体'>构成这个顶点的两条边位于扫描线上方的条数；</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>3</span><span style='font-family:宋体'>）扫描线按照</span><span lang=EN-US>y</span><span
style='font-family:宋体'>轴从低到高顺次记录；</span> </p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>4</span><span style='font-family:宋体'>）一条边按照</span><span lang=EN-US>y</span><span
style='font-family:宋体'>轴的高低记录；</span> </p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>5</span><span style='font-family:宋体'>）多条边以</span><span lang=EN-US>x</span><span
style='font-family:宋体'>轴递增顺序记录；</span> </p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>上图说明：</span> </b></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>1</span><span style='font-family:
宋体'>）扫描线</span><span lang=EN-US>y=1</span><span style='font-family:宋体'>，穿过了</span><span
lang=EN-US>P3</span><span style='font-family:宋体'>点，此点为极值点，则有两条边。</span><span
lang=EN-US>P3P4</span><span style='font-family:宋体'>和</span><span lang=EN-US>P3P2</span><span
style='font-family:宋体'>。注意不是</span><span lang=EN-US>P4P3</span><span
style='font-family:宋体'>和</span><span lang=EN-US>P2P3</span><span
style='font-family:宋体'>。也不是</span><span lang=EN-US>P3P2</span><span
style='font-family:宋体'>和</span><span lang=EN-US>P3P4</span><span
style='font-family:宋体'>。因为对于一条边来说，</span><span lang=EN-US>P4</span><span
style='font-family:宋体'>的</span><span lang=EN-US>y</span><span style='font-family:
宋体'>大于</span><span lang=EN-US>P3</span><span style='font-family:宋体'>的</span><span
lang=EN-US>y</span><span style='font-family:宋体'>，所以是</span><span lang=EN-US>P3P4</span><span
style='font-family:宋体'>。同理，</span><span lang=EN-US>P3P2</span><span
style='font-family:宋体'>也是这么得到的。又因为</span><span lang=EN-US>P2</span><span
style='font-family:宋体'>点的</span><span lang=EN-US>x</span><span
style='font-family:宋体'>轴坐标大于</span><span lang=EN-US>P4</span><span
style='font-family:宋体'>点的坐标，所以</span><span lang=EN-US>P3P4</span><span
style='font-family:宋体'>在</span><span lang=EN-US>P3P2</span><span
style='font-family:宋体'>的前面。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>2</span><span style='font-family:
宋体'>）扫描线</span><span lang=EN-US>y=2</span><span style='font-family:宋体'>，和多边形的两条边相交，</span><span
lang=EN-US>P3P4</span><span style='font-family:宋体'>和</span><span lang=EN-US>P3P2</span><span
style='font-family:宋体'>，但是这两条边已经被扫描线</span><span lang=EN-US>1</span><span
style='font-family:宋体'>占用了，也就不算做新的边，故扫描线</span><span lang=EN-US>2</span><span
style='font-family:宋体'>的边表为空。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>3</span><span style='font-family:
宋体'>）扫描线</span><span lang=EN-US>y=3</span><span style='font-family:宋体'>，穿越了</span><span
lang=EN-US>P4P5,P3P4,P3P2</span><span style='font-family:宋体'>，这里只有</span><span
lang=EN-US>P4P5</span><span style='font-family:宋体'>是新的边，所以加入扫描线</span><span
lang=EN-US>3</span><span style='font-family:宋体'>的边表。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>4</span><span style='font-family:
宋体'>）扫描线</span><span lang=EN-US>y=4</span><span style='font-family:宋体'>，与多边形相交的边有</span><span
lang=EN-US>P4P5</span><span style='font-family:宋体'>和</span><span lang=EN-US>P3P2</span><span
style='font-family:宋体'>，而这两条边都已经在边表中，所以扫描线</span><span lang=EN-US>4</span><span
style='font-family:宋体'>的边表为空。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>5</span><span style='font-family:
宋体'>）扫描线</span><span lang=EN-US>y=5</span><span style='font-family:宋体'>，与多边形相交的边有</span><span
lang=EN-US>P4P5</span><span style='font-family:宋体'>、</span><span lang=EN-US>P3P2</span><span
style='font-family:宋体'>、</span><span lang=EN-US>P2P1</span><span
style='font-family:宋体'>，其中只有线段</span><span lang=EN-US>P2P1</span><span
style='font-family:宋体'>是新边，所以扫描线</span><span lang=EN-US>y=5</span><span
style='font-family:宋体'>的边表中有一个新边。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>6</span><span style='font-family:
宋体'>）扫描线</span><span lang=EN-US>y=6</span><span style='font-family:宋体'>，与多边形相交的边有</span><span
lang=EN-US>P4P5</span><span style='font-family:宋体'>、</span><span lang=EN-US>P5P1</span><span
style='font-family:宋体'>、</span><span lang=EN-US>P2P1</span><span
style='font-family:宋体'>，其中只有线段</span><span lang=EN-US>P5P1</span><span
style='font-family:宋体'>是新边，所以扫描线</span><span lang=EN-US>y=6</span><span
style='font-family:宋体'>的边表中有一个新边。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>7</span><span style='font-family:
宋体'>）扫描线</span><span lang=EN-US>y=7</span><span style='font-family:宋体'>，与多边形相交的边有</span><span
lang=EN-US>P5P1</span><span style='font-family:宋体'>、</span><span lang=EN-US>P2P1</span><span
style='font-family:宋体'>，这些边都不是新边，所以不需要加入边表中去。</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>算法过程：</span></b> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>1</span><span style='font-family:
宋体'>）开始</span><span lang=EN-US>y=1</span><span style='font-family:宋体'>，将边表中的</span><span
lang=EN-US>y=1</span><span style='font-family:宋体'>节点</span><span lang=EN-US>AET</span><span
style='font-family:宋体'>中，什么是</span><span lang=EN-US>AET</span><span
style='font-family:宋体'>呢？</span><span lang=EN-US>active edge table</span><span
style='font-family:宋体'>，俗称活化边表。这里要保证</span><span lang=EN-US>AET</span><span
style='font-family:宋体'>链表中记录按照</span><span lang=EN-US>x</span><span
style='font-family:宋体'>递增排列，如下图所示：</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>&nbsp;</span><span lang=EN-US style='font-size:12.0pt;font-family:
宋体'><img border=0 width=248 height=45 id="图片 81"
src="CG/CG_algorithms/image038.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>2</span><span style='font-family:
宋体'>）因为上图中</span><span lang=EN-US>P3P4</span><span style='font-family:宋体'>和</span><span
lang=EN-US>P3P2</span><span style='font-family:宋体'>两个</span><span lang=EN-US>xi</span><span
style='font-family:宋体'>是相同的都是</span><span lang=EN-US>6</span><span
style='font-family:宋体'>，中间没有任何点需要着色，所以无需处理。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>3</span><span style='font-family:
宋体'>）然后因为</span><span lang=EN-US>P3P4</span><span style='font-family:宋体'>和</span><span
lang=EN-US>P3P2</span><span style='font-family:宋体'>的两个</span><span lang=EN-US>y</span><span
style='font-family:宋体'>值一个是</span><span lang=EN-US>3</span><span
style='font-family:宋体'>，一个是</span><span lang=EN-US>5</span><span
style='font-family:宋体'>，而此时处理的是</span><span lang=EN-US>y=1</span><span
style='font-family:宋体'>，所以不需要删除。为什么不删除呢？因为此时</span><span lang=EN-US>y=1</span><span
style='font-family:宋体'>还没有到达</span><span lang=EN-US>y=3</span><span
style='font-family:宋体'>和</span><span lang=EN-US>y=5</span><span
style='font-family:宋体'>。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>4</span><span style='font-family:
宋体'>）对保留下来的每个记录，用</span><span lang=EN-US>Xi+1/m</span><span style='font-family:
宋体'>代替</span><span lang=EN-US>Xi</span><span style='font-family:宋体'>，比如：</span>
</p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>&nbsp;</span><span lang=EN-US style='font-size:12.0pt;font-family:
宋体'><img border=0 width=254 height=107 id="图片 82"
src="CG/CG_algorithms/image039.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>5</span><span style='font-family:
宋体'>）使</span><span lang=EN-US>yi+1</span><span style='font-family:宋体'>，以便进入下一轮循环。当</span><span
lang=EN-US>y=2</span><span style='font-family:宋体'>时，</span><span lang=EN-US>ET</span><span
style='font-family:宋体'>表为空，所以不需要</span><span lang=EN-US>ET</span><span
style='font-family:宋体'>表加入</span><span lang=EN-US>AET</span><span
style='font-family:宋体'>表。此时上图中</span><span lang=EN-US>x=4</span><span
style='font-family:宋体'>和</span><span lang=EN-US>x=6.5</span><span
style='font-family:宋体'>，将他们之间的点填上像素。由于</span><span lang=EN-US>y=2</span><span
style='font-family:宋体'>，此时没有达到</span><span lang=EN-US>y=3</span><span
style='font-family:宋体'>和</span><span lang=EN-US>y=5</span><span
style='font-family:宋体'>，所以不必删除节点。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>6</span><span style='font-family:
宋体'>）再让</span><span lang=EN-US>Xi+1/m</span><span style='font-family:宋体'>代替</span><span
lang=EN-US>Xi</span><span style='font-family:宋体'>，得到：</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>&nbsp;</span><span lang=EN-US style='font-size:12.0pt;font-family:
宋体'><img border=0 width=245 height=97 id="图片 83"
src="CG/CG_algorithms/image040.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>使</span><span lang=EN-US>yi=3</span><span
style='font-family:宋体'>，此时他的边表不为空，所以将其</span><span lang=EN-US>ET</span><span
style='font-family:宋体'>表加入，得到：</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>&nbsp;</span><span lang=EN-US style='font-size:12.0pt;font-family:
宋体'><img border=0 width=344 height=42 id="图片 84"
src="CG/CG_algorithms/image041.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>注意按照</span><span lang=EN-US>xi</span><span
style='font-family:宋体'>的升序排列。将</span><span lang=EN-US>Xi=2</span><span
style='font-family:宋体'>，至</span><span lang=EN-US>Xi=7</span><span
style='font-family:宋体'>之间填上颜色。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>7</span><span style='font-family:
宋体'>）由于此时</span><span lang=EN-US>yi=3</span><span style='font-family:宋体'>，而第一个节点的</span><span
lang=EN-US>yi=3</span><span style='font-family:宋体'>，所以去掉此节点。</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>&nbsp;</span><span lang=EN-US style='font-size:12.0pt;font-family:
宋体'><img border=0 width=330 height=85 id="图片 85"
src="CG/CG_algorithms/image042.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>（</span><span lang=EN-US>8</span><span style='font-family:
宋体'>）再用</span><span lang=EN-US>Xi+1/m</span><span style='font-family:宋体'>代替</span><span
lang=EN-US>Xi</span><span style='font-family:宋体'>，得到：</span> </p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US>&nbsp;</span><span lang=EN-US style='font-size:12.0pt;font-family:
宋体'><img border=0 width=248 height=102 id="图片 86"
src="CG/CG_algorithms/image043.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-family:宋体'>使</span><span lang=EN-US>yi=4</span><span
style='font-family:宋体'>，重复继续。</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>边缘填充算法</span></b></p>

<h2 style='margin-top:6.0pt;margin-right:0cm;margin-bottom:12.0pt;margin-left:
0cm;text-indent:21.0pt;line-height:24.0pt;background:white'><span
style='font-size:10.5pt'>填充原理</span></h2>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>边缘填充算法是先求出多边形的每条边与扫描线的交点，然后将交点右侧的所有像素颜色全部取为补色（或反色）。按任意顺序处理完多边形的所有边后，就完成了多边形的填充任务。边缘填充算法利用了图像处理中的求</span><span
lang=EN-US>“</span><span style='font-family:宋体'>补</span><span lang=EN-US>”</span><span
style='font-family:宋体'>或求</span><span lang=EN-US>“</span><span
style='font-family:宋体'>反</span><span lang=EN-US>”</span><span style='font-family:
宋体'>的概念，对于黑白图像，求补就是把</span><span lang=EN-US>RGB(1,1,1)</span><span
style='font-family:宋体'>（白色）的像素置为</span><span lang=EN-US>RGB(0,0,0)</span><span
style='font-family:宋体'>（黑色），反之亦然；对于彩色图像，求补就是将背景色置为填充色，反之亦然。求补的一条基本性质是一个像素求补两次就恢复为原色。如果多边形内部的像素被求补偶数次，保持原色，如果被求补奇数次，显示填充色。</span></p>

<h2 style='margin-top:6.0pt;margin-right:0cm;margin-bottom:12.0pt;margin-left:
0cm;text-indent:21.0pt;line-height:24.0pt;background:white'><span
style='font-size:10.5pt'>填充过程</span></h2>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:12.0pt;margin-left:
0cm;text-indent:21.0pt;line-height:19.5pt;background:white'><span
style='font-size:10.5pt;font-family:宋体'>假定边的顺序为</span><span lang=EN-US
style='font-size:10.5pt'>E0</span><span style='font-size:10.5pt;font-family:
宋体'>、</span><span lang=EN-US style='font-size:10.5pt'>E1</span><span
style='font-size:10.5pt;font-family:宋体'>、</span><span lang=EN-US
style='font-size:10.5pt'>E2</span><span style='font-size:10.5pt;font-family:
宋体'>、</span><span lang=EN-US style='font-size:10.5pt'>E3</span><span
style='font-size:10.5pt;font-family:宋体'>、</span><span lang=EN-US
style='font-size:10.5pt'>E4</span><span style='font-size:10.5pt;font-family:
宋体'>、</span><span lang=EN-US style='font-size:10.5pt'>E5</span><span
style='font-size:10.5pt;font-family:宋体'>和</span><span lang=EN-US
style='font-size:10.5pt'>E6</span><span style='font-size:10.5pt;font-family:
宋体'>。这里，边的顺序并不影响填充结果，只是方便编写循环结构而已。</span><span lang=EN-US style='font-size:
10.5pt'>&nbsp;</span></p>

<p style='margin-top:0cm;margin-right:0cm;margin-bottom:12.0pt;margin-left:
0cm;text-indent:21.0pt;line-height:19.5pt;background:white'><span lang=EN-US
style='font-family:宋体'><img border=0 width=492 height=397 id="图片 87"
src="CG/CG_algorithms/image044.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span style='font-family:宋体'>区域填充算法（种子填充）</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>内定义区域（</span><span
lang=EN-US>interior-defined</span><span style='font-family:宋体'>）的定义是：给定一个像素</span><span
lang=EN-US>S</span><span style='font-family:宋体'>，颜色是</span><span lang=EN-US>C</span><span
style='font-family:宋体'>，区域</span><span lang=EN-US>R</span><span
style='font-family:宋体'>指与</span><span lang=EN-US>S</span><span
style='font-family:宋体'>连通的且颜色都是</span><span lang=EN-US>C</span><span
style='font-family:宋体'>的像素集合（</span><span lang=EN-US>Region R is the set of all
pixels having color C that are “connected” to a given pixel S</span><span
style='font-family:宋体'>）</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>如果两个像素连通，则它们之间有一条</span><span
lang=EN-US>“</span><span style='font-family:宋体'>相邻（</span><span lang=EN-US>adjacent</span><span
style='font-family:宋体'>）</span><span lang=EN-US>”</span><span style='font-family:
宋体'>像素组成的连续路径，所以连通的概念就依赖</span><span lang=EN-US>“</span><span style='font-family:
宋体'>相邻</span><span lang=EN-US>”</span><span style='font-family:宋体'>的定义。在图形学中，相邻通常有两种定义：</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US>1）</span><span
style='font-family:宋体'>四相邻（</span><span lang=EN-US>4-Adjacent</span><span
style='font-family:宋体'>）</span><span lang=EN-US>:</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>两个像素是四相邻的，则它们在彼此水平或者垂直相邻的位置上</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'><img border=0 width=175 height=173
id="图片 89" src="CG/CG_algorithms/image045.jpg" alt="IMG_256"></span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US>2）</span><span
style='font-family:宋体'>八相邻（</span><span lang=EN-US>8-Adjacent</span><span
style='font-family:宋体'>）</span><span lang=EN-US>:</span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span style='font-family:宋体'>两个像素是八相邻的，则它们在彼此水平、垂直或者是斜方向上相邻的位置</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'><img border=0 width=183 height=173
id="图片 90" src="CG/CG_algorithms/image046.jpg" alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>如果两个像素是四连通（</span><span
lang=EN-US>4-connected</span><span style='font-family:宋体'>），指它们之间有一条四相邻像素组成的连续路径；如果两个像素是八连通（</span><span
lang=EN-US>8-connected</span><span style='font-family:宋体'>），指它们之间有一条四相邻像素组成的连续路径。举个例子，如下图</span><span
lang=EN-US>3</span><span style='font-family:宋体'>所示，是由黑色、灰色和白色组成的像素图，给定一个像素点</span><span
lang=EN-US>S</span><span style='font-family:宋体'>，则由它定义的四连通区域共有</span><span
lang=EN-US>20</span><span style='font-family:宋体'>像素，由它定义的八连通区域共有</span><span
lang=EN-US>28</span><span style='font-family:宋体'>个像素：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'><img border=0 width=243 height=240
id="图片 91" src="CG/CG_algorithms/image047.jpg" alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-size:12.0pt;
font-family:宋体'>两种简单的填充算法：</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'>(1) </span><span style='font-size:12.0pt;
font-family:宋体'>泛洪法</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US style='font-size:12.0pt;font-family:宋体'>1. </span><span
style='font-size:12.0pt;font-family:宋体'>从内部一个选中的种子像素点开始，并用新的颜色替换它</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
lang=EN-US style='font-size:12.0pt;font-family:宋体'>2. </span><span
style='font-size:12.0pt;font-family:宋体'>填充四连通或者八连通区域，直到所有的内部点被替换</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=176 height=125
id="图片 92" src="CG/CG_algorithms/image048.jpg">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img
border=0 width=150 height=126 id="图片 93" src="CG/CG_algorithms/image049.jpg">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img
border=0 width=147 height=129 id="图片 94" src="CG/CG_algorithms/image050.jpg">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img
border=0 width=134 height=117 id="图片 95" src="CG/CG_algorithms/image051.jpg">&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img
border=0 width=142 height=115 id="图片 96" src="CG/CG_algorithms/image052.jpg"></span></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span style='font-size:9.5pt;font-family:宋体;color:black;
background:white'>缺点：</span></b><span lang=EN-US style='font-size:9.5pt;
font-family:"Arial","sans-serif";color:black;background:white'>1</span><span
style='font-size:9.5pt;font-family:宋体;color:black;background:white'>）大量的嵌套调用；</span><span
lang=EN-US style='font-size:9.5pt;font-family:"Arial","sans-serif";color:black;
background:white'>2</span><span style='font-size:9.5pt;font-family:宋体;
color:black;background:white'>）很多像素点可能会被测试多次；</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Arial","sans-serif";color:black;background:
white'>3</span><span style='font-size:9.5pt;font-family:宋体;color:black;
background:white'>）难以清楚的掌控由于嵌套调用所占的内存大小；</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Arial","sans-serif";color:black;background:
white'>4</span><span style='font-size:9.5pt;font-family:宋体;color:black;
background:white'>）如果算法多次测试一个像素，会导致占用的内存扩大。</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:"Arial","sans-serif";
color:black;background:white'>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'>(2) </span><span style='font-size:12.0pt;
font-family:宋体'>像素相关性改进</span></p>

<p class=MsoNormal style='margin-left:21.0pt;text-indent:21.0pt'><span
style='font-size:12.0pt;font-family:宋体'>利用像素间的相关性，可以提高算法的性能，并避免堆栈的溢出。每次填充在同一条扫描线上相邻的一排像素，同时把与它相邻的未填充的种子像素放在堆栈中</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=176 height=171
id="图片 97" src="CG/CG_algorithms/image053.jpg">&nbsp;<img border=0
width=180 height=169 id="图片 99" src="CG/CG_algorithms/image054.jpg">&nbsp;<img
border=0 width=179 height=171 id="图片 100" src="CG/CG_algorithms/image055.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=177 height=167
id="图片 101" src="CG/CG_algorithms/image056.jpg">&nbsp;<img border=0
width=175 height=166 id="图片 102" src="CG/CG_algorithms/image057.jpg">&nbsp;<img
border=0 width=176 height=167 id="图片 103" src="CG/CG_algorithms/image058.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=174 height=164
id="图片 104" src="CG/CG_algorithms/image059.jpg">&nbsp;<img border=0
width=174 height=165 id="图片 106" src="CG/CG_algorithms/image060.jpg">&nbsp;<img
border=0 width=177 height=169 id="图片 107" src="CG/CG_algorithms/image061.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=173 height=164
id="图片 108" src="CG/CG_algorithms/image062.jpg">&nbsp;<img border=0
width=170 height=162 id="图片 109" src="CG/CG_algorithms/image063.jpg">&nbsp;<img
border=0 width=176 height=166 id="图片 110" src="CG/CG_algorithms/image064.jpg"></span></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:9.5pt;font-family:新宋体;
color:black'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-size:20.0pt;font-family:幼圆;background:
#D9D9D9'>裁剪算法<span lang=EN-US>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;</span></span></b></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=412 height=190
id="图片 111" src="CG/CG_algorithms/image065.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=414 height=134
id="图片 112" src="CG/CG_algorithms/image066.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>*</span><span style='font-family:宋体'>裁剪是在进行规范化投影变换后进行的（</span><span
lang=EN-US>NDC</span><span style='font-family:宋体'>坐标空间下）</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>裁剪过程：</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US>1、</span><span
style='font-family:宋体'>判断是否完全落在裁剪窗口内；</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US>2、</span><span
style='font-family:宋体'>是否完全落在裁剪窗口外；</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US>3、</span><span
style='font-family:宋体'>条件（</span><span lang=EN-US>1</span><span
style='font-family:宋体'>、</span><span lang=EN-US>2</span><span style='font-family:
宋体'>）都不能完全确定时，则计算它与一条或多条裁剪边界的交点</span><span lang=EN-US>.</span></p>

<p class=MsoNormal><b><span lang=EN-US style='font-family:"微软雅黑","sans-serif";
color:#333333;background:white'>Cohen-Sutherland</span></b><b><span
style='font-family:"微软雅黑","sans-serif";color:#333333;background:white'>方法</span></b></p>

<p class=MsoNormal><span style='font-family:幼圆'>基于编码的裁剪方法</span></p>

<p class=MsoNormal><span style='font-family:幼圆'>基本思想：对每条直线段分三种情况处理</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=208 height=26
id="图片 113" src="CG/CG_algorithms/image067.jpg">&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img
border=0 width=222 height=26 id="图片 115" src="CG/CG_algorithms/image068.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=205 height=139
id="图片 114" src="CG/CG_algorithms/image069.jpg">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img
border=0 width=231 height=142 id="图片 116" src="CG/CG_algorithms/image070.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=283 height=69
id="图片 117" src="CG/CG_algorithms/image071.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>编码规则：</span></b></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=388 height=167
id="图片 118" src="CG/CG_algorithms/image072.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=389 height=171
id="图片 119" src="CG/CG_algorithms/image073.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=392 height=146
id="图片 121" src="CG/CG_algorithms/image074.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:幼圆'>优点</span></b><span
style='font-family:幼圆'>（两类裁剪场合中非常高效）：</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>（1）</span><span style='font-family:幼圆'>大窗口场合</span></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>（2）</span><span style='font-family:幼圆'>窗口特别小的场合</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:幼圆'>第三种情况求交还可以采用<b>二分法（中点裁剪算法）</b>：</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=316 height=164
id="图片 122" src="CG/CG_algorithms/image075.jpg">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img
border=0 width=205 height=148 id="图片 123" src="CG/CG_algorithms/image076.jpg"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:宋体'>优点：</span><span lang=EN-US>(1)</span><span
style='font-family:宋体'>适合硬件实现；</span><span lang=EN-US>(2)</span><span
style='font-family:宋体'>适合并行运算</span><span lang=EN-US>.</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><b><span lang=EN-US style='font-family:"微软雅黑","sans-serif";
color:#333333;background:white'>Liang-Barsky</span></b><b><span
style='font-family:"微软雅黑","sans-serif";color:#333333;background:white'>算法</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>在<span
lang=EN-US>Cohen-Sutherland</span>算法提出后，梁友栋和<span lang=EN-US>Barsky</span>又针对标准矩形窗口提出了更快的<span
lang=EN-US>Liang-Barsky</span>直线段裁剪算法，<span lang=EN-US>Liang-Barsky</span>算法是<span
lang=EN-US> Cyrus-Beck </span>算法的特例。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><b><span lang=EN-US
style='font-family:幼圆'>Cyrus-Beck</span></b><b><span style='font-family:幼圆'>算法</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US><img border=0
width=226 height=144 id="图片 124" src="CG/CG_algorithms/image077.jpg"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>Cyrus-Beck</span><span style='font-family:幼圆'>算法本质是每次通过裁剪窗口<span
lang=EN-US>(</span>任意凸多边形<span lang=EN-US>, </span>文章最后会说明为什么凹多边形不行<span
lang=EN-US>)</span>的一条边界来确定待裁剪线段的哪部分应当被留下<span lang=EN-US>, </span>最后<span
lang=EN-US>, </span>对所有应该被留下的部分取交集<span lang=EN-US>, </span>便可以求得线段应当留下的部分。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>举个例子<span
lang=EN-US>, </span>假设多边形<span lang=EN-US>ABCDE, </span>那么我们每次使用一条边<span
lang=EN-US>(AB, BC, </span>…<span lang=EN-US>), </span>延长这条边和待裁剪的线段<span
lang=EN-US>, </span>那么最后两条直线必定相交或平行<span lang=EN-US>, </span>如果相交<span
lang=EN-US>, </span>根据交点确定哪部分被留下<span lang=EN-US>, </span>如果平行<span lang=EN-US>,
</span>根据坐标确定哪部分被留下。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>而<span
lang=EN-US>Liang-Barsky</span>算法只是将这个裁剪窗口固定为了一个平行于坐标轴的矩形<span lang=EN-US>, </span>所以<span
lang=EN-US>Liang-Barsky</span>算法和<span lang=EN-US>Cyrus-Beck</span>算法本质是一样的<span
lang=EN-US>, </span>只是<span lang=EN-US>Liang-Barskys</span>算法因为拥有更多信息<span
lang=EN-US>(</span>裁剪窗口是一个平行与坐标轴的矩形<span lang=EN-US>), </span>可以对其中一些步骤进行简化处理。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><b><span lang=EN-US
style='font-family:幼圆'>Liang-Barsky</span></b><b><span style='font-family:幼圆'>算法</span></b></p>

<p class=MsoNormal style='margin-left:0cm;text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>（1）</span><span style='font-family:幼圆'>把被裁剪的红色直线段看 成是一条有方向的线段，把窗口
的四条边分成两类：入边和出边</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US><img border=0
width=240 height=163 id="图片 125" src="CG/CG_algorithms/image078.jpg"><img
border=0 width=269 height=161 id="图片 128" src="CG/CG_algorithms/image079.jpg"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>2</span><span style='font-family:宋体'>）裁剪结果的线段<b>起点</b>是直线和两条入边的交点以及始端点三个点里<b>最前面的一个</b>点，即<b>参数</b></span><b><span
lang=EN-US>u</span></b><b><span style='font-family:宋体'>最大</span></b><span
style='font-family:宋体'>的那个点；裁剪线段的<b>终点</b>是和两条出边的交点以及端点<b>最后面的一个</b>点，取<b>参数</b></span><b><span
lang=EN-US>u</span></b><b><span style='font-family:宋体'>最小</span></b><span
style='font-family:宋体'>的那个点。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>3</span><span style='font-family:宋体'>）用</span><span lang=EN-US>u1</span><span
style='font-family:宋体'>，</span><span lang=EN-US>u2</span><span
style='font-family:宋体'>分别表示线段（</span><span lang=EN-US>u1</span><span
style='font-family:宋体'>≤</span><span lang=EN-US>u2</span><span
style='font-family:宋体'>）可见部分的开始和结束</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US><img border=0
width=179 height=64 id="图片 127" src="CG/CG_algorithms/image080.jpg"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>4</span><span style='font-family:宋体'>）对于直线的参数方程，求判断条件</span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span lang=EN-US><img border=0
width=243 height=60 id="图片 129" src="CG/CG_algorithms/image081.jpg"></span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span lang=EN-US><img border=0
width=294 height=115 id="图片 130" src="CG/CG_algorithms/image082.jpg"></span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span lang=EN-US><img border=0
width=335 height=114 id="图片 131" src="CG/CG_algorithms/image083.jpg"></span></p>

<p class=MsoNormal style='margin-left:21.0pt'><span lang=EN-US><img border=0
width=426 height=127 id="图片 132" src="CG/CG_algorithms/image084.jpg"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>（</span><span
lang=EN-US>5</span><span style='font-family:宋体'>）基于</span><span lang=EN-US>p<sub>k</sub></span><span
style='font-family:宋体'>与</span><span lang=EN-US>q<sub>k</sub></span><span
style='font-family:宋体'>即可判断线段情况</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=267 height=188
id="图片 135" src="CG/CG_algorithms/image085.jpg"><img border=0 width=285
height=188 id="图片 137" src="CG/CG_algorithms/image086.jpg"></span></p>

<p style='margin-top:7.5pt;margin-right:0cm;margin-bottom:7.5pt;margin-left:
0cm;text-indent:21.0pt;background:white'><span lang=EN-US style='font-size:
9.5pt;font-family:"Verdana","sans-serif";color:#111111'>（2）</span><span
style='font-size:9.5pt;font-family:宋体;color:#111111;background:white'>当</span><span
lang=EN-US style='font-size:9.5pt;font-family:"Verdana","sans-serif";
color:#111111;background:white'>pk≠0</span><span style='font-size:9.5pt;
font-family:宋体;color:#111111;background:white'>时</span></p>

<p style='margin-top:7.5pt;margin-right:0cm;margin-bottom:7.5pt;margin-left:
21.0pt;background:white'><span style='font-size:9.5pt;font-family:宋体;
color:#111111;background:white'>线段和窗口边界一共有四个交点，根据</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Verdana","sans-serif";color:#111111;
background:white'>pk</span><span style='font-size:9.5pt;font-family:宋体;
color:#111111;background:white'>的符号，就知道</span><span style='font-size:9.5pt;
font-family:"Verdana","sans-serif";color:#111111;background:white'> </span><span
style='font-size:9.5pt;font-family:宋体;color:#111111;background:white'>哪两个是入交点，哪两个是出交点</span></p>

<p style='margin-top:7.5pt;margin-right:0cm;margin-bottom:7.5pt;margin-left:
0cm;text-indent:21.0pt;background:white'><span style='font-size:9.5pt;
font-family:宋体;color:#111111;background:white'>当</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Verdana","sans-serif";color:#111111;
background:white'>p<sub>k</sub> &lt; 0</span><span style='font-size:9.5pt;
font-family:宋体;color:#111111;background:white'>时：对应入边交点</span><span
style='font-size:9.5pt;font-family:宋体;color:#111111'>；<span style='background:
white'>当</span></span><span lang=EN-US style='font-size:9.5pt;font-family:"Verdana","sans-serif";
color:#111111;background:white'>p<sub>k</sub> &gt; 0</span><span
style='font-size:9.5pt;font-family:宋体;color:#111111;background:white'>时：对应出边交点</span></p>

<p style='margin-top:7.5pt;margin-right:0cm;margin-bottom:7.5pt;margin-left:
0cm;text-indent:21.0pt;background:white'><span style='font-size:9.5pt;
font-family:宋体;color:#111111;background:white'>一共四个</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Verdana","sans-serif";color:#111111;
background:white'>u</span><span style='font-size:9.5pt;font-family:宋体;
color:#111111;background:white'>值，再加上</span><span lang=EN-US style='font-size:
9.5pt;font-family:"Verdana","sans-serif";color:#111111;background:white'>u=0</span><span
style='font-size:9.5pt;font-family:宋体;color:#111111;background:white'>、</span><span
lang=EN-US style='font-size:9.5pt;font-family:"Verdana","sans-serif";
color:#111111;background:white'>u=1</span><span style='font-size:9.5pt;
font-family:宋体;color:#111111;background:white'>两个端点值，总共六个值</span></p>

<p style='margin-top:7.5pt;margin-right:0cm;margin-bottom:7.5pt;margin-left:
0cm;text-indent:21.0pt;background:white'><span style='font-size:9.5pt;
font-family:宋体;color:#111111;background:white'>把</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Verdana","sans-serif";color:#111111;
background:white'>p<sub>k</sub></span><span style='font-size:9.5pt;font-family:
宋体;color:#111111;background:white'>＜</span><span lang=EN-US style='font-size:
9.5pt;font-family:"Verdana","sans-serif";color:#111111;background:white'>0</span><span
style='font-size:9.5pt;font-family:宋体;color:#111111;background:white'>的两个</span><span
lang=EN-US style='font-size:9.5pt;font-family:"Verdana","sans-serif";
color:#111111;background:white'>u</span><span style='font-size:9.5pt;
font-family:宋体;color:#111111;background:white'>值和</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Verdana","sans-serif";color:#111111;
background:white'>0</span><span style='font-size:9.5pt;font-family:宋体;
color:#111111;background:white'>比较去找最大的，把</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Verdana","sans-serif";color:#111111;
background:white'>p<sub>k</sub></span><span style='font-size:9.5pt;font-family:
宋体;color:#111111;background:white'>＞</span><span lang=EN-US style='font-size:
9.5pt;font-family:"Verdana","sans-serif";color:#111111;background:white'>0</span><span
style='font-size:9.5pt;font-family:宋体;color:#111111;background:white'>的两个</span><span
lang=EN-US style='font-size:9.5pt;font-family:"Verdana","sans-serif";
color:#111111;background:white'>u</span><span style='font-size:9.5pt;
font-family:宋体;color:#111111;background:white'>值和</span><span lang=EN-US
style='font-size:9.5pt;font-family:"Verdana","sans-serif";color:#111111;
background:white'>1</span><span style='font-size:9.5pt;font-family:宋体;
color:#111111;background:white'>比较去找最小的，这样就得到两个端点的参数值，最后代回直线参数方程，即求出窗口的两实交点坐标。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US><img border=0
width=206 height=142 id="图片 138" src="CG/CG_algorithms/image087.jpg">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img
border=0 width=271 height=103 id="图片 139" src="CG/CG_algorithms/image088.jpg"></span></p>

<br>

<p class=MsoNormal><b><span style='font-size:20.0pt;font-family:幼圆;background:
#D9D9D9'>光照模型<span lang=EN-US>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></b></p>

<p class=MsoNormal><b><span lang=EN-US style='font-family:"微软雅黑","sans-serif";
color:#333333;background:white'>Phong</span></b><b><span style='font-family:
"微软雅黑","sans-serif";color:#333333;background:white'>模型</span></b></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:幼圆'><img
border=0 width=233 height=161 src="CG/CG_algorithms/image089.jpg"
alt="IMG_256"><br>
</span><span lang=EN-US style='font-family:幼圆;position:relative;top:5.0pt'><img
border=0 width=369 height=21 id="对象 13" src="CG/CG_algorithms/image090.png"></span></p>

<p class=MsoNormal><span style='font-family:幼圆'>表面颜色<span lang=EN-US>=</span>自发光<span
lang=EN-US>+</span>环境光（全局光）<span lang=EN-US>+</span>漫反射<span lang=EN-US>+</span>高光，自发光是可选的</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:幼圆'>公式形式：</span></b><span
lang=EN-US style='font-family:幼圆;position:relative;top:7.0pt;background:#D9D9D9'><img
border=0 width=257 height=27 id="对象 14" src="CG/CG_algorithms/image091.png"></span></p>

<p class=MsoNormal><i><span lang=EN-US style='font-family:幼圆'>k</span></i><sub><span
lang=EN-US style='font-family:幼圆'>a</span></sub><span style='font-family:幼圆'>环境反射系数<span
lang=EN-US>,<i>k</i><sub>d</sub></span>漫反射系数<span lang=EN-US>,<i>k</i><sub>s</sub></span>镜面反射系数，其中<i><span
lang=EN-US>k</span></i><sub><span lang=EN-US>d</span></sub><span lang=EN-US>+<i>k</i><sub>s</sub>=1</span>；求和代表对所有特定光源求和。由上式看出，一旦反射光中三种分量的颜色以及它们的系数<i><span
lang=EN-US>k</span></i><sub><span lang=EN-US>a</span></sub>，<i><span
lang=EN-US>k</span></i><sub><span lang=EN-US>d</span></sub>和<i><span
lang=EN-US>k</span></i><sub><span lang=EN-US>s</span></sub>确定以后，从景物表面上某点达到观察者的反射光颜色就仅仅和光源入射角和视角有关。因此可以说，<span
lang=EN-US>Phong</span>光照模型实际上是纯几何模型。</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:幼圆'>各分量意义：</span></p>

<p class=MsoNormal><b><span style='font-family:幼圆'>环境反射光<span lang=EN-US>
Ambient</span></span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>环境反射光是由环境光<span
lang=EN-US>(</span>照亮整个场景<span lang=EN-US>)</span>在临近物体上经过多次反射所产生的，没有位置和方向，在仅有环境光的情况上，物体的明暗亮度是一样的。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆;position:relative;top:7.0pt'><img border=0 width=68
height=25 id="对象 15" src="CG/CG_algorithms/image092.png"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><i><span lang=EN-US
style='font-family:幼圆'>I</span></i><sub><span style='font-family:幼圆'>α</span></sub><span
style='font-family:幼圆'>为物体的环境光反射亮度，<i><span lang=EN-US>I</span></i><sub><span
lang=EN-US>pa</span></sub>为环境光亮度，<i><span lang=EN-US>K</span></i><sub><span
lang=EN-US>a</span></sub>为物体表面的环境光反射系数</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:幼圆'>漫反射<span lang=EN-US> Diffuse</span></span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>实际上使用的是<span
lang=EN-US>Lambert</span>光照模型，兰伯特余弦定理（<span lang=EN-US>Lambert</span>’<span
lang=EN-US>s cosine law</span>）是模拟漫反射的光照模型，模型表面的光亮度直接取决于光线向量<span lang=EN-US>(light
vector)</span>和表面法线两个向量夹角的余弦值。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆;position:relative;top:7.0pt'><img border=0 width=100
height=25 id="对象 16" src="CG/CG_algorithms/image093.png"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆;position:relative;top:5.0pt'><img border=0 width=232
height=21 id="对象 17" src="CG/CG_algorithms/image094.png"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><i><span lang=EN-US
style='font-family:幼圆'>L</span></i><span style='font-family:幼圆'>为光照方向，<i><span
lang=EN-US>N</span></i>为表面法向，θ是它们之间的夹角</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:幼圆'>镜面反射<span lang=EN-US>
Specular</span></span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>Lambert</span><span style='font-family:幼圆'>光照模型并没有考虑到表面光泽的镜面反射效果。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>对于理想的镜面反射，入射角等于反射角。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆;position:relative;top:7.0pt'><img border=0 width=107
height=27 id="对象 18" src="CG/CG_algorithms/image095.png"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><i><span lang=EN-US
style='font-family:幼圆'>I</span></i><sub><span lang=EN-US style='font-family:
幼圆'>ps</span></sub><span style='font-family:幼圆'>为入射光的光亮度，<span lang=EN-US>θ</span>为镜面反射方向和视线方向的夹角，介于<span
lang=EN-US>0</span>到<span lang=EN-US>90</span>之间，<i><span lang=EN-US>n</span></i>为镜面反射光的汇聚指数<span
lang=EN-US>(</span>光滑度<span lang=EN-US>)</span>，<i><span lang=EN-US>K</span></i><sub><span
lang=EN-US>s</span></sub>为镜面反射系数</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=132 height=136 id="图片 14" src="CG/CG_algorithms/image096.png"
alt="IMG_256"><img border=0 width=138 height=136
src="CG/CG_algorithms/image097.png" alt="IMG_256"></span><span lang=EN-US
style='font-family:幼圆'>Phong</span><span style='font-family:幼圆'>模型为左图</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:幼圆'>反射向量<span lang=EN-US>R</span>的计算<span
lang=EN-US>(Phong</span>模型计算中的一个关键步骤<span lang=EN-US>)</span>：</span></b></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=188 height=167 src="CG/CG_algorithms/image098.png"
alt="IMG_256"><img border=0 width=352 height=114
src="CG/CG_algorithms/image099.png" alt="IMG_256"></span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>*<b><i>I</i></b></span><span
style='font-family:幼圆'>指向光源时右式需要加负号</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><span style='font-family:幼圆'>实现</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=295 height=326
id="图片 19" src="CG/CG_algorithms/image100.jpg"></span></p>

<p class=MsoNormal><span style='font-family:宋体'>具体实现与理论公式稍有差别：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>实现中增加了物体的颜色与灯光颜色，同时最后叠加颜色时使用了相乘混合以减少高光颜色的突兀感（虽然高光颜色本应只与灯光颜色有关）。</span></p>

<p class=MsoNormal><b><span style='font-family:幼圆'>补充</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>Phong</span><span style='font-family:幼圆'>光照模型是真实图形学中提出的第一个有影响的光照明模型，该模型只考虑物体对直接光照的反射作用，认为环境光是常量，没有考虑物体之间相互的反射光，物体间的反射光只用环境光表示。<span
lang=EN-US>Phong</span>光照模型属于简单光照模型。</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=545 height=147 src="CG/CG_algorithms/image101.jpg"
alt="IMG_256"></span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=544 height=319 id="图片 20" src="CG/CG_algorithms/image102.jpg"
alt="IMG_256"></span></p>

<p class=MsoNormal><b><span lang=EN-US style='font-family:"微软雅黑","sans-serif";
color:#333333;background:white'>Gouraud</span></b><b><span style='font-family:
"微软雅黑","sans-serif";color:#333333;background:white'>着色</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>在光照着色器的早期，开发者曾经在<b>顶点着色器中</b>实现冯氏光照模型，相比片段来说，顶点要少得多，因此会更高效，所以（开销大的）光照计算频率会更低。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>然而，顶点着色器中的最终颜色值是仅仅只是那个顶点的颜色值，片段的颜色值是由插值光照颜色所得来的。结果就是这种光照看起来不会非常真实，除非使用了大量顶点。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=288 height=162 src="CG/CG_algorithms/image103.png"
alt="IMG_256"></span></p>

<p class=MsoNormal><b><span lang=EN-US style='font-size:12.0pt;font-family:
幼圆'>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US style='font-family:"微软雅黑","sans-serif";
color:#333333;background:white'>Blinn-Phong</span></b><b><span
style='font-family:"微软雅黑","sans-serif";color:#333333;background:white'>模型</span></b></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:幼圆'><img
border=0 width=255 height=161 id="图片 21" src="CG/CG_algorithms/image104.jpg"
alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>Blinn-Phong</span><span style='font-family:幼圆'>模型与<span
lang=EN-US>Phong</span>模型的主要区别就在于镜面光的计算，<span lang=EN-US>Phong</span>模型中计算反射光线的向量是一件相对比较耗时的任务，因此<span
lang=EN-US>Blinn-Phong</span>对这一点进行了改进</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><b><span style='font-family:幼圆'>它们的唯一的区别就是，<span
lang=EN-US>Blinn-Phong</span>测量的是法线与半程向量之间的夹角，而<span lang=EN-US>Phong</span>模型测量的是观察方向与反射向量间的夹角</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>在<span
lang=EN-US>Blinn-Phong</span>中：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'><img border=0 width=401 height=35
src="CG/CG_algorithms/image105.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US><img border=0
width=103 height=58 src="CG/CG_algorithms/image106.jpg"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><i><span lang=EN-US
style='font-family:幼圆'>K</span></i><sub><span lang=EN-US style='font-family:
幼圆'>s</span></sub><span style='font-family:幼圆'>：物体对于反射光线的衰减系数，<b><i><span
lang=EN-US>N</span></i></b>：表面法向量，</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><b><i><span lang=EN-US
style='font-family:幼圆'>H</span></i></b><b><span style='font-family:幼圆'>：光入射方向<span
lang=EN-US>L</span>和视点方向<span lang=EN-US>V</span>的中间向量</span></b><span
style='font-family:幼圆'>，<i><span lang=EN-US>Shininess</span></i>：高光系数</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><b><span lang=EN-US
style='font-family:幼圆'>Blinn-Phong</span></b><b><span style='font-family:幼圆'>的优点：</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>（<span
lang=EN-US>1</span>）光照结果不会出现断层问题。<span lang=EN-US>Phong</span>模型不仅对真实光照有很好的近似，而且性能也很高，但是它的镜面反射会在一些情况下出现问题：</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=176 height=138 id="图片 22" src="CG/CG_algorithms/image107.jpg"
alt="IMG_256"><img border=0 width=361 height=127
src="CG/CG_algorithms/image108.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>可以看到，在镜面高光区域的边缘出现了一道很明显的断层。问题的原因是观察向量和反射向量间的夹角不能大于<span
lang=EN-US>90</span>度。如果点积的结果为负数，镜面光分量会变为<span lang=EN-US>0.0</span>（右图）</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>引入半程向量后就不会再看到冯氏光照中高光断层的情况。下面是两种方法在镜面光分量为<span
lang=EN-US>0.5</span>时的对比：</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=449 height=177 src="CG/CG_algorithms/image109.jpg"
alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>除此之外，它们之间还有一些细微差别：半程向量与表面法线的夹角通常会小于观察与反射向量的夹角。所以，如果想获得和<span
lang=EN-US>Phong</span>着色类似的效果，就必须在使用<span lang=EN-US>Blinn-Phong</span>模型时将镜面反光度设置得更高，通常我们会选择<span
lang=EN-US>Phong</span>着色时反光度分量的<span lang=EN-US>2</span>到<span lang=EN-US>4</span>倍。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>下面是<span
lang=EN-US>Phong</span>着色反光度为<span lang=EN-US>8.0</span>，<span lang=EN-US>Blinn-Phong</span>着色反光度为<span
lang=EN-US>32.0</span>时的对比：</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:12.0pt;font-family:宋体'><img
border=0 width=449 height=176 src="CG/CG_algorithms/image110.jpg"
alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>Blinn-Phong</span><span style='font-family:幼圆'>的镜面光分量会比冯氏模型更锐利一些。为了得到与<span
lang=EN-US>Phong</span>模型类似的结果，可能会需要不断进行一些微调，但<span lang=EN-US>Blinn-Phong</span>模型通常会产出更真实的结果。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>（<span
lang=EN-US>2</span>）速度快。<span lang=EN-US>H</span>的计算比起反射向量<span lang=EN-US>R</span>的计算简单的多，<span
lang=EN-US>R</span>向量的计算需要若干次的向量乘法与加法，而<span lang=EN-US>H</span>的计算仅仅需要一次加法。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><b><span lang=EN-US
style='font-family:幼圆'>Blinn-Phong</span></b><b><span style='font-family:幼圆'>的缺点：</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>在相同条件下<span
lang=EN-US>Blinn-Phong</span>的高光范围要比<span lang=EN-US>Phong</span>更大，写实效果<span
lang=EN-US>Phong</span>光照模型更好。但算法简单，运行速度快是<span lang=EN-US>Blinn-Phong</span>光照模型的优点。</span></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=150 height=168
src="CG/CG_algorithms/image111.jpg"><img border=0 width=146 height=158
src="CG/CG_algorithms/image112.jpg"></span></p>

<p class=MsoNormal><span style='font-family:宋体'>左</span><span lang=EN-US>Phong</span><span
style='font-family:宋体'>右</span><span lang=EN-US>Blinn-Phong</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>实现</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US><img border=0
width=427 height=199 id="图片 13" src="CG/CG_algorithms/image113.png"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:幼圆'>补充</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>1977</span><span style='font-family:幼圆'>年，<span
lang=EN-US>James F. Blinn</span>在冯氏着色模型上加以拓展，引入了<span lang=EN-US>Blinn-Phong</span>着色模型。<span
lang=EN-US>Blinn-Phong</span>模型与冯氏模型非常相似，但是它对镜面光模型的处理上有一些不同，让我们能够解决之前提到的问题。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-family:幼圆'>Blinn-Phong</span><span style='font-family:幼圆'>模型不再依赖于反射向量，而是采用了所谓的半程向量<span
lang=EN-US>(Halfway Vector)</span>，即光线与视线夹角一半方向上的一个单位向量。当半程向量与法线向量越接近时，镜面光分量就越大。</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:幼圆'>&nbsp;</span></p>

<p class=MsoNormal><b><span lang=EN-US style='font-family:"微软雅黑","sans-serif";
color:#333333;background:white'>PBR(Physically Based Rendering)</span></b><b><span
style='font-family:"微软雅黑","sans-serif";color:#333333;background:white'>模型</span></b></p>

<p class=MsoNormal><span lang=EN-US><img border=0 width=379 height=181
id="图片 15" src="CG/CG_algorithms/image114.jpg"></span></p>

<p class=MsoNormal><span style='font-family:宋体'>基于物理的渲染是使用了一种更符合物理学规律的方式来模拟光线，因此这种渲染方式比我们原来的</span><span
lang=EN-US>Phong</span><span style='font-family:宋体'>或</span><span lang=EN-US>Blinn-Phong</span><span
style='font-family:宋体'>光照算法相比总体上看起来要更真实一些。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>虽然如此，基于物理的渲染仍然只是对基于物理原理的现实世界的一种近似，这也就是为什么它被称为基于物理的着色</span><span
lang=EN-US>(Physically based Shading) </span><span style='font-family:宋体'>而非物理着色</span><span
lang=EN-US>(Physical Shading)</span><span style='font-family:宋体'>的原因。判断一种</span><span
lang=EN-US>PBR</span><span style='font-family:宋体'>光照模型是否是基于物理的，必须满足以下三个条件：</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span
style='font-family:宋体'>基于微平面</span><span lang=EN-US>(Microfacet)</span><span
style='font-family:宋体'>的表面模型</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span
style='font-family:宋体'>能量守恒</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span
style='font-family:宋体'>应用基于物理的</span><span lang=EN-US>BRDF</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><b><span style='font-family:"微软雅黑","sans-serif";color:#333333;
background:white'>金属质地工作流<span lang=EN-US>(Metallic Workflow)</span>方案</span></b></p>

<p class=MsoNormal><b><span style='font-family:宋体'>微平面理论</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>所有的</span><span
lang=EN-US>PBR</span><span style='font-family:宋体'>技术都基于微平面理论。这项理论认为，达到微观尺度之后任何平面都可以用被称为微平面</span><span
lang=EN-US>(Microfacets)</span><span style='font-family:宋体'>的细小镜面来进行描绘，在微观尺度下，没有任何平面是完全光滑的。然而由于这些微平面已经微小到无法逐像素的继续对其进行区分，因此我们只有假设一个粗糙度</span><span
lang=EN-US>(Roughness)</span><span style='font-family:宋体'>参数，然后用统计学的方法来概略的估算微平面的粗糙程度。</span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'><img border=0 width=505 height=94
id="图片 16" src="CG/CG_algorithms/image115.png" alt="IMG_256"></span></p>

<p class=MsoNormal style='text-indent:21.0pt'><span lang=EN-US
style='font-size:12.0pt;font-family:宋体'><img border=0 width=516 height=105
id="图片 17" src="CG/CG_algorithms/image116.jpg" alt="IMG_256"></span></p>

<p class=MsoNormal align=center style='text-align:center;text-indent:21.0pt'><span
style='font-family:宋体'>较高的粗糙度值显示出来的镜面反射轮廓要更大</span></p>

<p class=MsoNormal align=center style='text-align:center;text-indent:21.0pt'><span
style='font-family:宋体'>与之相反，较小的粗糙显示出的镜面反射轮廓则更小更锐利</span></p>

<p class=MsoNormal><b><span style='font-family:宋体'>能量守恒理论</span></b></p>

<p class=MsoNormal style='text-indent:21.0pt'><span style='font-family:宋体'>微平面近似法使用了这样一种形式的能量守恒</span><span
lang=EN-US>(Energy Conservation)</span><span style='font-family:宋体'>：出射光线的能量永远不能超过入射光线的能量（发光面除外）。</span></p>

</div>

</body>

</html>
