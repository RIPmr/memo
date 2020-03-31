# LinearAlgebra

线性代数

## 特征向量/特征值
### 通俗解释
矩阵可以看成是对某一坐标系下运动过程的描述，于是:
- 特征向量就是该坐标系每一个坐标轴指向的方向
- 特征值可以看成是每个轴向的长度(也就是运动的距离或运动的速度)

<center><img width="70%" src="Pics/math/66.gif"/></center>

<center><img width="70%" src="Pics/math/67.gif"/></center>

### 应用
- 可以用在研究物理、化学领域的微分方程、连续的或离散的动力系统中。例如，在力学中，惯量的特征向量定义了刚体的主轴。惯量是决定刚体围绕质心转动的关键数据；
- 生态学家用来预测原始森林遭到何种程度的砍伐，会造成猫头鹰的种群灭亡；
- 著名的图像处理中的PCA方法，选取特征值最高的k个特征向量来表示一个矩阵，从而达到降维分析+特征显示的方法，还有图像压缩的K-L变换。再比如很多人脸识别，数据流模式挖掘分析等方面。
- 在谱系图论中，一个图的特征值定义为图的邻接矩阵A的特征值，或者（更多的是）图的拉普拉斯算子矩阵，Google的PageRank算法就是一个例子。

<center><img width="70%" src="Pics/math/68.png"/></center>
<center>PCA主成分分析</center>

## 仿射变换
### 先看线性变换
线性变换从几何直观有三个要点：
- 变换前是直线的，变换后依然是直线
- 直线比例保持不变
- 变换前是原点的，变换后依然是原点

例如对于下面这个正方形：

<center><img width="40%" src="Pics/math/69.png"/></center>

我们分别对它做旋转和推移(两种都是线性变换)：

<table><tr>
	<td>
		<center><img width="80%" src="Pics/math/70.png"/></center>
		<center>旋转</center>
	</td>
	<td>
		<center><img width="80%" src="Pics/math/71.png"/></center>
		<center>推移</center>
	</td>
</tr></table>

或者组合这两种操作，仍然是线性变换。所以可得，线性变换是通过矩阵乘法来实现的：

<table><tr>
	<td>
		<center><img width="80%" src="Pics/math/72.png"/></center>
		<center>组合操作</center>
	</td>
	<td>
		<center><img width="80%" src="Pics/math/73.png"/></center>
		<center>矩阵乘法</center>
	</td>
</tr></table>

### 再看仿射变换
仿射变换从几何角度看只有两个要点：
- 变换前是直线的，变换后依然是直线
- 直线比例保持不变

相比线性变换少了原点保持不变这一条。比如平移变换：

<center><img width="40%" src="Pics/math/74.png"/></center>

所以我们表示仿射变换为：

<center><img width="20%" src="Pics/math/75.png"/></center>

### 通过线性变换完成仿射变换
线性变换与仿射变换统一而优美的地方在于：

增加一个维度之后，就可以在高纬度通过线性变换来完成低纬度的仿射变换。

<center><img width="50%" src="Pics/math/76.png"/></center>

用动画来描述就是这样(可以看作变换过程中三维图形的中心是不变的)：

<center><img width="50%" src="Pics/math/Transform.gif"/></center>

## 相似矩阵
### 定义
<center><img width="80%" src="Pics/math/77.png"/></center>

### 通俗解释
所谓相似矩阵，就是相同的变换在不同坐标系下的描述。比如常见的，把直角坐标系（xy坐标系）的圆方程换元为极坐标（pθ坐标系）下：

<center><img width="40%" src="Pics/math/78.png"/></center>

<center><img width="60%" src="Pics/math/79.png"/></center>

换元之后数式和图像都变简单了，相似变换也是这样的目的。

### 应用

例如，对于矩阵A：

<center><img width="15%" src="Pics/math/80.png"/></center>

可以这样去分解：

<center><img width="25%" src="Pics/math/81.png"/></center>

其中：

<center><img width="30%" src="Pics/math/82.png"/></center>


B是对角阵，计算起来就相对方便，所以说相似变换就是坐标转换，转换到一个更方便计算的坐标系下做计算。

