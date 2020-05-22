﻿# Vis Note

《大数据可视化》课程笔记

## 第一章
### 可视化初识
可视分析系统能够帮助我们思考，基于人们各自背景知识储备，找到新的兴趣点，提出新的分析目标

可视分析系统的输入输出：
```
输入：数据（data）
输出：视觉形式（visual form）
目标：深入理解（insight）
```

### 可视化的前世今生
- 16世纪：图表萌芽
- 17世纪：物理测量
- 18世纪：图形符号
- 19世纪：可视化应用
- 20世纪中期:	
1900-1987：信息可视化<br>
1987-2004：科学可视化
- 21世纪：	
2004-至今：可视分析学

### 可视化深入理解及掌握
#### 可视化工具
- Tableau				
不需要编程，快速轻量，用户友好。
- D3.js				
开源JS库，需要编程基础，D3 允许将数据与被选择的元素绑定在一起，为根据数据来操作元素提供方便。
- Vega/Vega-Lite		
一种可视化语法，用于创建、保存和共享交互式可视化设计的声明式语言。能够以JSON格式描述可视化的视觉外观和交互行为，并使用Canvas或SVG生成基于Web的视图。
- Processing			
一种开源编程语言，运行在JVM上，其最初目标是用来形象地教授计算机科学的基础知识。之后，它逐渐演变成了可用于创建图形可视化专业项目的一种环境，不仅可以绘制二维的静态图形与动画，同时也有三维图形的支持。

#### 可视化分支
三个分支   | 应用领域							|  研究对象及研究内容  
-		   |-									|-
<div style="width: 70pt">科学可视化 | 科学与工程领域						| 带有空间信息和几何信息的三维测量数据、计算模拟数据、医学影像数据;<br>具体包括：标量场可视化、向量场可视化、张量场可视化（标量 → 0阶张量、向量 → 1阶张量） |
信息可视化 | 跨学科领域							| 非结构化、非几何的抽象数据，侧重于抽象数据集，如非结构化文本或者高维空间当中的点;<br>具体包括：时空数据可视化、层次与网络结构数据可视化、文本与跨媒体数据可视化、多变量数据可视化 |
可视分析学 | 需要人参与理解和决策的多种实际问题 | 以交互式界面为基础的分析推理科学，结合了可视化、人机交互与数据挖掘;<br>具体包括：地理分析、信息分析、科学分析、统计分析、知识发现、交互、数据管理和知识表达、表达、作业和传播、感知与认知科学 |

### 错题记录




## 第二章
### 视觉感知与认知

#### 感知
指客观事物通过人的感觉器官在人脑中形成的直接反映

> 感知系统基于相对判断，而非绝对判断<br>使用相同的参照物或者相互对齐，有助于人们做出更加准确的相对判断

#### 认知
指人们获得知识或应用知识的过程，或信息加工的过程

#### 总结
- 记忆在人类认知过程中起着至关重要的作用，但工作记忆容量十分有限
- 可视化可以作为外部辅助来增强工作记忆
- 在可视化中突出变化，可以减少认知负担


### 格式塔(Gestalt)理论
- 结构比元素重要，视觉形象首先作为统一的整体被认知，而后才以部分的形式被认知

!> 疑问: 格式塔理论为什么似乎和当下的神经网络认识物体的流程相反？（神经网络认识物体从局部特征到整体特征）

#### 八大原则
```
1 接近原则
```
- 当视觉元素在空间距离上相距<strong>较近</strong>时，人们通常倾向于将它们归为<strong>一组</strong>。
<br><br>

```
2 相似原则
```
- 人们在观察事物的时候，会自然地根据事物的<strong>相似性</strong>进行感知分组。

- 通常依据对<strong>形状、颜色、光照</strong>或其他的<strong>性质的感知</strong>决定分组。
<br><br>

```
3 连续原则
```
- 人们在观察事物的时候会很自然地沿着物体的<strong>边界</strong>，将不连续的物体视为连续的整体。
<br><br>

```
4 闭合原则
```
- 在某些视觉映像中，其中的物体可能是<strong>不完整</strong>的或者<strong>不闭合</strong>的。

- 只要物体的形状足以表征物体物体本身，人们会很容易地感知整个物体而忽视未闭合的特征。
<br><br>

```
5 共势原则
```
- 一组物体具有沿着<strong>相似的</strong>光滑<strong>路径运动</strong>趋势或具有相似的<strong>排列模式</strong>时，将被识别为同一类物体。
<br><br>

```
6 好图原则
```
- 人眼通常会<strong>消除复杂性和不熟悉性</strong>来理解被识别的物体。
<br><br>

```
7 对称原则
```
- 人的意识倾向于将物体识别为沿某点或某轴<strong>对称</strong>的形状。
<br><br>

```
8 经验原则
```
- 某些情形下视觉感知与<strong>过去的经验</strong>有关。

- 如果两个物体看上去<strong>距离相近</strong>，或者<strong>时间间隔小</strong>，通常被识别为同一类。


### 视觉通道
#### 组成：
- <strong>标记</strong> - 通常是一些几何图形元素（点、线、面等）；
- <strong>视觉通道</strong> - 则用于控制标记的展现特征，包括标记的位置、大小、形状、方向、色调、饱和度、亮度等。

#### 数据：
- <strong>类别型</strong> - 区分事物（如性别）
- <strong>有序型</strong> - 表示对象间的顺序关系（如衣服尺码）
- <strong>数值型</strong> - 表示对象的定量数值（如商品价格）

#### 视觉通道分类：
- <strong>定性/分类型</strong> - 描述感知对象是什么或在哪里，适合编码分类型数据（如形状、色调、空间位置）
- <strong>定量/定序型</strong> - 描述感知对象某一属性的具体数值，适合编码有序型或数值型数据（如长度、面积、体积、饱和度、亮度）
- <strong>分组型</strong> - 描述多个或多种标记的组合，适合将存在相互联系的分类的数据属性进行分组，表现内在关联性（如位置接近、颜色相似、显式连接、显式包围）

> 如何选择视觉通道？
- <strong>表现力</strong> - 视觉通道的表现力要求视觉通道<strong>准确编码</strong>数据包含的所有信息。也就是说，视觉通道在对数据进行编码的时候，需要尽量<strong>忠于原始数据</strong>
- <strong>有效性</strong> - <strong>表现力更高</strong>的视觉通道，编码<strong>更重要</strong>的数据信息

<center><img width="50%" src="Vis/pics/1.png"/></center>
<center>视觉通道的表现力排序</center>

> 表现力排序的依据？
```
1 精确性
```
描述人类感知系统对于可视化的判断结果和原始数据的吻合程度。

```不同视觉通道在史蒂文斯幂次法则S=I^n中所对应的n值:```

视觉通道   | 亮度 | 响度 | 面积 | 长度 | 灰对比度
-		   |-	  |-	 |-		|-	   |-
幂次	   |0.5   |0.67  |0.7   |1.0   |1.2


```
2 可辨性
```
如何在给定的取值范围内选择合适数目的<strong>不同取值</strong>，

使得人类的感知系统可<strong>以轻易区分</strong>该视觉通道的<strong>两种或多种</strong>取值状态。

```视觉通道的取值范围是有限的，例如直线宽度增大会最终变为对面积的感知。```

```
3 可分离性
```
描述不同视觉通道在被用于表达数据属性的时候，两两之间的<strong>干扰现象</strong>。

如何在给定的取值范围。


```
4 视觉突出
```
在<strong>很短的时间内(200~250毫秒)</strong>，

仅仅依赖感知的低阶视觉即可直接<strong>察觉</strong>某一对象和其他所有对象的<strong>不同</strong>的现象。


> 总结：视觉通道的选择流程

识别数据类型 > 确定想要传递的信息 > 选用合适的标记与视觉通道 > 迭代

<details>
<summary>例</summary>
<center><img width="60%" src="Vis/pics/2.png"/></center>
· ID: 有序型数据， 定量型通道<br>
· 类型：类别型数据，定性型通道<br>
· 款式：类别型数据，分组型通道<br>
· 尺码：有序型数据，定量型通道<br>
· 销量: 数值型数据，定量型通道<br>
· 年增长: 数值型数据，定量型通道<br>
</details>

### 错题记录





## 第三章
### 数据基础

#### 大数据的4个特征
- 数量大
- 更新快
- 多样性
- 准确性

#### 数据的属性

属性在不同学科中的称呼：
```
数学 - 维度
机器学习 - 特征
统计 - 变量
```

属性可分为两类：<strong>类别属性</strong>与<strong>序数属性</strong>

```
1 类别属性
```
也称为<strong>状态</strong>，它类似于“<strong>东西的名称</strong>”。类别属性不能够作为对象之间比较的依据。


```
2 序数属性
```
若属性能够提供对象之间的<strong>比较信息</strong>，就称这种属性为序数属性。（例：大小的比较、重量的比较）

```
序数属性的细分：数值属性
```
如果一个序数属性中的数据在算数<strong>运算</strong>下具有意义，那么这种更细分的类型称为数值属性。

<center><img width="80%" src="Vis/pics/3.png"/></center>
<center>类别属性与数值属性</center>
<br>
<center><img width="60%" src="Vis/pics/4.png"/></center>
<center>数值属性有离散与连续之分</center>

#### 统计方法在数据分析中的意义
- 了解数据总体情况的有力工具
- 分析数据的基础

#### 用于衡量数据中值的统计方法
```
1 均值
```
均值也就是平均数，表示为一组数据中所有数据项之和再除以这组数据的个数。

```
2 中位数
```
以排序后最中间的数据项表示，若出现总数为<strong>偶数</strong>的情况，则以<strong>最中间的两个数的均值</strong>表示。

```*非对称分布数据的均值与中位数存在差异```

类别   | 优点 | 缺点
-	   |-	  |-
均值   |计算简单，快速获得   |不适用于有序属性
中位数 |避免极端值影响，适用有序属性   |计算复杂，需先排序

```
3 方差
```
表达了数据的离散程度。

方差越小，数据越集中;<br>
方差越大，数据越分散。

<center><img width="50%" src="Vis/pics/5.png"/></center>
<center>方差</center>

#### 数据对象之间相似性的度量
```
相异性矩阵
```
```
|0							|
|d(2, 1) 0					|
|d(3, 1) d(3, 2) 0			|
|...	 ...		  		|
|d(n,1)  d(n, 2) ... ... 0	|
```

```
失配比
```
两个数的失配比就是它们中<strong>值不相等的属性个数占总属性个数</strong>的比例。

```d(i,j)=(p-m)/p```

例：
<center><img width="70%" src="Vis/pics/6.png"/></center>
<center>失配比</center>

```
Jaccard相似系数
```
Jaccard相似系数（Jaccard similarity coefficient）用于比较有限样本集之间的相似性与差异性。Jaccard系数值越大，样本相似度越高。