## 秩
### 什么是秩
-「秩」是图像经过矩阵变换之后的空间维度
-「秩」是列空间的维度

### 空间维度
什么叫“空间维度”？举个例子：

我们通过矩阵对一个二维图形进行旋转：

<table><tr>
	<td>
		<center><img width="60%" src="Pics/math/83.png"/></center>
		<center>原始图形</center>
	</td>
	<td>
		<center><img width="60%" src="Pics/math/84.png"/></center>
		<center>旋转后</center>
	</td>
</tr></table>

旋转后的图形依然是一个二维图形，因此秩为2；下面我们再分别通过以下矩阵对图形进行变换：

<table><tr>
	<td>
		<center><img width="90%" src="Pics/math/87.png"/></center>
	</td>
	<td>
		<center><img width="90%" src="Pics/math/88.png"/></center>
	</td>
</tr></table>

<table><tr>
	<td>
		<center><img width="70%" src="Pics/math/85.png"/></center>
		<center>转换到一维，秩为1</center>
	</td>
	<td>
		<center><img width="70%" src="Pics/math/86.png"/></center>
		<center>转换到点，秩为0</center>
	</td>
</tr></table>

所以，「秩」是图像经过矩阵变换之后的列空间维度。

### 注意
!> 矩阵的「秩」是列空间的维度并非严格准确的说法，列空间的维度准确来说，是「列秩」，行空间的维度是「行秩」，但是，还好有「秩」=「列秩」=「行秩」是恒成立的。所以直接把「列秩」称为「秩」也不算错误。

## 迹
### 定义
线性代数中，把方阵的对角线之和称为“迹”：

<center><img width="50%" src="Pics/math/89.png"/></center>

### 为什么叫做“迹”
首先我们明确两个定义：
- 坐标系是什么？

	这在线性代数里面称为<strong>基</strong>

- 映射法则是什么？

	这在线性代数里面称为<strong>线性变换</strong>

所以我们知道所谓矩阵就是指定基下的线性变换，而同一个线性变换在不同基下的矩阵，就是相似矩阵。

再细看相似矩阵的性质我们会发现，<strong>相似矩阵的“迹”都相等</strong>。也就是说，这个线性变换，悄悄在这两个相似矩阵A、B中留下了<strong>痕迹</strong>，就是它们的主对角线之和相等。

主对角线之和因此称为“迹”。

从另外一个观点来看，我们也可以认为“迹”与坐标无关，也可以说<strong>“迹”是相似不变量</strong>。

### 相似矩阵的“迹”、行列式、特征值的关系
#### 行列式
令A，B代表不同基下的同一个线性变换，而根据行列式的意义，行列式代表的是线性变换的伸缩比例。

既然是比例，那么也和坐标无关：|A|=|B|=1

所以行列式也是一个相似不变量。

#### 特征值
根据特征值分解的定义，特征值矩阵λ=Q^(-1)AQ

可见，λ和A，B也是相似矩阵。显而易见，对A，B求特征值矩阵都得到的是同一个λ（特征向量有所不同，因为在不同的基下）：

<center><img width="60%" src="Pics/math/91.png"/></center>

特征值是两个复数。根据λ，我们可以得到迹为：

	-0.41615+0.90930i+(-0.41615-0.90930i)=-0.923

行列式为：

	(-0.41615+0.90930i)\times(-0.41615-0.90930i)=1

更一般地可以得到这两个相似不变量分别为：

	迹=λ1 + λ2 + ...

	行列式=λ1·λ2·...

	其中λ1,λ2,...是矩阵的特征值。

什么是特征，<strong>不被变换所改变的就是特征</strong>。

迹、行列式都是<strong>相似变换中的不变量</strong>，也就是线性变换的特征，现在全部被特征值表示了出来。

所以特征值这个名字名符其实。

## 奇异值
### 定义
<center><img width="100%" src="Pics/math/60.png"/></center>

### 通俗理解
用翻绳游戏来举例：

<center><img width="60%" src="Pics/math/46.jpg"/></center>