<center><img width="60%" src="Vis/pics/7.png"/></center>

<center><img width="70%" src="Vis/pics/8.png"/></center>

与杰卡德相似系数相反的概念是杰卡德距离(Jaccard distance)：
- P：样本A与B都是1的维度的个数
- q：样本A是1，样本B是0的维度的个数
- r：样本A是0，样本B是1的维度的个数
- s：样本A与B都是0的维度的个数

那么样本A与B的杰卡德距离可以表示为：
```J = p/(p+q+r)```

#### 数据对象之间距离的度量
```
欧拉距离
```
两点间的直线距离公式
<center><img width="50%" src="Vis/pics/9.png"/></center>
<center>欧拉距离</center>

```
曼哈顿距离
```
<center><img width="50%" src="Vis/pics/10.png"/></center>
<center><img width="30%" src="Vis/pics/11.png"/></center>
<center>曼哈顿距离（投影距离之和）</center>

```
闵可夫斯基距离
```
<center><img width="90%" src="Vis/pics/12.png"/></center>
<center>闵可夫斯基距离可统一表示以上两种距离</center>

### 数据分析与探索

```
四大范式
```
- 第一范式: 几千年前记录和描述自然现象的经验科学;
- 第二范式: 数百年前利用模型归纳总结过去记录的现象的理论科学;
- 第三范式: 利用科学计算机对复杂现象进行模拟仿真的计算科学;
- 第四范式: 计算机将模拟仿真,进行分析总结，得到理论，即数据密集型科学。(2007年)

```
什么是数据科学？（2010）
```
- 获取与预处理数据 
- 存储与分析数据
- 呈现与解释数据

```
利用数据的能力
```
- 理解数据
- 处理数据
- 提取价值
- 可视化数据
- 交流数据

```
确保数据的质量
```
- 准确性 - 数据的值是否正确
- 完整性 - 有没有遗漏、空数据
- 一致性 - 数据的单位是否一致
- 时效性 - 数据是否及时更新
- 可信性 - 数据是否真实可信
- 可解释性 - 数据是否有语义上的解释

```
常见数据质量问题
```
- 由于机器记录错误、人为失误录入等
- 现实中的数据很可能是"脏的”!
- 因此需要审视数据的质量、清洗处理问题数据

<center><img width="90%" src="Vis/pics/13.png"/></center>
<center>重复ID</center>

```
数据清洗
```
- 如何发现潜在的数据质量问题?
- 如何发现未知的错误?

例：
矩阵视图 > 排序 > 呈现缺失问题
<center><img width="60%" src="Vis/pics/14.png"/></center>
<center>矩阵视图</center>
<center><img width="60%" src="Vis/pics/15.png"/></center>
<center>对上图按行列排序后可发现数据缺失</center>

### 可视化+
#### 可视化数据分析过程
采集数据 > 总结规律 > 形成结论

#### 统计分析
- 预处理的有效工具
- 提高了识别复杂数据特征的能力

#### 探索式数据分析 & 传统数据分析
<br>
<center><img width="80%" src="Vis/pics/16.png"/></center>

#### 探索式数据分析中的可视化方法
- 原始数据可视化
- 统计结果可视化
- 多协同视图

```
数据轨迹
```
是一种<strong>单变量数据</strong>呈现方法，通过将自变量与因变量在图中用点呈现出来。

数据轨迹可以直观地展现数据<strong>分布、走势</strong>以及<strong>离群异常点</strong>。

<center><img width="60%" src="Vis/pics/17.png"/></center>
<center>电影公司评分的例子</center>

```
柱状图
```
用长方形的<strong>形状与颜色</strong>编码数据的属性。

常见:柱子的<strong>高度</strong>表示属性值的大小。

作用:揭示数据的<strong>趋势与分布</strong>。

```
饼状图
```
用<strong>环状</strong>方式呈现各分量在整体之中的<strong>比例</strong>。

作用:<strong>快速且直观</strong>地传达数据中的比例信息。

```
直方图
```
是对数据集的某个数据属性的频率统计。
- 每个区间的数据之和为数据集整体
- 不同的数据分布在直方图下有不同的效果

<center><img width="80%" src="Vis/pics/18.png"/></center>
<center>直方图例</center>

```
等高线图
```
将相等数值所在的位置用曲线连接起来所形成的图形。
- 反映数据的连续变化与分布情况

```
走势图
```
简单的数据变化趋势，通常以折线图为基础。

```
散点图
```
<center><img width="60%" src="Vis/pics/20.png"/></center>
<center>散点图矩阵</center>
<center><img width="60%" src="Vis/pics/19.png"/></center>
<center>散点图矩阵的构成</center>

```
热力图
```
有3个维度的数据，利用颜色属性，将第三个维度的数值映射为颜色值，此时就成了热力图。

作用:展示三维数据点的分布情况。

```
箱线图
```
箱形图（Box-plot）又称为盒须图、盒式图或箱线图，是一种用作显示一组数据分散情况资料的统计图。因形状如箱子而得名。在各种领域也经常被使用，常见于品质管理。它主要用于反映原始数据分布的特征，还可以进行多组数据分布特征的比较。
<center><img width="60%" src="Vis/pics/21.png"/></center>
<center>箱线图</center>

```
多协同视图
```
将多个视图结合起来，每个视图展现数据某个方面的属性，并允许用户进行交互分析。

```
数据挖掘
```
是从大型数据库、网络上或其他大型储存库中，自动地发现和提取模式、特征或知识。
<center><img width="60%" src="Vis/pics/22.png"/></center>

!> 百度搜索得到的信息不属于数据挖掘的范畴，数据挖掘指得到非常规的或以前未知的数据。

#### 数据挖掘任务
<center><img width="60%" src="Vis/pics/23.png"/></center>

```
数据挖掘的方法
```
- 统计方法
➢回归分析
➢参数估计

- 机器学习
➢决策树
➢神经网络

- 传统算法
➢K均值算法
➢K临近算法



```
描述型任务
```
- 概念描述 - 直接描述数据特征

- 关联分析 - 数据集中关联性或相关性

- 聚类 - 将数据分簇，簇内数据相似，簇间数据不同

- 异常分析 - 分析异常数据

```
预测型任务
```
- 分类 - 寻找一个模型或算法
- 演化分析 - 针对数据的时空特性

### 错题记录




## 第四章
### 可视化基本流程初探
用图形化的手段处理数据并发现数据中潜在的模式

#### 可视化的作用
- 从数据中探索新的假设证实相关假设与数据是否吻合
- 帮助专家向公众展示数据中的信息

#### 什么是可视分析
结合可视化和数据挖掘的分析模式，以视觉感知为基本通道，通过可视化和交互界面，将人的知识或经验融入到数据分析和推理决策过程中，以迭代求精的方式将数据复杂度降低到人类和计算机可以处理的范围，获取有效知识。


### 数据可视化的框架
#### 如何、为何、用何实现可视化数据分析

以数据流向为主线，包括数据采集、数据处理和变换、可视化映射和用户感知。

<center><img width="80%" src="Vis/pics/24.png"/></center>

#### 可视化交互
可视化过程中，用户控制修改数据采集、数据处理和变换、可视化映射各模块而产生新的可视化结果，并反馈给用户。

#### 数据采集
传感器采样、调查记录、模拟计算等方式采集直接决定了数据的格式、维度、尺寸、分辨率和精确度等重要性质，并在很大程度上决定了可视化结果的质量。

#### 数据的处理和变换
- 原始数据不可避免的含有噪音和误差因此需要前期处理（数据清洗）
- 数据模式和特征往往是隐藏的（特征提取）

#### 可视化映射（核心）

<center><img width="80%" src="Vis/pics/25.png"/></center>

#### 用户感知
从数据可视化结果中提取信息、知识和灵感

<center><img width="80%" src="Vis/pics/26.png"/></center>

<center><img width="80%" src="Vis/pics/27.png"/></center>

#### Tamaro Munzner 框架

<center><img width="40%" src="Vis/pics/28.png"/></center>

```
1 领域，目标用户是谁
```

```
2 问题抽象，将特定领域问题转换为用可视化的语言描述的问题
```
- What要展示什么数据? 数据抽象
- Why为什么用户看这些? 任务抽象

```
3 可视化形式，How如何呈现?
```
视觉编码形式: 如何画图
用户交互形式: 如何操作

```
4 算法.高效率的计算(来最终得到可视化)
```

例：
<center><img width="90%" src="Vis/pics/29.png"/></center>

> Why people are using vis?
<center><img width="90%" src="Vis/pics/30.png"/></center>
<center><img width="50%" src="Vis/pics/31.png"/></center>
<center><img width="60%" src="Vis/pics/32.png"/></center>
<center><img width="90%" src="Vis/pics/33.png"/></center>

> How to design vis idiom?

编码数据、操作视图、多方面呈现和减少被可视化的数据

<center><img width="90%" src="Vis/pics/34.png"/></center>


### 数据处理与变换1
标准化、平滑化和采样

```
数据归一化
```
- 数据的归一化是将数据按比例缩放，使之落入一个小的特定范围。
- 其中最典型的是数据统一映射到[0,1]区间上。

#### 数据归一化
线性变换、反正切变换

<center><img width="50%" src="Vis/pics/35.png"/></center>

#### 数据标准化
把值全都映射到标准正态分布上进行数据的处理和变换


```
数据平滑化
```
#### 曲线拟合（数据平滑化）
- 发现数据的趋势
- 分析变量之间的关系
- 将数据转化成平滑连续的曲线
- 将注意力从"微小的细节”中转移到”更高层面的趋势观察和判断

常用曲线: 模拟一次方程曲线、模拟指数函数曲线、模拟多项式曲线、自定义方程曲线

基本思想：选用适当的曲线，表达并观测”趋势"，劫富济贫


```
数据采样
```
#### 使用数据采样的原因
- 获取或处理全部数据集代价太高，时间开销无法接受。
- 选出具备原始数据特征的数据。


### 数据处理与变换2
分箱、数据降维和数据聚类

```
分箱
```
将一些连续值分组装进些"小箱子”的方法。

```
数据降维
```
- 把数据从多维的空间投影到二维或者三维的空间
- 对降维后的数据运用简单的可视化手段

#### 数据降维方法
##### 线性方法:
主成分分析(Principal component analysis, PCA)<br>
多维尺度分析(Multidimensional scaling, MDS)

##### 非线性方法:
t分布随即近邻嵌入(t-Distributed Stochastic Neighbor Embedding, t-SNE)<br>
自组织映射(Self-organizing map, SOM)<br>
等距特征映射(lsometric Feature Mapping, ISOMAP)

```
数据聚类
```
#### k-means
给数据一些参考点归为不同的类，计算均值，然后把均值所在的点，作为归类的参考点再重新归类