我们可以认为绳子的花型是由两个方向的力合成的，容易想象，如果其中一个力（相比另外一个力而言）比较小的话，那么绳子的形状基本上由大的那个力来决定。

所以<strong>奇异值分解，就是把矩阵分成多个“分力”。奇异值的大小，就是各个“分力”的大小。</strong>

### 奇异值分解
下面通过一个具体的矩阵例子来解释：

<center><img width="20%" src="Pics/math/46.png"/></center>

我们通过单位圆来观察矩阵，把这个单位圆的每一点都通过A进行变换，得到一个椭圆：

<table><tr>
	<td>
		<center><img width="60%" src="Pics/math/47.png"/></center>
		<center>单位圆</center>
	</td>
	<td>
		<center><img width="60%" src="Pics/math/48.png"/></center>
		<center>基于A变换后</center>
	</td>
</tr></table>

对A进行奇异值分解：

<center><img width="46%" src="Pics/math/49.png"/></center>

实际上，我们将A分为了两个“分力”：

<center><img width="80%" src="Pics/math/50.png"/></center>

对于第一个分力：

<center><img width="50%" src="Pics/math/51.png"/></center>

其作用在单位圆这个“橡皮筋”上的效果：

<center><img width="40%" src="Pics/math/52.png"/></center>

再来看第二个分力：

<center><img width="50%" src="Pics/math/55.png"/></center>

其作用在单位圆这个“橡皮筋”上的效果：

<center><img width="40%" src="Pics/math/53.png"/></center>

这两个“分力”一起作用的时候，单位圆这个“橡皮筋”被拉成了椭圆：

<center><img width="40%" src="Pics/math/54.png"/></center>

### 奇异值决定了什么
奇异值分解实际上把矩阵的变换分为了三部分：旋转、拉伸、投影(方阵没有投影)。

例如，对于上一节中的矩阵A：

<center><img width="50%" src="Pics/math/56.png"/></center>

于是，从右到左(分解后的矩阵)，单位圆先被旋转，再被拉伸，最后又被旋转：

<table><tr>
	<td>
		<center><img width="70%" src="Pics/math/57.png"/></center>
		<center>旋转</center>
	</td>
	<td>
		<center><img width="60%" src="Pics/math/58.png"/></center>
		<center>拉伸</center>
	</td>
	<td>
		<center><img width="60%" src="Pics/math/59.png"/></center>
		<center>再旋转，得到最终结果</center>
	</td>
</tr></table>

所以，奇异值决定了形变，大小决定在形变中的重要性。

### 应用
根据奇异值分解、以及奇异值的特点，有很多应用。
比如，可以把图片转为矩阵，通过丢弃不重要的奇异值(即取前n个奇异值重建图像)，进行压缩：

<table><tr>
	<td>
		<center><img width="100%" src="Pics/math/62.png"/></center>
	</td>
	<td>
		<center><img width="100%" src="Pics/math/63.png"/></center>
	</td>
	<td>
		<center><img width="100%" src="Pics/math/64.png"/></center>
	</td>
	<td>
		<center><img width="100%" src="Pics/math/61.png"/></center>
	</td>
</tr></table>

从上面的图片的压缩结果中可以看出来，奇异值可以被看作成一个矩阵的代表值，或者说，奇异值能够代表这个矩阵的信息。当奇异值越大时，它代表的信息越多。因此，我们取前面若干个最大的奇异值，就可以基本上还原出数据本身。

如下，可以作出奇异值数值变化和前部分奇异值和的曲线图:

<center><img width="100%" src="Pics/math/65.png"/></center>

从上面第1个图可以看出，奇异值下降是非常快的，因此可以只取前面几个奇异值，便可基本表达出原矩阵的信息。从第2个图，可以看出，当取到前100个奇异值时，这100个奇异值的和已经占总和的95%左右。

## 二次型
### 用矩阵来研究二次方程
考虑如下的一元二次方程以及二元二次方程，给它们增加一次项和二次项(例如：y=x^2-2x，x^2+xy+y^2-x=1)并不会改变图形的形状，只会改变图形的位置或使得图像看起来有一些伸缩：