#### 数据聚类方法
K均值(K-means)<br>
高斯混合模型(Gaussian Mixture Model)<br>
DBSCAN算法(Density-Based Spatial Clustering of Applications with Noise)<br>
层次聚类(Hierarchical clustering)<br>
谱聚类(Spectral clustering)


### 错题记录




## 第五章
### 可视化编码
```
标记与视觉通道
```
#### 标记和视觉通道的定义
##### 标记
是图像中的基本图形元素，即原始的几何元素。（点、线、面）

##### 视觉通道
主要用来控制标记的外观，与几何元素的维度无关。（形状、体积、运动）

标记确定了可视化的<strong>形式</strong>，而视觉通道则是确定了可视化的<strong>外观样式</strong>。

<center><img width="50%" src="Vis/pics/36.png"/></center>

#### 标记和视觉通道的应用

<center><img width="60%" src="Vis/pics/37.png"/></center>
<center><img width="80%" src="Vis/pics/38.png"/></center>

#### 视觉通道的类型

<center><img width="60%" src="Vis/pics/39.png"/></center>
<center><img width="45%" src="Vis/pics/40.png"/></center>

```*不同视觉通道有不同的表现力和有效性。```

<center><img width="60%" src="Vis/pics/41.png"/></center>

#### 表现力判断标准
```
1 精确性
```
描述了人们从可视化中获取的信息结果和原始数据的吻合程度。

```
2 可辨认性
```
描述的是如何在给定的取值范围内，选择合适数目的不同取值，使得人们能够轻易地区分这些不同的数值。

```
3 可分离性
```
主要描述的是在表达数据的时候，不同视觉通道之间的干扰问题。

```
4 视觉突出
```
指的是人们可以依靠本能的感知能力，在很短时间内发掘和其他所有对象都不相同的对象。


### 可视化图表
#### 原始数据绘图
- 折线图 - 使用直线段来连接一系列数据点
- 走势图 - 本质上可以看作是缩小版的折线图（可以嵌入文本中）
- 柱状图 - 使用矩形的柱子的高低来展示数值型数据的数值，而矩形的高度和长度都是正比于数据的数值的 ```*不要使用三维柱状图，容易错读```
- 堆叠柱状图 - 主要用于分解整体，并用于比较局部
- 饼图 - 直观展现百分比
- 散点图 - 使用二维坐标系来表示一维数据，每个点即一个数据，点对应的坐标值，就是其坐标轴对应的数据属性的值。

#### 多视图协调关联
多协同视图将不同种类的图表组合起来。每个图表单元既可以单独呈现数据某个方面的属性，也可以一起关联呈现某种特定的数据信息。


### 可视化设计三部曲
#### 可展示数据筛选
是确定在有限的可视化空间中选择适当数量的信息进行视觉编码。

#### 可视化编码映射
针对某一数据，要选择合适的可视化编码映射，本质上就是选择合适的<strong>标记</strong>和<strong>视觉通道</strong>。

<center><img width="60%" src="Vis/pics/42.png"/></center>

```*实际应用中往往需要对多种视觉通道进行组合```

#### 视图与交互设计
```
滚动和缩放
```
当数据无法在当前有限的分辨率和显示空间下完整展示时，需要进行滚动和缩放来查看更多更详细的数据信息。

```
颜色映射
```
例如可视化系统中的调色盘。

```
数据映射
```
<center><img width="60%" src="Vis/pics/43.png"/></center>
<center>同一数据的两种可视化方法</center>

```
细节层次控制
```
有助于在不同的条件下，隐藏或者突出数据的细节部分。

### 可视化设计进阶
#### 考虑因素
- 选择合理的标注和说明
- 合理的配色（正确使用颜色编码）```配色工具：Color brewer```

> 如何提高可视化的表现力和有效性？
- 聚焦: 通过适当的技术手段将用户的注意力集中到可视化结果中的最重要的区域。
- 均衡: 有效利用空间，重要元素位于中心区域，所有元素均衡分布。
- 简单: 避免过多元素，避免过于复杂。


#### 隐喻技术
用人们<strong>熟悉的某样事物</strong>去表达信息，从而使得可视化内容更加<strong>直观、易懂</strong>。

#### 相关案例

<center><img width="60%" src="Vis/pics/44.png"/></center>
<center>隐喻：主题河流</center>

### 错题记录








## 第六章
### 空间场数据可视化概述
#### 如何绘制图像?
- 对空间场数据的可视化
- 根据数据类型和分析任务确定
- 标量场可视化方法以及矢量场、张量场的可视化方法

#### 空间场数据
- 对连续的空间进行度量(现实世界/软件模拟)
- 与空间、时间、地理位置有关
- 根据空间的维度与属性值的特征共同命名

- 多元结构 → 属性值
- 多维结构 → 空间维度
- 数据处理注意点 → 采样频率及所带来的相关数学问题

<center><img width="60%" src="Vis/pics/45.png"/></center>

#### 表格型数据
存储离散的对象，仅代表空间中特定点的值。

#### 风格化的绘制
- 展现医疗影像数据、蛋白质合成示意图等
- 洋流数据可视化
- NASA卫星观测到的日冕爆发

#### 其他研究方向
- 表达数据采集或者模拟生成中的不确定性;
- 通过风格化绘制生成更加具有艺术美感的结果或类似教科书上示意图的图像;
- 在三维场可视化结果或者虚拟现实环境中进行交互;
- 并行计算、空间索引等加速算法。
- 空间场数据可视化在医疗、气象、流体力学、计算机模拟等多个科学领域有着广泛的应用。


### 标量场数据可视化（上）
不同类型的空间场数据的可视化方法，包括了一维、二维和三维的标量场数据以及矢量场和张量场数据。

#### 一维标量场数据
沿空间某一路径采集的数据（如：对土层钻探时到得的地质信息）

通常用折线图表现

#### 二维标量场数据
分为平面型、曲面型，如：
- 医学诊断的X-光片
- 实测的地球表面温度
- 遥感观测的卫星影像

复杂的曲面通常基于三维空间可视化<br>
相对简单的曲面通常基于二维平面可视化（进行投影）

- 等值线提取:
医学影像中的组织边界、大气数值数据中低压区的边缘
常用移动四边形法生成等值线

<center><img width="60%" src="Vis/pics/46.png"/></center>
<center>一共16种情况</center>

<center><img width="60%" src="Vis/pics/47.png"/></center>
<center>然后进行插值</center>

### 标量场数据可视化（下）
#### 三维场数据
- 记录三维空间中的物理属性及其演化规律
- 获取的方式为：
测量、计算机模拟
- 常见三维场数据：
医学断层扫描（CT）、气象观测数据

#### 三维场数据绘制方法
- 三维等值面提取
<center><img width="60%" src="Vis/pics/48.png"/></center>
<center>三维等值面可视化中的移动立方体算法</center>

- 直接体绘制<br>
对三维数据场进行变换和着色，进而在屏幕上生成二维图像
<center><img width="60%" src="Vis/pics/49.png"/></center>

- 光线投射法
<center><img width="40%" src="Vis/pics/50.png"/></center>

- 体数据分类<br>
将数据中的标量值转换为颜色通过调节和应用传输函数实现<br>
传输函数定义如何将数据值映射为光学属性
<center><img width="15%" src="Vis/pics/51.png"/><img width="30%" src="Vis/pics/52.png"/></center>

<center><img width="60%" src="Vis/pics/53.png"/></center>
<center>调节传输函数</center>

<center><img width="60%" src="Vis/pics/54.png"/></center>
<center>突出特征</center>

- 光学模型
#### 吸收光和发射光
只考虑光的直线传播，通过修改光学积分进行
#### 散射光、多次散射光、阴影等
需考虑光在不同方向的传播，光学属性是多个光学积分之和。

- 交互方式<br>
三维影像交互方式如旋转，平移，放缩等<br>
通过调节传输函数来调节显示、消除遮挡


### 矢量场和张量场数据可视化
> 矢量场与标量场的区别
空间中的任意位置都对应一一个失量而非标量。

#### 流场数据
每一个点的矢量的方向都代表流体在这个位置的流向，矢量的大小代表流速。

#### 标记法
用方向的标记编码不同位置上的失量的方向和大小。

```局限性:```
可显示空间的尺寸会限制标记的数量，限制了可视化的精度。<br>
离散排布的标记缺乏对场数据连续性的直观表达。

#### 积分曲线法
- 流线 - 静态场生成的积分曲线
- 迹线 - 动态场中产生的积分曲线
- 脉线 - 从同一个点不断发射新的粒子

#### 纹理法
<center><img width="60%" src="Vis/pics/55.png"/></center>
<center>线积分卷积 - 可视化效果逼真、信息密度大</center>

#### 张量
常用于表示物理性质的各向异性。

如:
- 固体力学和土木工程中，张量用来表示应力、惯性、渗透性和扩散。
- 医学图像领域，张量场是弥散张量成像的理论基础。

#### 指数法
将每一个张量转化为一个标量，运用标量的可视化方法进行展示。

#### 标记法
类似二维场数据中使用的标记法，只是使用的标记更加复杂，通常用一些的图形来表达张量。

#### 弥散张量中的主特征向量
- 指向生物组织中水分子扩散最快的方向
- 与纤维状组织如脑白质或肌肉纤维组织的方向重合
- 因此可以用来重现生物组织的结构

<center><img width="60%" src="Vis/pics/56.png"/></center>

<center><img width="60%" src="Vis/pics/57.png"/></center>
<center>纤维束聚类</center>

#### 混合绘制
难点:正确显示不同类型绘制对象间的层次关系和透明颜色的叠加

### 错题记录







## 第七章
### 灵活多变的地图
#### 地理空间数据
如: 一个餐厅的地理位置和评分

- 描述的是对象在空间中的位置和属性
- 真实的人类生活空间
- 由移动设备和传感器产生

```
等角度地图投影
```
墨卡托投影 (正轴等角圆柱投影)

<center><img width="60%" src="Vis/pics/58.png"/></center>
<center>等角度投影</center>

<strong>缺点：</strong>面积变形明显

```
等面积投影
```
亚尔勃斯投影

<center><img width="60%" src="Vis/pics/59.png"/></center>
<center>等面积投影</center>

<center><img width="40%" src="Vis/pics/60.png"/></center>
<center>投影结果</center>

解决了等角度地图投影的面积变形，被广泛应用于着重表现面积的国家或地区等

```
等距离投影
```
方位角投影

<center><img width="60%" src="Vis/pics/61.png"/></center>
<center><img width="40%" src="Vis/pics/62.png"/></center>

被广泛应用于导航地图，联合国国徽也应用了等距离投影

> 如何展示对象的属性信息?
<center><img width="80%" src="Vis/pics/63.png"/></center>
<center>地图常用可视化变量</center>