<table><tr>
	<td>
		<center><img width="60%" src="Pics/math/31.png"/></center>
		<center>一元二次方程</center>
	</td>
	<td>
		<center><img width="60%" src="Pics/math/32.png"/></center>
		<center>二元二次方程</center>
	</td>
	<td>
		<center><img width="80%" src="Pics/math/33.png"/></center>
		<center>二元二次方程加一次项</center>
	</td>
</tr></table>

可见对于二次函数或者二次方程，二次部分是主要部分，往往研究二次这部分就够了。

因为二次函数（方程）的二次部分最重要，为了方便研究，我们把含有n个变量的二次齐次函数：

<center><img width="70%" src="Pics/math/34.png"/></center>

或者二次齐次方程称为<strong>二次型</strong>。

### 二次型矩阵
于是我们可以用矩阵来表示二次型：

<center><img width="50%" src="Pics/math/35.png"/></center>

更一般地：

<center><img width="50%" src="Pics/math/36.png"/></center>

写成更线代的形式：

<center><img width="50%" src="Pics/math/37.png"/></center>

所以有下面一一对应的关系：

<center><img width="50%" src="Pics/math/38.png"/></center>

所以在线代里面，就是通过一个对称矩阵，去研究某个二次型。

### 为什么要用矩阵
例如，对于下面的圆，我们改变其二次型矩阵即可得到椭圆。

基于矩阵变换意味着圆和椭圆之间是线性关系，也就是通过矩阵变换就可以从圆变为椭圆；

更一般地，我们会发现双曲线和圆之间是仿射变换的关系：

<table><tr>
	<td>
		<center><img width="80%" src="Pics/math/39.png"/></center>
		<center>圆</center>
	</td>
	<td>
		<center><img width="80%" src="Pics/math/40.png"/></center>
		<center>椭圆</center>
	</td>
	<td>
		<center><img width="80%" src="Pics/math/41.png"/></center>
		<center>双曲线</center>
	</td>
</tr></table>

到这里我们知道，其实圆、椭圆、双曲线之间的关系十分紧密，它们之所以都被称之为圆锥曲线，是因为它们都是圆锥体和平面的交线（也即平面的运动是线性的、或者是仿射的）：

<center><img width="50%" src="Pics/math/curve.gif"/></center>

### 规范化
所谓规范化，就是把图形“扶正”。比如下面这个椭圆看起来有点歪，不太好处理，我们来把它扶正，这就叫做规范化。

矩阵代表了运动，包含：旋转、拉伸、投影；而对于方阵，因为没有维度的改变，所以就没有投影这个运动了，只有：旋转、拉伸。

具体到这个椭圆的矩阵：

<table><tr>
	<td>
		<center><img width="80%" src="Pics/math/42.png"/></center>
		<center>歪的椭圆</center>
	</td>
	<td>
		<center><img width="80%" src="Pics/math/43.png"/></center>
		<center>拉伸</center>
	</td>
</tr></table>

我们把矩阵进行特征值分解，对于二次型矩阵，都是对称矩阵，所以特征值分解总可以得到正交矩阵与对角矩阵。而特征值分解实际上就是把运动分解了：

<center><img width="50%" src="Pics/math/44.png"/></center>

那么我们只需要保留拉伸部分，就相当于把矩阵扶正了：

<center><img width="40%" src="Pics/math/45.png"/></center>

所以，用二次型矩阵进行规范化是非常轻松的事情。

## 正定
### 通俗理解
正定是对二次函数有效的一个定义，对方程无效。

首先半正定矩阵定义为: X^TMX≥0，其中 X 是向量，M 是变换矩阵；

我们换一个思路看这个问题，矩阵变换中 MX 代表对向量 X 进行变换，我们假设变换后的向量为Y = MX；

于是半正定矩阵可以写成：X^TY≥0 ，他是两个向量的内积；

同时我们也有公式：cos(θ) = X^TY / (||X|| * ||Y||)，||X||，||Y||代表向量 X,Y 的长度，是他们之间的夹角； 

于是半正定矩阵意味着 cos(θ) ≥ 0, 也就是说，正定、半正定矩阵代表一个向量经过它的变化后的向量与其本身的夹角小于等于90度。