<center><img width="80%" src="Vis/pics/64.png"/></center>
<center>选择合适的可视化变量</center>


### 地图上的点与线
#### 点
- 经纬度坐标和对象的名称，类别组成
- 地理数据可视化中最基础的数据类型

#### 点数据的可视化
- 直接绘制
- 点标记
- 图标标记

#### 图标或符号可视化原则
- 符号必须直观且符合常识 
- 符号的数量和种类不宜过多

```
点数据可视化编码
```
<center><img width="60%" src="Vis/pics/65.png"/></center>
<center><img width="60%" src="Vis/pics/66.png"/></center>

```
聚合方法
```
<center><img width="60%" src="Vis/pics/67.png"/></center>

```
采样方法
```
- 模拟原数据分布的低密度数据
- 减轻视图的负担和数据的交叠

<center><img width="60%" src="Vis/pics/68.png"/></center>

#### 线数据的可视化
连接两个或更多地点的线段或者路径

<center><img width="60%" src="Vis/pics/69.png"/></center>

```
边绑定
```
<center><img width="60%" src="Vis/pics/70.png"/></center>

```
采样方法
```
<center><img width="60%" src="Vis/pics/71.png"/></center>

```
信息说明
```
<center><img width="60%" src="Vis/pics/72.png"/></center>


### 区域数据可视化
- 简单理解为地图上的一个区域
- 有长度，有宽度
- 是由一系列的点围成的一个封闭的二维空间

可采用连线和集合等方法展现区域属性之间的多元关系。

```
等值线图
```
- 绘制等值线
- 标注数值大小
<center><img width="60%" src="Vis/pics/73.png"/></center>

```
Choropleth Map(分级统计图)
```
- 包括统计值的区域数据
- 用颜色代表数值
<center><img width="60%" src="Vis/pics/74.png"/></center>

<strong>不足</strong>
- 假设数据平均分布
- 视觉误导

<center><img width="60%" src="Vis/pics/75.png"/></center>

```
比较统计图
```
<center><img width="60%" src="Vis/pics/76.png"/></center>
<center><img width="90%" src="Vis/pics/77.png"/></center>

```
规则形状地图
```
<center><img width="90%" src="Vis/pics/78.png"/></center>

```
气泡集合
```
隐式曲线对每一组集合聚类生成一个连续光滑的闭包;

<center><img width="50%" src="Vis/pics/79.png"/></center>

```
线集合地图
```

<center><img width="50%" src="Vis/pics/80.png"/></center>

```
视觉编码
```
<center><img width="60%" src="Vis/pics/81.png"/></center>

```
折线图、点图
```
<center><img width="60%" src="Vis/pics/82.png"/></center>

### 地理可视化应用
<center><img width="60%" src="Vis/pics/83.png"/></center>

```
三维绘制
```
- 常配有交互操作
- 允许图像进行旋转和缩放

<center><img width="60%" src="Vis/pics/84.png"/></center>

```
城市数据的可视化的挑战
```
- 数据量大，多源异构
- 需满足多样的分析任务
- 需表达让用户更容易发现数据特征的数据

<center><img width="60%" src="Vis/pics/85.png"/></center>
<center><img width="60%" src="Vis/pics/86.png"/></center>
<center><img width="60%" src="Vis/pics/87.png"/></center>

```
多个数据源数据融合、推理系统
```
应用:
- 出租车轨迹数据
- 手机轨迹信息数据
- 微博数据等多个数据源的数据

特点:
- 数据维度不一
- 属性各异

处理方法:<br>
系统针对每一种数据源都设计了高效的数据存储和计算方法，并建立了各个数据对象在时空上的关联。

```
城市数据的可视化
```
- 帮助人们更好的理解大数据
- 优化人们的生活

<center><img width="60%" src="Vis/pics/88.png"/></center>
<center><img width="70%" src="Vis/pics/89.png"/></center>
<center><img width="70%" src="Vis/pics/90.png"/></center>


### 错题记录





## 第八章
### 时间属性的可视化
#### 时变数据
随着时间变化的、带有时间属性的数据。

#### 时变数据的分类
<center><img width="70%" src="Vis/pics/91.png"/></center>

#### 时间序列数据
生物DNA测序

#### 特点
- 量大
- 维数多
- 变量多
- 类型丰富
- 分布范围广泛

> 时变型数据可视化设计的三个维度
<center><img width="70%" src="Vis/pics/92.png"/></center>

```
表达维度
```
#### 线性
- 以典型的阅读方式呈现内容
- 将时间数据作为二维的线图显示
- x轴表示时间，y轴表示其他的变量

<center><img width="60%" src="Vis/pics/93.png"/></center>

#### 径向
- 将时间序列编码为弧形
- 沿圆周排列
- 合适呈现周期性的时变型数据

<center><img width="70%" src="Vis/pics/94.png"/></center>
<center><img width="70%" src="Vis/pics/95.png"/></center>

#### 网格
- 和日历相对应
- 一般采用表格映射的方式

<center><img width="70%" src="Vis/pics/96.png"/></center>
<center><img width="70%" src="Vis/pics/97.png"/></center>
<center><img width="70%" src="Vis/pics/98.png"/></center>

#### 随机
<center><img width="70%" src="Vis/pics/99.png"/></center>
<center><img width="70%" src="Vis/pics/100.png"/></center>

```
比例维度
```
比例维度<strong>(按时间顺序)</strong>可以被用来表示<strong>事件之间的距离，事件的持续时间</strong>。

<center><img width="70%" src="Vis/pics/101.png"/></center>

#### 相对顺序
相对顺序是指存在一个基线事件在时间零点，可以被用在<strong>多时间线</strong>的对比。
<center><img width="70%" src="Vis/pics/102.png"/></center>

#### 对数
对数的比例从按时间的前后顺序排列的比例转换而来，强调了最早的或最近的事件，对数比例适用于长范围或不均匀的事件布局。
<center><img width="70%" src="Vis/pics/103.png"/></center>

#### 次序
次序，按次序的比例中连续事件之间的距离是相等的，只表达事件的顺序。
<center><img width="70%" src="Vis/pics/104.png"/></center>

#### 次序+中间时长
次序+中间时长，这种形式可以用来表达长时间和不均匀分布的事件。
<center><img width="70%" src="Vis/pics/105.png"/></center>

```
布局维度
```
#### 单一时间线
<center><img width="70%" src="Vis/pics/106.png"/></center>

#### 多个时间线
<center><img width="70%" src="Vis/pics/107.png"/></center>

#### 分段时间线
在这种形式中，一个时间线被有意义的进行划分，进行另一种形式的比较。
<center><img width="70%" src="Vis/pics/108.png"/></center>

#### 多个时间线加上分段时间线
指不同属性时间线加上分割的时间段，可以进行多种形式的比较。


### 多变量时变型数据可视化
- 数据本身的属性
- 数据集的顺序性
- 数据分析的方法
- 展现、挖掘数据中的规律

> 多变量时变型数据可视化的步骤
- 第一步，数据抽象，包括数据降维、特征选取和数据简化
- 第二步，数据聚类，核心在于定义恰当的距离或相似性度量
- 第三步，特征分析，包括特征抽取、语义分析等操作

```
基于线表示
```
高维抽象的时变非空间数据的可视化
- 第一步:进行高维曲线采样，采样的频率由用户交互指定。
- 第二步:将采样后的高维曲线分段,便于刻画每段曲线的特性,小段之间可以重叠。分段尺寸、重叠程度也由用户交互指定。
- 第三步:用降维方法将高维曲线投影到二维空间，显示和研究曲线的特性。

<center><img width="30%" src="Vis/pics/109.png"/></center>
<center>心电图可视化</center>


```
基于图结构
```
基于事件的时变型数据可视化

核心:事件演化的组织

- 第一步，用户根据领域需求和任务描述，从数据中找到与用户
关注点实际相匹配的事件;
- 第二步，对事件分类，根据事件不同类型的特征描述，从输入
的数据中检测事件，得到事件实例;
- 第三步，通过可视化方法将检测到的事件整合到可视表达中。

<center><img width="70%" src="Vis/pics/110.png"/></center>

时变型数据可视化常用的一种交互手段是从时变型数据中<strong>查询特定的时间序列，以便交互地发现特征和趋势</strong>。

#### 交互
- 表现重要的区域

#### 方法
- 概览加上下文
- 层次细节

#### TimeSearcher
- 直接指定时变趋势模式
- 操纵时变型数据集
- 基于实例查询给定的时变趋势模式

<center><img width="70%" src="Vis/pics/111.png"/></center>
<center><img width="70%" src="Vis/pics/112.png"/></center>


### 流数据可视化
流数据的输入数据并不存储在可随机访问的磁盘或内存中，而是以一个或多个"连续数据流”的形式到达。

#### 常见的流数据
- 移动通信日志
- 网络数据(日志、传输数据包、警报等)
- 高性能集群平台日志
- 传感器网络记录
- 金融数据(如股票市场)
- 社交数据等

#### 流数据的特点.
- 第一，数据流的潜在大小也许是无限的;
- 第二，数据元素在线到达，需要实时处理;
- 第三，无法控制数据元素的到达顺序和数量;
- 第四，某个元素被处理后，要么被丢弃,要么被归档存储;
- 第五，对于流数据的查询异常情况和相似类型比较耗时，人工检测日志相当乏味且易出错。

#### 流数据可视化模型及技术
<center><img width="90%" src="Vis/pics/113.png"/></center>

#### 用户的交互
- 对输出内容的可视检索
- 对可视布局的基本交互
- 自定义的数据定制

#### 多数据库的设计
- 保护了原始数据
- 提高了数据存取的效率

#### 系统日志监控流数据可视化
流数据可视化按功能可以分两种可视化类型:
- 监控型: 用滑动窗口固定一个时间区间，把流数据转化为静态数据，数据更新方式可以是刷新，属于局部分析;
- 叠加型或者是历史型: 把新产生的数据可视映射到原来的历史数据可视化结果上，更新方式是渐进式更新，属于全局分析。

#### 系统日志监控流数据可视化
系统日志数据反映了一机器、一个计算集群的系统性能，是商业智能中最重要的数据。

##### 工业应用
- Splunk、Loggy、Flume等
<br>
LogTool是一个可视化用户浏览行为的工具。它通过分析数据包的不同IP地址和端口，判断用户正在使用的网络程序或者服务。
<center><img width="80%" src="Vis/pics/114.png"/></center>

#### 文本流数据可视化
文本数据从事件角度对文本进行可视分析，挖掘事件的发生、发展及变化。
<br>
EventRiver首先使用增量式聚类算法从一系列事件中提取热门话题，然后用河流的隐喻将事件的语义和上下文在一个 布局界面中自然地表达出来。
<center><img width="80%" src="Vis/pics/115.png"/></center>

### 错题记录