当A为一个n阶实对称矩阵时，二次型f(x) = x^TAx是一个定义在R^n上的实值函数。
<strong>以二元函数为例，正定即其对应的曲面在底面的上方，负定即在底面下方，不定即曲面部分在上部分在下。</strong>

<div align=center><img width="80%" src="Pics/math/24.jpg"/></div>
<center>从左至右：正定、半正定、不定、负定</center>

数学形式上等价于，矩阵A(A为对称矩阵)的特征值全大于0，特征值全大于0，以其对应的特征向量为基时，曲面相当于往上翻的，因为都是拉伸变换。

### 正定的判定
一个二次型f(x)=x^TAx是
- 正定的，若对所有x≠0，有f(x)>0；
- 负定的，若对所有x≠0，有f(x)<0；
- 不定的，若f(x)既有正值，又有负值；
- 半正定的，若对所有x，有f(x)≥0；
- 半负定的，若对所有x，有f(x)≤0；

有两种判定方法：
1. 求出A的所有特征值

- 若A的特征值均为正数，则A是正定的；
- 若A的特征值均为负数，则A为负定的；
- 若A的特征值有正有负，则A为不定的。

2. 计算A的各阶主子式

- 若A的各阶主子式均大于零，则A是正定的；
- 若A的各阶主子式中，奇数阶主子式为负，偶数阶为正，则A为负定的。

## 黑塞矩阵(Hessian Matrix)
黑塞矩阵（Hessian Matrix），又译作海森矩阵、海瑟矩阵、海塞矩阵等，是一个多元函数的二阶偏导数构成的方阵，描述了函数的局部曲率。黑塞矩阵常用于牛顿法解决优化问题，利用黑塞矩阵可判定多元函数的极值问题。在工程实际问题的优化设计中，所列的目标函数往往很复杂，为了使问题简化，常常将目标函数在某点邻域展开成泰勒多项式来逼近原函数，此时函数在某点泰勒展开式的矩阵形式中会涉及到黑塞矩阵。

### 应用
一般地，设n元实值函数f(x)有三阶连续偏导数，x0是f(x)的一个稳定点，那么若f在x0点的Hessian矩阵：

<details>
<summary>稳定点</summary>
<p>稳定点就是导数值等于0的点（图象上看，有水平切线）。</p>
<p><strong>稳定点与分界点：</strong></p>
<p>分界点是单调性改变的点，即分界点两边函数的单调性改变（比如左边单调增右边单调减）一般来说，对于可导函数，分界点都是稳定点，稳定点不一定是分界点（稳定点导数为零，但是它两侧点的导数值可能同号。</p>
<p>比如y=x³在x=0处，导数为0，但是x=0两边的单调性没有变化，故而不是分界点。</p>
<p><strong>稳定点与极值点：</strong></p>
<p>驻点和不可导点都可能是极值点。 也就是说，极值点只能是驻点或不可导点，但驻点或不可导点不一定是极值点。</p>
<p>极值点也不一定是稳定点，当f在极值点不可微时，这个点就不是稳定点，但它仍是极值点；稳定点也不一定是极值点，如函数f=x³在(0，0)处是稳定点，但不是极值点。</p>
</details>

<div align=center><img width="40%" src="Pics/math/24.png"/></div>

- 为正定，则f(x)在x0点达到极小值
- 若负定，则f(x)在点x0达到极大值
- 若不定，则x0不是极值点
- 若半正定或半负定，则f(x)在x0处的极值性质需进一步分析

此外，对于二次型的矩阵：

<div align=center><img width="60%" src="Pics/math/25.png"/></div>

称为函数f(x,y)在点(x0,y0)处的Hessian矩阵。

<details>
<summary>例题</summary>
<div align=center><img width="60%" src="Pics/math/26.png"/></div>

<div align=center><img width="60%" src="Pics/math/27.png"/></div>

<div align=center><img width="60%" src="Pics/math/28.png"/></div>

<div align=center><img width="60%" src="Pics/math/29.png"/></div>

<div align=center><img width="60%" src="Pics/math/30.png"/></div>
</details>