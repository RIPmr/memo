# Computer Graphics Note

《Real-time Rendering 4th Edition》读书笔记

## Chapter 1 - Introduction - 概述
> Real-time rendering is concerned with rapidly making images on the computer. <br>It is the most highly interactive area of computer graphics. 

### 什么是实时渲染
<strong>实时渲染（Real-time rendering）</strong>指的是在计算机上快速生成图像。它是计算机图形学中最具交互性的领域。首先一幅图像显示在屏幕上，然后观察者做出动作与反应，并且其动作反馈会影响接下来的生成内容。由于这种反馈、渲染的循环速度足够快，观察者就不会只看到独立的图像，而是会沉浸在这种动态过程中。

### 符号和定义 (Notation and Definitions)
<br>
<center><img width="70%" src="CG/RTR/1.png"/></center>
<center>书中使用的数学符号总结</center>

<br>
<center><img width="70%" src="CG/RTR/2.png"/></center>
<center>一些数学运算符的符号</center>

其中运算符8和9是限制（clamping）运算符，通常用于着色计算中。运算符8将负值限制为0：
<center><img width="24%" src="CG/RTR/3.png"/></center>

运算符9将值限制在0和1之间：
<center><img width="26%" src="CG/RTR/4.png"/></center>

第11个运算符，即二项式因子：
<center><img width="20%" src="CG/RTR/5.png"/></center>

<br>
<center><img width="70%" src="CG/RTR/6.png"/></center>
<center>一些特殊数学函数的符号</center>


## Chapter 2 - The Graphics Rendering Pipeline - 图形绘制流水线
> 实时渲染的核心是一系列变换步骤，这些步骤将场景的数学描述转换成我们能看到的东西（图像信息）

### 渲染管线
渲染管线的基本构造包括四个阶段：
- 应用程序阶段（application）
- 几何处理阶段（geometry processing）
- 光栅化阶段（rasterization）
- 像素处理阶段（pixel processing）

这些阶段中的每个阶段本身也可以是管线化或并行化的：
<br>
<center><img width="90%" src="CG/RTR/7.png"/></center>
<center>渲染管线的基本构造</center>

### 应用程序阶段（application）
应用程序阶段（application）由应用程序驱动，因此通常由在通用 CPU 上运行的软件实现。这些 CPU 通常包括多个内核，这些内核能够并行处理多个线程。这使 CPU 可以有效地运行应用程序阶段负责的各种任务。传统上通常在 CPU 执行包括碰撞检测、全局加速算法、动画、物理模拟还有许多其他任务，任务具体取决于应用程序的类型。

在应用程序阶段结束时，要渲染的几何图形被移交到几何处理阶段。因为此阶段是基于软件的实现，所以它不像几何处理阶段、光栅化阶段和像素处理阶段那样能够划分为多个子阶段（从而提升处理效率）。但是，为了提高性能表现，应用程序阶段通常会在多个处理器核心上并行执行。在CPU设计中，这被称为超标量构造（superscalar construction），因为它能在同一阶段同时执行多个进程。

### 几何处理阶段（geometry processing）
此阶段会处理变换，投影以及所有其他类型的几何处理。另外，此阶段会计算所需要绘制的内容，并判断应如何绘制以及应在何处绘制。几何处理阶段通常在包含许多可编程内核以及固定操作硬件的图形处理单元（GPU）上执行。
GPU 上的几何处理阶段（Geometry Processing）负责大部分的逐三角形和逐顶点的操作。该阶段进一步分为以下功能阶段（functional stages）：
- 顶点着色（vertex shading）
- 投影（projection）
- 裁剪（clipping）
- 屏幕映射（screen mapping）
<br>
<center><img width="90%" src="CG/RTR/8.png"/></center>
<center>几何处理阶段中的渲染管线</center>

### 光栅化阶段（rasterization）
此阶段通常会依次将三个顶点输入，形成三角形，然后找到该三角形内所有需要计算的像素，将它们发送到下一个阶段。我们称这种过程为光栅化，它被分为两个功能子阶段：三角形设置（triangle setup，也称为基本装配）和三角形遍历（triangle traversal）：
<center><img width="70%" src="CG/RTR/9.png"/></center>
<center>光栅化的两个阶段</center>

#### 三角形设置（triangle setup，也称为基本装配）
在这一阶段，计算了三角形的微分、边缘方程和其他数据。 这些数据可用于三角形遍历以及几何阶段产生的各种着色数据的插值。

#### 三角形遍历（triangle traversal）
这个阶段将检查每个像素（或样本）中心被三角形覆盖的情况，并为与三角形重叠的像素部分生成一个片元（fragment）。

### 像素处理阶段（pixel processing）
在此阶段，经过之前所有阶段的处理，已经找到了在三角形或其他图元内部应考虑的所有像素，于是此阶段为每个像素执行一段程序以确定其颜色，并可以进行深度测试，以判断该像素是否可见。它还可以对每个像素进行其他操作，例如将新计算的颜色与之前的颜色混合。光栅化和像素处理阶段都是完全在 GPU 上进行处理。


## Chapter 3 - The Graphics Processing Unit - 图形处理单元
> 现代GPU使用固定功能和可编程单元的组合来实现渲染管线(Rendering Pipeline)的各个阶段

专用图形硬件相对于CPU的唯一优势是计算速度，但速度至关重要。GPU通过专注于一组高度可并行化的任务而获得了卓越的速度。在过去的二十年中，图形硬件经历了不可思议的转变。

### 数据并行架构 (Data-Parallel Architectures)
<strong>延迟（latency）</strong>是所有处理器都面临的问题。访问数据需要花费一些时间。考虑延迟长短的一种基本方法是，信息所处位置离处理器越远，等待时间就越长。

不同的处理器体系结构使用各种策略来避免延迟。

一个CPU可以包含多个处理器，但是每个处理器都以串行方式运行代码，为了最大程度地减少延迟，许多CPU芯片都由快速本地缓存组成，这些缓存中填充了下一步可能需要的数据。CPU还通过使用诸如<strong>分支预测（branch prediction），指令重新排序（instruction reordering），寄存器重命名（register renaming）和缓存预取（cache prefetching ）</strong>之类的巧妙技术来避免停顿。

GPU采用不同的方法避免延迟。GPU的大部分芯片区域专用于称为<strong>着色器核心（shader cores）</strong>的大量处理器，通常数量多达数千个。GPU是流处理器，其中依次处理相似数据的有序集合。由于这种相似性（例如，一组顶点或像素），GPU可以大规模并行地处理这些数据。另一个重要的部分是这些调用要尽可能地独立，这样它们就不需要来自相邻调用的信息，并且不共享可写的存储位置。有时我们会打破该规则来实现新的功能，但是代价是潜在的延迟，因为一个处理器可能会等待另一个处理器完成其工作。

GPU针对吞吐量（throughput）进行了优化，吞吐量定义为可以处理数据的最大速率。但是，这种快速处理具有成本，由于专用于高速缓存存储器和控制逻辑的芯片面积较小，因此每个着色器内核的等待时间通常比CPU处理器遇到的等待时间长得多。

假设网格已光栅化，并且我们现在有2000个要处理的片元（fragments），像素着色器程序将被调用2000次。想象现在我们只有一个处理器，这是世界上最弱的GPU。它开始为2000个片元的第一个片元执行着色器程序。着色器处理器对寄存器中的值执行一些算术运算。寄存器是本地的，可以快速访问，因此不会发生停顿。然后，着色器处理器会执行一条指令，例如纹理访问。由于纹理是一个完全独立的资源，而不是像素程序本地内存的一部分，所以内存提取可能需要数百到数千个时钟周期，在此期间GPU处理器不执行任何操作。<strong>此时，着色器处理器将停止运行，等待纹理的颜色值返回。</strong>

为了缓解这种情况，我们为每个片元提供一些用于其本地寄存器的存储空间。现在，允许着色器处理器切换并执行另一个片元，而不是在采样纹理期间停下来。切换的速度非常快，现在执行第二个片元，与第一个相同，执行一些算术函数，然后再次遇到纹理获取。着色器核心现在再次切换到另一个片元，即第三个片元。最终，所有两千个片元都以这种方式处理。此时，着色器处理器将返回片元一，此时纹理颜色已被获取并且可以使用，因此着色器程序可以继续执行。处理器以相同的方式进行处理，直到遇到另一个已知会暂停执行的指令，或者程序完成。与着色器处理器（shader processor）始终专注于一个片元相比，执行单个片元所需的时间更长，但是整个片元的总体执行时间将大大减少。

在这种架构中，通过切换到另一个片元使GPU保持忙碌来隐藏延迟。GPU通过将指令执行逻辑与数据分离开来，使该设计更进一步。称为<strong>单指令多数据（SIMD，single instruction, multiple data）</strong>的这种安排可以在固定数量的着色器程序上以锁定步骤执行同一命令。SIMD的优点是，与使用单独的逻辑和调度单元运行每个程序相比，用于处理数据和交换的硅（和功率）要少得多。将我们的2000片元示例转换为现代GPU术语，每个片元的像素着色器调用都称为线程。这种类型的线程与CPU线程不同。它由用于着色器输入值的一点内存以及着色器执行所需的任何寄存器空间组成。使用相同着色器程序的线程被分为几组，被NVIDIA称为<strong>warp</strong>，被AMD称为<strong>wavefronts</strong>。一个 warp/wavefront 被 计划用于SIMD处理，由8至64之间的任意数量的GPU着色器内核执行。每个线程都映射到SIMD通道。

假设我们有两千个线程要执行。NVIDIA GPU的 warps 包含32个线程。这将产生2000/32 = 62.5个 warps，这意味着分配了63个warps，其中一个 warps 是一半为空。warp 的执行类似于我们的单个GPU处理器示例。着色器程序在所有32个处理器上以固定步骤执行。因为对所有线程执行相同的指令，遇到内存提取时，所有线程都会同时遇到它。提取信号表明线程warp将停止，所有线程都在等待它们的（不同的）结果。此时不会停顿，而是将warp换成32个线程的另一个warp，然后由32个内核执行。这种交换的速度与我们的单处理器系统一样快，因为在将warp换入或换出时，每个线程内的数据都不会被触及。每个线程都有自己的寄存器，每个warp都跟踪其正在执行的指令。交换新线程只是将一组核心指向另一组要执行的线程即可。没有其他开销。warp执行或换出，直到全部完成。

<center><img width="70%" src="CG/RTR/10.png"/></center>
<center>简化的着色器执行示例</center>

与每个线程相关联的着色器程序所需的寄存器越多，则线程中可以驻留的线程越少，因此warp也就越少。warps 不足可能意味着无法通过交换来减轻失速。驻留的 warps 被称为“飞行中”（in flight），这个数字称为占用率（occupancy）。高占用率意味着有许多可用于处理的 warp，因此空闲处理器的可能性较小。占用率低通常会导致性能不佳。

影响整体效率的另一个因素是由“if”语句和循环引起的动态分支。假设在着色器程序中遇到 “if” 语句。如果所有线程求值并采用同一分支，则warp可以继续进行而不必担心其他分支。但是，如果某些线程甚至一个线程采用了替代路径，那么warp必须执行两个分支，从而丢弃每个特定线程不需要的结果。这个问题称为<strong>线程发散（thread divergence）</strong>，其中一些线程可能需要执行循环迭代或执行warp中其他线程不执行的 “if” 路径，从而使它们在此期间处于空闲状态。

### GPU管线概述 (GPU Pipeline Overview)
GPU实现了第2章中描述的概念如几何处理，光栅化和像素处理管线阶段。这些阶段分为几个硬件阶段，这些阶段具有不同程度的可配置性或可编程性。

这些阶段根据用户对其操作的控制程度进行颜色编码。绿色阶段是完全可编程的。虚线表示可选阶段。黄色阶段是可配置的，但不是可编程的，例如，可以为合并阶段设置各种混合模式。蓝色阶段的功能完全固定。

<center><img width="80%" src="CG/RTR/11.png"/></center>
<center>渲染管线的GPU实现</center>

随着时间的流逝，GPU管道已从硬编码操作阶段演变到增加灵活性和控制能力的阶段。可编程着色器阶段的引入是这一发展过程中最重要的一步。

### 可编程着色器阶段 (The Programmable Shader Stage)
现代着色器程序使用统一的着色器设计。这意味着与顶点，像素，几何和曲面细分相关的着色器共享一个公共的编程模型。在内部，它们具有相同的<strong>指令集体系结构（ISA，instruction set architecture）</strong>。实现此模型的处理器在 DirectX 中称为“通用着色器核心”（common-shader core）。

着色器使用类似C的<strong>着色语言（shading languages）</strong>进行编程，例如DirectX的高级着色语言（HLSL，High-Level Shading Language）和OpenGL着色语言（GLSL，OpenGL Shading Language）。DirectX 的 HLSL 可以编译为虚拟机字节码，也称为中间语言（IL或DXIL），以提供硬件独立性。中间表示还可以允许着色器程序被编译和离线存储。驱动程序将此中间语言转换为特定GPU的ISA。

一次 Draw Call 调用图形API来绘制一组图元（primitives），从而使图形管线执行并运行其着色器（shaders）。每个可编程着色器阶段都有<strong>两种类型的输入</strong>：

- <strong>uniform inputs</strong>: 其值在整个绘制调用期间保持不变（但可以在绘制调用之间进行更改）；
- <strong>varying inputs</strong>: 即来自三角形顶点或光栅化的数据。例如，纹理或任何大型数据数组。

基础虚拟机（The underlying virtual machine）为不同类型的输入和输出提供特殊的寄存器。用于uniforms的可用寄存器的数量比用于varying的输入或输出的可用寄存器的数量多得多。

<center><img width="70%" src="CG/RTR/12.png"/></center>
<center>Shader Model 4.0下的统一虚拟机体系结构和寄存器布局</center>

### 流控制（flow control）
术语<strong>“流控制”（flow control）</strong>是指使用分支指令来更改代码执行流。

与流控制相关的指令用于实现高级语言构造，例如“if”和“ case”语句，以及各种类型的循环。着色器支持两种类型的流控制。

<strong>静态流控制（Static flflow control）</strong>分支基于统一输入的值。这意味着代码流在绘图调用中是恒定的。静态流控制的主要好处是允许将相同的着色器用于各种不同的情况（例如，不同数量的灯光）。由于所有调用都采用相同的代码路径，因此没有线程差异。

<strong>动态流控制（Dynamic flflow control）</strong>基于变化的输入的值，这意味着每个片段可以不同地执行代码。这比静态流控制功能强大得多，但会降低性能，尤其是在着色器调用之间代码流发生不规则变化时。

### 顶点着色器 (Vertex Shader)
顶点着色器是处理三角形网格的第一阶段，顶点着色器提供了一种修改、创建或忽略与每个三角形的顶点关联的值的方法，例如其颜色、法线、纹理坐标和位置。通常，顶点着色器程序会将顶点从模型空间转换为<strong>齐次裁剪空间（homogeneous clip space）</strong>。顶点着色器至少必须始终输出此位置。

顶点着色器的输出将发送到像素着色器程序以进行继续处理。在某些GPU上，数据也可以发送到细分阶段或几何着色器，或存储在内存中。

### 曲面细分阶段 (The Tessellation Stage)
细分阶段允许我们渲染曲面，此阶段是可选的GPU功能，该功能首先在DirectX 11中可用，OpenGL4.0 和 OpenGL ES 3.2也支持该功能。

细分阶段由三个部分组成： DirectX中，它们是：外壳着色器（hull shader），细分（tessellator）和域着色器（domain shader）。在OpenGL中，外壳着色器对应曲面细分控制着色器（the tessellation control shader），而域着色器对应曲面细分评估着色器（tessellation evaluation shader）。

hull shader的输入是一个特殊的补丁图元（patch primitive）。它由几个控制点组成，这些控制点定义了细分曲面，例如Bezier曲面或其他类型的曲面元素。hull shader具有两个功能：首先，它告诉细分器应生成多少个三角形以及采用哪种配置。其次，它对每个控制点执行处理。同样，可选地，hull shader可以修改传入的patch数据，根据需要添加或删除控制点。

hull shader将细分因子（tessellation factors, TFs）和类型发送给固定功能细分器。控制点集由外壳着色器根据需要进行转换，并与TF和相关的修补程序常量一起发送到域着色器。曲面细分对象将创建一组顶点及其重心坐标。然后由域着色器对其进行处理，从而生成三角形网格（显示控制点以供参考）。

<center><img width="70%" src="CG/RTR/13.png"/></center>
<center>细分阶段</center>

### 几何着色器 (Geometry Shader)
几何着色器可以将图元转换为其他图元，而这在细分阶段是无法完成的。几何着色器是在2006年底随 DirectX 10 发行版添加到硬件加速的图形管道中的。它位于管道中的细分着色器之后，并且使用与否是可选的。OpenGL 3.2和OpenGL ES 3.2也支持这种类型的着色器。

几何着色器设计用于修改传入的数据或制作有限数量的副本（copies），几何着色器的行为是最不可预测的，因为它是完全可编程的。实际上，几何着色器通常用得很少，因为它无法很好地展现GPU的优势。在某些移动设备上，它是通过软件实现的，因此强烈建议不要使用它。

### 像素着色器 (Pixel Shader)
顶点，曲面细分和几何体着色器执行完操作后，便会裁剪并设置图元以进行光栅化，流水线的这一部分在其处理步骤中是相对固定的，即不是可编程的，但是高度可配置的。在OpenGL中，像素着色器称为片元着色器。

顶点着色器程序的输出实际上是像素着色器程序的输入，通常像素着色器会计算并输出片元的颜色，但它还可能会产生透明度值（opacity value），并可以选择修改z深度。像素着色器还具有丢弃传入片元（即不生成任何输出）的独特功能。

最初，像素着色器只能输出到合并阶段，以进行最终显示。随着时间的推移，像素着色器可以执行的指令数量已大大增加。于是出现了<strong>多目标渲染（multiple render targets，MRT）</strong>，这使得不仅可以将像素着色器程序的结果发送到颜色缓冲和z缓冲区，还可以为每个片元生成多组值并将其保存到不同的缓冲区，每个缓冲区称为<strong>渲染目标（render target）</strong>。

!> 一些架构要求渲染目标必须具有相同的位深，甚至可能具有相同的数据格式。取决于GPU，可用的渲染目标数量为四个或八个。

另一种类型的基于MRT的渲染管线被称为延迟着色（deferred shading），其中可见性和着色是在单独的通道（passes）中完成的。第一遍渲染存储有关每个像素处对象位置和材质的数据。然后，照明和其他效果在后续的passes中完成。

像素着色器的局限性在于，它通常只能在传递给目标的片元位置上写入渲染目标，而不能从相邻像素读取当前结果。也就是说，执行像素着色器程序时，它无法将其输出直接发送到相邻像素，也无法访问其他像素的最新更改。

像素着色器无法知道或影响相邻像素的结果的规则是有例外的。诸如纹理过滤之类的操作，因为我们想知道多少图像覆盖了一个像素，所有现代GPU都通过以2×2为一组处理片元（称为四边形）来实现此功能。当像素着色器请求梯度值时，将返回相邻片元之间的差异。

DirectX 11引入了一种缓冲区类型，该类型允许对任何位置（<strong>无序访问视图（unordered access view，UAV）</strong>）的写访问。这最初仅适用于像素和计算着色器，DirectX 11.1中对UAV的访问已扩展到的所有着色器。OpenGL 4.3将此称为<strong>着色器存储缓冲区对象（shader storage buffer object，SSBO）</strong>。像素着色器以任意顺序并行运行，并且此存储缓冲区在它们之间共享。

<center><img width="70%" src="CG/RTR/14.png"/></center>
<center>左侧为栅格化，每组2 × 2像素。右侧显示了像素的梯度计算过程</center>

### 合并阶段 (Merging Stage)
合并阶段是将各个片段（在像素着色器中生成）的深度和颜色与帧缓冲区组合在一起的阶段。DirectX将此阶段称为输出合并（output merger）； OpenGL将其称为逐样本操作（per-sample operations）。

在大多数传统管线上，此阶段是模板缓冲区（stencil-buffer）和z缓冲区（z-buffer）操作发生的地方。如果片元可见，则此阶段中发生的另一种操作是颜色混合。

想象一下，通过光栅化生成的片元通过像素着色器运行，然后在应用z缓冲区时被某些先前渲染的片元隐藏。这样就不需要在像素着色器中进行所有处理。为了避免这种浪费，许多GPU在执行像素着色器之前执行一些合并测试。片元的z深度用于测试可见性。如果隐藏该片元，则将其剔除。此功能称为 Early-z。

合并阶段占据了固定功能阶段（例如三角形设置）和完全可编程着色器阶段之间的中间地带。尽管它不是可编程的，但它的操作是高度可配置的。可以将颜色混合设置为执行大量不同的操作。最常见的是涉及颜色和Alpha值的乘法，加法和减法的组合，但是其他操作（例如最小值和最大值）以及按位逻辑运算也是可能的。

### 计算着色器 (Compute Shader)
除了实现传统的图形管线外，GPU还可以用于更多用途。在计算领域，有许多非图形用途，例如计算股票期权的估计价值和训练用于深度学习的神经网络。以这种方式使用硬件称为GPU计算。诸如 CUDA 和 OpenCL 之类的平台可作为大型并行处理器来控制 GPU，而无需真正的需求或访问特定于图形的功能。这些框架通常使用带有扩展功能的 C 或 C++ 等语言以及为 GPU 制作的库。

DirectX 11中引入了计算着色器，它是GPU计算的一种形式，因为它是未锁定在图形管线中某个位置的着色器。它与渲染过程紧密相关，因为它由图形API调用。它与顶点，像素和其他着色器一起使用。它使用与管道中使用的统一着色器处理器池相同的池。与其他着色器一样，它是着色器，因为它具有一组输入数据，并且可以访问缓冲区（例如纹理）以进行输入和输出。

每个调用都会获取一个可以访问的线程索引。还有一个线程组的概念，它由DirectX 11中的1到1024个线程组成。这些线程组由x，y和z坐标指定，主要是为了简化在着色器代码中的使用。每个线程组都有少量的内存，这些内存在线程之间共享。在DirectX 11中，这等于32 kB。计算着色器由线程组执行，因此保证该组中的所有线程可以同时运行。

!> 计算着色器的一个重要优点是它们可以访问在GPU上生成的数据。需要注意的是，从 GPU 向 CPU 发送数据会产生延迟。


## Chapter 4 - Transforms - 变换
> 操纵对象的位置、方向、大小、形状，相机的位置和视图的基本工具

变换（transform）是一种操作，它接受点（points），向量（vectors）或颜色（colors）之类的实体（entities），并且以某种方式变换它们。

#### 线性变换（linear transform）
线性变换（linear transform）是保留向量加法和标量乘法的变换：

<center><img width="20%" src="CG/RTR/15.png"/></center>

#### 仿射变换（affine transform）
仿射变换（affine transform）将线性变换（linear transforms）和平移（translations）结合起来，仿射变换通常存储为4 × 4矩阵。仿射变换是先执行线性变换然后执行平移变换。

所有平移（translation），旋转（rotation），缩放（scaling），反射（reflflection）和剪切矩阵（shearing matrices）都是仿射（affine）。仿射矩阵（affine matrix）的主要特征就是它保留了线的平行性，但不一定保留长度和角度。仿射变换（affine transform）也可以是各个仿射变换级联（concatenations）的任何序列。

### 基本变换 (Basic Transforms)
<br>
<center><img width="80%" src="CG/RTR/16.png"/></center>
<center>各种变换的小结</center>

#### 平移 (Translation)
从一个位置到另一个位置的变化由平移矩阵<strong>T</strong>表示。此矩阵通过向量  去平移实体。

<center><img width="36%" src="CG/RTR/17.png"/></center>

#### 旋转 (Rotation)
旋转变换将一个向量（位置或方向）绕经过原点的给定轴旋转指定的角度。像平移矩阵一样，它是一个刚体变换（rigid-body transform），换句话说，它保留了变换后的点之间的距离，并保留了惯用性（handedness）（即从不导致左右两侧互换）。在计算机图形学中，这两种类型的变换对于定位和定向对象显然很有用。方向矩阵（orientation matrix）是与摄像机视图（camera view）或对象相关联的旋转矩阵，它定义了其在空间中的方向，即其向上和向前的方向。

绕X，Y和Z轴旋转实体的矩阵如下：

<center><img width="30%" src="CG/RTR/18.png"/></center>

如果从4 × 4矩阵中删除最底行和最右列，则将获得 3 × 3 矩阵。对于每个绕任意轴旋转phi弧度的3 × 3矩阵<strong>R</strong>，它的迹（trace，矩阵中对角元素的总和）与轴无关，是恒定的，计算公式为：tr(<strong>R</strong>) = 1 + 2cos(phi)。

所有旋转矩阵的行列式（determinant）均为 1，并且是正交的（orthogonal）。这对于任意数量的这些变换的级联（concatenations）也成立。还有另一种求逆的方法：R^-1(phi) = R(-phi)，即绕同一轴沿相反方向旋转。

#### 缩放 (Scaling)
缩放矩阵S，分别沿x，y和z方向按s_x，s_y和s_z的缩放因子去缩放实体。

<center><img width="26%" src="CG/RTR/19.png"/></center>

如果 s_x=s_y=s_z，则缩放操作称为统一操作（uniform），否则称为非统一操作（nonuniform）。

进行反缩放有两种方法：
第一种是求逆：
<center><img width="26%" src="CG/RTR/20.png"/></center>

第二种是使用齐次坐标，并在每次使用矩阵S之前进行归一化：
<center><img width="50%" src="CG/RTR/21.png"/></center>

#### 剪切 (Shearing)
剪切矩阵可以用于扭曲游戏中整个场景，以产生迷幻效果或扭曲模型的外观。剪切矩阵的第一个下标用于表示剪切矩阵正在更改哪个坐标，而第二个下标表示进行剪切的坐标：
<center><img width="26%" src="CG/RTR/22.png"/></center>
<center><img width="80%" src="CG/RTR/23.png"/></center>

### 级联变换 (Concatenation of Transforms)
由于矩阵上乘法运算的不可交换性，因此矩阵出现的顺序很重要。因此，变换的级联被认为是顺序相关的：

<center><img width="80%" src="CG/RTR/24.png"/></center>

将一系列矩阵的连接转换为单个矩阵的明显原因是为了提高效率。例如，假设你的游戏场景具有数百万个顶点，并且场景中的所有对象都必须缩放，旋转并最终平移。现在，不是将所有顶点与这三个矩阵中的每一个相乘，而是将这三个矩阵连接到一个矩阵中。然后将此单个矩阵应用于顶点。该复合矩阵为M = TRS。

注意这里的顺序。比例矩阵S应该首先应用于顶点，因此在合成中显示在右侧。该排序意味着TRSp = (T(R(Sp)))，其中p是要变换的点。顺便说一句，TRS是场景图系统（scene graph systems）常用的顺序。

### 刚体变换 (Rigid-Body Transform)
当一个人抓住一个坚固的物体时，例如从桌子上用笔将其移动到另一个位置，也许移动到衬衫的口袋里，只有物体的方向和位置会发生变化，而物体的形状通常不会受到影响。这种仅由平移和旋转的级联组成的变换称为刚体变换。

可以将任何刚体矩阵X表示为平移矩阵T(t)和旋转矩阵R的串联：

<center><img width="30%" src="CG/RTR/25.png"/></center>

#### LookAt矩阵
计算机图形中的常见任务是调整相机的方向，使其对准特定位置。

假设照相机位于c处，我们希望照相机看着目标l，并且照相机的给定方向为u'。我们要计算一个由三个向量{r,u,v}组成的基数。我们从计算视点向量为v=(c-1)/||c-1||开始，即从目标到摄像机位置的归一化向量。然后可以将向右看的向量计算为r=-(v×u')/||v×u'||。通常不能保证u'向量指向正上方，因此最终的向上向量是另一个叉积u=v×r。

<center><img width="70%" src="CG/RTR/26.png"/></center>

### 法线变换 (Normal Transform)
单个矩阵可用于一致地变换点，线，三角形和其他几何形状。矩阵还可以沿这些线或在三角形的曲面上变换切向量。但是，矩阵不能始终用于变换一个重要的几何特性，即表面法线（和顶点照明法线）。

下图左侧是原始几何图形，三角形以及从侧面显示的法线。中间的插图显示了如果模型沿 x 轴缩放 0.5，法线使用相同的矩阵会发生什么。右图显示了法线的正确变换：

<center><img width="70%" src="CG/RTR/27.png"/></center>

适当的方法不是使用矩阵本身相乘，而是使用矩阵的伴随项的转置相乘。

### 逆的计算 (Computation of Inverses)
在许多情况下都需要逆（inverses）。例如在坐标系之间来回切换时， 根据有关变换的可用信息，我们可以使用以下三种方法之一来计算矩阵的逆：
- 如果矩阵是单个变换或具有给定参数的简单变换序列，则该矩阵可以通过“反转参数”和矩阵顺序轻松地计算。举个例子，如果M=T(t)R(phi)，则M^(-1)=R(-phi)T(-t)。这很简单，并且保留了变换的准确性，这在渲染大世界时很重要。
- 如果已知矩阵是正交的，则M^(-1)=M^T，即转置为逆。旋转的任何序列都是旋转，因此是正交的。
- 如果没有任何已知条件，则可以使用伴随方法（the adjoint method），克莱姆法则（Cramer’s rule），LU分解（LU decomposition）或高斯消除法（Gaussian elimination）来计算逆。通常最好使用克莱姆法则和伴随方法，因为它们的分支操作较少； 在现代体系结构上最好避免使用“if”测试。

## 特殊矩阵变换与运算 (Special Matrix Transforms and Operations)
### 欧拉变换 (The Euler Transform)
这种变换是构造矩阵以将自己（即相机）或任何其他实体定向到某个方向的一种直观方法。它的名字来自伟大的瑞士数学家莱昂哈德·欧拉（Leonhard Euler，1707–1783年）。

欧拉变换是三个矩阵的乘积，矩阵的顺序可以以24种不同的方式选择，这可以通过选择矩阵的顺序来实现。

由于E是旋转的串联，因此它也显然是正交的。因此，它的逆可以表示为E^(-1)=E^T=(R_zR_xR_y)^T=(R_x)^T(R_y)^T(R_z)^T，当然，直接使用E的转置会更容易。

欧拉角 ， 和  分别表示 head，pitch 和 roll 应按其顺序旋转以及绕其各自的轴旋转多少。有时，所有角度都称为“rolls”，例如，我们的“head”为“ y-roll”，而我们的“pitch”为“ x-roll”。另外，“head”有时也称为“yaw”，例如在飞行模拟中。

<center><img width="50%" src="CG/RTR/28.png"/></center>
<center>欧拉变换及其与更改 head，pitch 和 roll 的方式之间的关系</center>

### 从欧拉变换中提取参数 (Extracting Parameters from the Euler Transform)
在某些情况下，使用从正交矩阵中提取欧拉参数 h，p 和 r 的过程很有用：

<center><img width="50%" src="CG/RTR/29.png"/></center>

将三个旋转矩阵串联起来：

<center><img width="90%" src="CG/RTR/30.png"/></center>

由此可见，pitch 参数由 sin(p)=e_21 给出。同样，将 e_01 除以 e_11，并类似地将 e_20 除以 e_22，会产生以下用于 head 和 roll 参数的提取公式：

<center><img width="60%" src="CG/RTR/31.png"/></center>

因此，如下所示，使用函数 atan2（y，x）从矩阵E提取欧拉参数h（head），p（pitch）和r（roll）：

<center><img width="20%" src="CG/RTR/32.png"/></center>

由于p不影响第一列中的值，因此当cos(p)=0时，我们可以使用sin(r)/cos(r)=tan(r)=e_10/e_00，得出r=atan2(e_01,e_00)。

!>根据反正弦的定义，-pi/2≤p≤pi/2，这意味着如果使用该间隔之外的p值创建E，则无法提取原始参数，因为h，p 和 r 不是唯一的。

!>使用欧拉变换时，可能会发生万向节死锁（gimbal lock），也就是旋转时，会失去一个自由度。举个例子，变换的顺序是 x/y/z。假设第二次旋转我们绕 y 轴旋转 pi/2，这样会旋转局部 z 轴以使其与原始 x 轴对齐，因此围绕 z 的最终旋转是不正确的。

### 矩阵分解 (Matrix Decomposition)
到目前为止，我们一直在假设我们知道所使用的变换矩阵的初始状态和历史记录的情况下进行工作。通常情况下并非如此。例如，仅连接的矩阵可以与某个变换后的对象相关联。从级联矩阵中提取各种变换的任务称为<strong>矩阵分解（matrix decomposition）</strong>。

提取变换的原因有很多。用途包括：

- 为对象提取比例因子。
- 查找特定系统所需的变换。（例如，某些系统可能不允许使用任意 4×4 矩阵）
- 确定模型是否仅经历了刚体变换。
- 在动画中的关键帧之间进行插值，其中仅对象的矩阵可用。
- 从旋转矩阵中删除剪切。

### 绕任意轴旋转 (Rotation about an Arbitrary Axis)
假设旋转轴 r 已归一化，并且我们需要创建一个围绕 e 旋转 alpha 弧度的变换。为此，我们首先变换到旋转轴所在的空间，这是通过一个 M 旋转矩阵完成的，然后执行实际的旋转，之后使用 M^-1 进行变换。

<center><img width="13%" src="CG/RTR/33.png"/></center>

该矩阵将向量 r 变换为 x 轴，将 s 变换为 y 轴，将 t 变换为 z 轴。因此，然后使围绕标准化向量 r 旋转 alpha 弧度的最终变换为：

<center><img width="20%" src="CG/RTR/34.png"/></center>

换句话说，这意味着首先我们进行变换，使 r 为 x 轴（使用 M），然后围绕该 x 轴旋转 alpha 弧度（使用 R_x(alpha)），然后使用 M 的逆函数进行变换 ，在这种情况下为 M^T，因为 M 是正交的。

Goldman提出了另一种通过 phi 弧度绕任意归一化轴 r 旋转的方法：

<center><img width="90%" src="CG/RTR/35.png"/></center>

## 四元数 (Quaternions)
四元数是复数的扩展，尽管它是威廉·罗恩·汉密尔顿爵士（Sir William Rowan Hamilton）于1843年发明的，但直到1985年，Shoemake才将它们引入计算机图形学领域。

>四元数用于表示旋转和方向。它们在几种方面都优于欧拉角和矩阵。任何三维定向都可以表示为围绕特定轴的单个旋转。四元数可用于稳定方向和恒定插值，而欧拉角无法很好地完成这些操作。

### 数学背景 Mathematical Background
#### 定义
四元数q可以用以下所有等效的方式定义：

<center><img width="60%" src="CG/RTR/36.png"/></center>

变量q_w被称为四元数q的实部（real part）。虚部（imaginary part）为q_v，i，j和k称为虚单位（imaginary units）。
对于虚部q，我们可以使用所有法向向量运算，例如加法，缩放，点积，叉积等等。使用四元数的定义，得出两个四元数q和r之间的乘法运算，如下所示。注意，虚部的乘法是不可交换的。

#### 乘法（Multiplication）
我们使用叉积和点积来计算两个四元数的乘法:

<center><img width="50%" src="CG/RTR/37.png"/></center>

#### 加法（Addition）

<center><img width="50%" src="CG/RTR/38.png"/></center>

#### 共轭（Conjugate）

<center><img width="30%" src="CG/RTR/39.png"/></center>


#### 归一化（Norm）

<center><img width="40%" src="CG/RTR/40.png"/></center>


#### 恒等式（Identity）

<center><img width="13%" src="CG/RTR/41.png"/></center>

#### 逆（Inverse）

<center><img width="18%" src="CG/RTR/42.png"/></center>

#### 共轭规则（Conjugate rules）

<center><img width="20%" src="CG/RTR/43.png"/></center>


#### 归一化规则（Norm rules）

<center><img width="20%" src="CG/RTR/44.png"/></center>

#### 乘法定律（Laws of Multiplication）- 线性度（Linearity）

<center><img width="26%" src="CG/RTR/45.png"/></center>

#### 乘法定律（Laws of Multiplication）- 关联性（Associativity）

<center><img width="16%" src="CG/RTR/46.png"/></center>

#### 对数运算

<center><img width="30%" src="CG/RTR/47.png"/></center>

#### 幂运算

<center><img width="60%" src="CG/RTR/48.png"/></center>

### 四元数变换 (Quaternion Transforms)

<center><img width="30%" src="CG/RTR/49.png"/></center>
<center>由单位四元数<img width="20%" src="CG/RTR/50.png"/>表示的旋转变换</center>

q的任何非零实数倍也表示相同的变换，这意味着q和-q表示相同的旋转。也就是说，取反轴u_q和实部q_w，将生成一个四元数，该四元数的旋转与原始四元数的旋转完全相同。这也意味着从矩阵中提取四元数可以返回q或 -q。

### 矩阵转换（Matrix Conversion）
由于通常需要组合几个不同的变换，并且大多数变换都是矩阵形式，因此需要一种将四元数转换为矩阵的方法。四元数 q可以转换成矩阵M^q：

<center><img width="55%" src="CG/RTR/51.png"/></center>

在此，标量为 s=2/(nq)。对于单位四元数，这简化为：

<center><img width="55%" src="CG/RTR/52.png"/></center>

一旦构建了四元数，就无需计算三角函数（trigonometric functions），因此转换过程实际上是有效的。

从正交矩阵M^q到单位四元数q的反向转换要复杂得多：

<center><img width="20%" src="CG/RTR/53.png"/></center>

这些等式的含义是，如果q_w是已知的，则可以计算向量v_q的值，从而得出q：

<center><img width="55%" src="CG/RTR/54.png"/></center>

<center><img width="40%" src="CG/RTR/55.png"/></center>

为了具有稳定的数值，应该避免小数除法。因此，首先设置<img width="20%" src="CG/RTR/56.png"/>，由此得出：

<center><img width="40%" src="CG/RTR/57.png"/></center>

这又意味着 m_00,m_11,m_22 和 u 中的最大值确定 q_x, q_y, q_z, 和 q_w 中的哪个最大。如果 q_w 不是最大，则使用下式计算q_x,q_y,q_z的最大值：

<center><img width="38%" src="CG/RTR/58.png"/></center>

### 球面线性插值（Spherical Linear Interpolation）
球面线性插值是在给定两个单元四元数q和r以及参数t∈[0,1]的情况下，计算插值四元数。

该运算的代数形式由下面的复合四元数s表示：

<center><img width="20%" src="CG/RTR/59.png"/></center>

但是，对于软件实现，以下形式更合适：

<center><img width="60%" src="CG/RTR/60.png"/></center>

slerp 代表球面线性插值(spherical linear interpolation)，为了计算该方程式所需的phi，可以使用以下事实：

<center><img width="40%" src="CG/RTR/61.png"/></center>

对于t∈[0,1]，slerp 函数计算（唯一）内插四元数，它们共同构成从q到r的二维单位球面上的最短弧。圆弧位于由q,r和原点之间的平面与三维单位球面的交点形成的圆上。计算出的旋转四元数以固定速度绕固定轴旋转。这样的曲线具有恒定速度，因此加速度为零，称为<strong>测地曲线（geodesic curve）</strong>。球体上的大圆是通过原点和球体的平面相交而生成的，这种圆的一部分称为<strong>大圆弧（great arc）</strong>。

<center><img width="30%" src="CG/RTR/62.png"/></center>
<center>单位四元数表示为单位球面上的点。slerp函数用于在四元数之间进行插值，并且插值路径是球面上的大弧</center>

!> 实际上，直接计算一个 slerp 是昂贵的操作，因为它涉及调用三角函数（trigonometric functions）

### 从一个向量旋转到另一个向量（Rotation from One Vector to Another）
常见的操作是通过最短路径从一个方向s转换到另一个方向t。四元数的数学极大地简化了此过程，并显示了四元数与该表示形式的密切关系。

首先，将s和t归一化。然后计算称为u的单位旋转轴，其计算公式为u=(s×t)/||s×t||。接下来，e=s·t=cos(2phi)和||s×t||=sin(2phi),其中2phi是s和t之间的角度。那么表示从s到t的旋转的四元数为q=(sin(phi u),cos(phi)),使用半角关系和三角恒等式简化：

<center><img width="30%" src="CG/RTR/63.png"/></center>
<center><img width="50%" src="CG/RTR/64.png"/></center>

当s和t指向几乎相同的方向时，以这种方式直接生成四元数（相对于叉积s×t的归一化）避免了数值不稳定。当s和t指向相反的方向时，这两种方法都会出现稳定性问题，因为它们会被零除。当检测到这种特殊情况时，可以使用任何垂直于s的旋转轴旋转到t。

有时我们需要从s到t旋转的矩阵表示：

<center><img width="50%" src="CG/RTR/65.png"/></center>

在此等式中，我们使用了以下中间计算（intermediate calculations）：

<center><img width="38%" src="CG/RTR/66.png"/></center>

可以看出，由于简化，所有平方根和三角函数都消失了，因此这是创建矩阵的有效方法。

请注意，当s和t平行或接近平行时必须小心，因为||s×t||≈0。如果phi≈0，那么我们可以返回单位矩阵。但是，如果2phi≈pi，那么我们可以绕任何轴旋转pi弧度。该轴可以作为s与不平行于s的任何其他向量之间的叉积找到。

### 顶点混合 (Vertex Blending)
顶点混合（Vertex blending）是解决柔性形变问题的一种流行解决方案。该技术还有其他几个名称，例如线性混合蒙皮（linear-blend skinning），包络（enveloping）或骨架子空间变形（skeleton-subspace deformation）。

<center><img width="70%" src="CG/RTR/67.png"/></center>

上图中，手臂由前臂和上臂组成，使用左侧的两个独立对象的刚体变换进行动画处理。肘部看起来不现实。在右侧，对一个对象使用顶点混合。最右边的手臂说明了当简单的蒙皮将两个部分直接覆盖以覆盖肘部时发生的情况。最右边的手臂说明了使用顶点混合时发生的情况，并且某些顶点以不同的权重进行了混合：（2/3，1/3）表示顶点对上臂的变换的权重为2/3，对前臂的变换的权重为。1/3。该图在最右边的插图中还显示了顶点混合的缺点。在这里，可以看到肘部内部的折叠。使用更多的骨骼和更精心选择的权重可以达到更好的效果。

通过进一步执行这一步骤，可以使单个顶点可以通过几种不同的矩阵进行变换，并将得到的位置加权并混合到一起。这是通过为动画对象设置骨骼来完成的，其中每个骨骼的变换可能会通过用户定义的权重影响每个顶点。由于整个手臂可能是“弹性的”，即所有顶点可能受到多个矩阵的影响，因此整个网格（mesh）通常称为（骨骼上的）蒙皮（skin）。

在数学上，这用如下公式表示，其中p是原始顶点，而u(t)是变换后的顶点，其位置取决于时间t：

<center><img width="60%" src="CG/RTR/68.png"/></center>

有 n个骨骼影响p的位置，这在世界坐标中表示出来。值w_i是顶点p的骨骼i的权重。M_i矩阵从初始骨骼的坐标系转换为世界坐标。通常，骨骼的控制关节位于其坐标系的原点。例如，前臂骨骼将其肘关节移动到原点，而动画旋转矩阵将手臂的这一部分绕关节移动。B_i(t)矩阵是第i个骨骼的世界变换，会随着时间变化以对对象进行动画处理，并且通常是多个矩阵的串联，例如以前的骨骼变换的层次结构和局部动画矩阵。

在实践中，对于动画的每一帧，为每个骨骼连接矩阵B_i(t)和(M_i)^-1，并且每个结果矩阵都用于变换顶点。顶点P由不同骨骼的级联矩阵转换，然后使用权重W_i进行混合，因此称为顶点混合（vertex blending）。权重是非负的，并且总和为1，因此发生的事情是将顶点转换到几个位置，然后在其中进行插值。这样，对于所有的i=0...n-1，变换后的点u将位于点集B_i(t)·(M_i)^-1·p(固定的t)的凸包中。

顶点混合非常适合在 GPU 上使用。网格中的顶点集可以放置在静态缓冲区中，该缓冲区会一次发送到 GPU 并重新使用。在每个框架中，只有骨骼矩阵会发生变化，而顶点着色器会计算它们对存储的网格的影响。这样，可以最大程度地减少在 CPU 上处理和从 CPU 传输的数据量，从而使 GPU 可以有效地渲染网格。如果可以将模型的整个骨矩阵一起使用，则是最简单的。否则，必须拆分模型并复制一些骨骼。或者，可以将骨骼变换存储在顶点访问的纹理中，从而避免达到寄存器存储限制。通过使用四元数表示旋转，每个变换可以仅存储在两个纹理中。如果可用，无序访问视图存储将允许重新使用蒙皮结果。

> 我们可以指定超出 [0,1] 范围或不等于 1 的权重集。但是，这仅在使用某些其他混合算法（例如变形目标，morph targets）时才有意义。

!> 基本顶点融合的一个缺点是可能发生不必要的折叠，扭曲和自相交。更好的解决方案是使用四元数。

基于四元数的蒙皮技术有助于保持原始变换的刚度，因此避免了四肢关节的扭曲。计算量不到线性蒙皮混合的成本的 1.5倍，并且效果很好：

<center><img width="60%" src="CG/RTR/69.png"/></center>
<center>左侧显示了使用线性混合蒙皮时关节处的问题。在右侧，使用双四元数混合可以改善外观</center>

### 变形 (Morphing)
变形（Morphing）涉及解决两个主要问题，即顶点对应问题（the vertex correspondence problem）和插值问题（the interpolation problem）。给定两个任意模型，这些模型可能具有不同的拓扑（topologies），不同的顶点数量和不同的网格连接性，通常必须从建立这些顶点对应关系开始，这是一个困难的问题。

但是，如果两个模型之间已经存在一对一的顶点对应关系，则可以在每个顶点的基础上进行插值。也就是说，对于第一个模型中的每个顶点，在第二个模型中必须仅存在一个顶点，反之亦然。这使插值变得容易。例如，线性插值可以直接在顶点上使用。

为了计算时间t∈[t0,t1]的变形顶点，我们首先计算s=(t-t0)/(t1-t0)，然后进行线性顶点混合：

<center><img width="20%" src="CG/RTR/70.png"/></center>

其中p0和p1对应于同一顶点，但是处在不同的时间t0和t1。

用户具有更直观控制的变形变体称为变形目标（morph targets）或混合形状（blend shapes）：

<center><img width="80%" src="CG/RTR/71.png"/></center>

我们从一个中性模型开始，在这种情况下，它是一张脸。让我们用 N 表示该模型。此外，我们还有一组不同的脸部姿势。在示例中只有一个姿势，即一张笑脸。通常我们可以允许 k≥1 个不同的姿势，表示为 P_i,i∈[1...k]。作为预处理，“差异面”的计算公式为：D_i=P_i-N，即，从每个姿势中减去中性模型。

在这一点上，我们有一个中性模型 N 和一组差异姿势 D_i。然后可以使用以下公式获得变形模型 M：

<center><img width="20%" src="CG/RTR/72.png"/></center>

变形目标（Morph targets）是一种强大的技术，可为动画师提供很多控制，因为模型的不同特征可以独立于其他特征进行操纵。

### 几何缓存回放 (Geometry Cache Playback)
在剪辑场景（cut scenes）中，可能希望使用极高质量的动画，例如，对于无法使用上述任何方法表示的运动。天真的方法是存储所有帧的所有顶点，从磁盘读取它们并更新网格。但是，对于短动画中使用的 30,000 个顶点的简单模型，这可能达到50 MB / s。

首先，使用量化（quantization）。例如，位置和纹理坐标使用每个坐标的 16 位整数存储。在执行压缩后无法恢复原始数据的意义上，这一步骤是有损的。为了进一步减少数据，进行了空间和时间预测，并对差异进行了编码。对于空间压缩，可以使用平行四边形预测。对于三角形带（triangle strip），下一个顶点的预测位置就是当前三角形在边缘周围的三角形平面中反射的三角形，从而形成平行四边形（parallelogram）。与新位置的差异接下来会被编码（encoded）。有了良好的预测，大多数值将接近零，这对于许多常用的压缩方案是十分理想的。与 MPEG 压缩类似，在时间维度上也会进行预测。也就是说，每  帧执行一次空间压缩。在这两者之间，将在时间维度上进行预测，例如，如果某个特定顶点通过增量向量从帧  移动到帧 ，则很可能以与帧  相似的量移动。这些技术减少了存储量，从而足以使该系统用于实时流数据。

## 投影 (Projections)
在实际渲染场景之前，必须将场景中的所有相关对象投影到某种平面或某种简单体积上。此后，执行裁剪和渲染。

### 正交投影 (Orthographic Projection)
正交投影的特征是平行线在投影之后保持平行。当使用正交投影观看场景时，无论与相机的距离如何，对象都保持相同的大小。

用于执行正交投影的矩阵由六元组 (l,r,b,t,n,f) 表示，分别表示左侧（left），右侧（right），底部（bottom），顶部（top），近侧（near）和远侧（far）平面。该矩阵缩放并将由这些平面形成的与轴对齐的边界框（axis-aligned bounding box, AABB）转换为以原点为中心的与轴对齐的立方体。AABB 的最小角为 (l,b,n)，最大角为
是 (r,t,f)。重要的是要意识到 n>f，因为我们正在向下看 z 轴的负空间。我们的常识是，接近值应该比远端值低，因此，可以让用户按原样提供它们，然后在内部对它们取反（negate）。

在 OpenGL 中，与轴对齐的立方体的最小角为(-1,-1,-1)，最大角为(1,1,1)。在 DirectX 中，范围是(-1,-1,0)到(1,1,1)。此立方体称为规范视图体（canonical view volume），而该体积中的坐标称为规范化设备坐标（normalized device coordinates）。变换为标准视图体积的原因是在此处能够更有效地执行裁剪（clipping）。

<center><img width="80%" src="CG/RTR/73.png"/></center>
<center>变换规范视图体（canonical view volume）上的轴对齐框（axis-aligned box）。首先平移左侧的框，使其中心与原点重合。然后将其缩放以获取规范视图体的大小，如右侧所示</center>

变换为标准视图体（canonical view volume）后，将要渲染的几何图形的顶点裁剪（clipped）到该立方体上。最后，通过将剩余的单位正方形映射到屏幕来渲染不在立方体之外的几何图形。此正交变换如下所示：

<center><img width="70%" src="CG/RTR/74.png"/></center>

在计算机图形学中，投影后最常使用左手坐标系（left-hand coordinate system），即对于视口，x 轴向右，y 轴向上，而 z 轴进入视口。

DirectX 将 z 深度（z-depth）映射到 [0,1] 范围，而不是OpenGL的 [-1,1]。这可以通过在正交矩阵之后应用简单的缩放和平移矩阵来实现，即

<center><img width="30%" src="CG/RTR/75.png"/></center>

因此，DirectX中使用的正交矩阵为:

<center><img width="40%" src="CG/RTR/76.png"/></center>

### 透视投影 (Perspective Projection)
透视投影比正交投影更复杂的变换是透视投影，它通常在大多数计算机图形应用程序中使用。在这里，平行线在投影后通常不平行； 相反，它们可能会在极端情况下收敛到单个点。透视更紧密地匹配我们如何感知世界，即，更远的物体更小。

<center><img width="80%" src="CG/RTR/77.png"/></center>
<center>使用相似三角形导出透视投影矩阵（perspective projection matrix）</center>

假设摄像机（视点）位于原点，并且我们要将一个点 p 投影到平面 z=-d,d>0，从而产生一个新点 q=(q_x,q_y,-d) 。图4.19 描绘了这种情况。从该图所示的相似三角形中，得出 q 的 x 分量的以下推导：

<center><img width="25%" src="CG/RTR/78.png"/></center>

q 的其他分量的表达式为 q_y=-dp_y/p_z（类似于 q_x 获得），q_z=-d。与上面的公式一起，它们给出了透视投影矩阵 P_p，如下所示：

<center><img width="20%" src="CG/RTR/79.png"/></center>

该矩阵可产生正确的透视投影，可通过以下方式确认:

<center><img width="60%" src="CG/RTR/80.png"/></center>

最后一步来自以下事实：整个矢量除以 w 分量（在这种情况下为 -p_z/d），最后得到 1。由于我们要投影到该平面上，因此所得的  z 值始终为 -d。

从直觉上讲，很容易理解为什么齐次坐标允许投影。齐次化过程的一种几何解释是将点 (p_x, p_y, p_z) 投影到平面 w = 1 上。

与正交变换（orthographic transformation）一样，还有一个透视变换（perspective transform），而不是实际投影到平面（不可逆）上，而是将视锥从视锥变换为前述的规范视像体。在这里，视锥视点假定从z=n开始并在z=f结束，且0>n>f。z=n处的矩形的最小角为(l, b, n)，最大角为(r, t, n)。

<center><img width="80%" src="CG/RTR/81.png"/></center>
<center>矩阵 P_p 将视锥体（view frustum）转换为单位立方体，称为标准视域（canonical view volume）</center>

参数(l,r,b,t,n,f)确定摄像机的视锥（view frustum）。水平视野由视锥的左右平面（由l和r决定）之间的角度确定。以相同的方式，垂直视野由顶平面和底平面之间的角度（由t和b确定）确定。视野越大，相机“看得越多”。可以通过r≠-l或t≠-b来创建不对称视锥（Asymmetric frusta）。不对称视锥可用于立体观看（stereo viewing）和虚拟现实（virtual reality）。

视野（the field of view）是提供场景感的重要因素。与计算机屏幕相比，眼睛本身具有物理视野。这种关系是：phi=2arctan(w/2d),其中 \phi 是视野，w 是垂直于视线的物体的宽度，d 是到物体的距离。

与物理设置相比，使用更窄的视野将减少透视效果，因为观看者将放大场景。设置较宽的视野将使对象看起来失真（例如使用广角相机镜头），尤其是在屏幕边缘附近，并且会放大附近对象的比例。然而，较宽的视野使观看者感觉到物体更大并且更令人印象深刻，并且具有向用户提供有关周围环境的更多信息的优点。

<center><img width="30%" src="CG/RTR/82.png"/></center>
<center>将视锥转化为单位立方体的透视变换矩阵</center>

将转换应用到一个点后，我们将得到另一个点q=(q_x, q_y, q_z, q_w)^T。此时的 w 分量 q_w（通常）将为非零且不等于1。要获得投影点p，我们需要除以 q_w。矩阵 P_p 总是将 z=f 映射为 +1，z=n 映射为 -1。

远平面以外的对象将被裁切，因此不会出现在场景中。另外，透视投影可以令远平面取到无穷远：

<center><img width="30%" src="CG/RTR/83.png"/></center>

综上所述，应用透视变换（以任何形式）P_p，然后进行裁剪和齐次化（除以 w），从而得到标准化的设备坐标。

以下是 OpenGL 中的透视投影矩阵公式：

<center><img width="35%" src="CG/RTR/84.png"/></center>

一个更简单的设置是仅提供垂直视场 phi，宽高比 a=w/h（其中 w×h 是屏幕分辨率），n'和 f'，于是：

<center><img width="35%" src="CG/RTR/85.png"/></center>

这是 DirectX 公式(将近平面映射到 z=0（而不是 z=-1），而将远平面映射到 z=1)：

<center><img width="35%" src="CG/RTR/86.png"/></center>

!> 近平面和远平面的放置会影响 z 缓冲区的精度

#### 增加深度精度的方法
有几种增加深度精度的方法。一种常见的方法（我们称为反向 z， reversed z）是使用浮点深度或整数存储1.0-z_NDC。

<center><img width="80%" src="CG/RTR/87.png"/></center>

使用 DirectX 变换设置深度缓冲区的不同方法，即z_NDC∈[0,+1]。

左上方：标准整数深度缓冲区，此处显示为4位精度（因此 y 轴上有 16 个标记）。

右上角：远平面设置为 ∞，两个轴上的微小偏移表明这样做不会损失太多精度。

左下：具有3个指数位和 3 个尾数位用于浮点深度。由于分布在y轴上是非线性的，这使得在x轴上的分布更糟。

右下角：反转的浮点深度，即1-z_NDC，结果分布更好。

Lloyd提出使用深度值的对数来提高阴影贴图的精度。Lauritzen等使用前一帧的 z 缓冲区（z-buffer）来确定最大近平面和最小远平面。对于屏幕空间深度，Kemen建议对每个顶点使用以下重新映射：

<center><img width="50%" src="CG/RTR/88.png"/></center>

其中w是投影矩阵之后的顶点的 w 值，而 z 是顶点着色器的输出 z。常数 f_{c} 为 f_{c}=2/\textrm{log}_{2}(f+1)，其中 f 为远平面。当仅在顶点着色器中应用此变换时，深度仍将由 GPU 在顶点的非线性变换深度之间在三角形上线性插值。由于对数是单调函数，因此只要分段线性插值与精确的非线性变换深度值之间的差异较小，遮挡剔除硬件和深度压缩技术仍将起作用。在大多数情况下，具有足够的几何细分的情况是正确的。但是，也可以对每个片段应用转换。这是通过输出每个顶点的值 e=1+w 来完成的，然后由 GPU 在三角形上进行插值。然后，像素着色器将片段深度修改为 log^2(e_i)f_c/2，其中 e_i 是 e 的内插值。当 GPU 中没有浮点深度并且使用深度较大的距离进行渲染时，此方法是不错的选择。

Cozzi建议使用多视锥（multiple frusta），这可以提高准确度以有效地达到任何期望的比率。视锥在深度方向上分为几个不重叠的较小的子视锥，它们的联合恰好是视锥。子视锥表以从后到前的顺序渲染。首先，清除颜色和深度缓冲区，并将所有要渲染的对象分类到它们重叠的每个子视锥中。对于每个子视锥，设置其投影矩阵，清除深度缓冲区，然后渲染与子视锥重叠的对象。


## Chapter 5 - Shading Basics - 着色基础
> 无论是写实（realistic）还是风格化（stylized），我们都会先讨论材质和光源的定义，还有它们是如何呈现出我们期望的表面外观（appearance）。<br>此章节介绍一些表面外观相关的话题，例如通过抗锯齿（也称反走样，Antialiasing）、透明度(Transparency)、伽马校正（Gamma Correction）来提供更高质量的图像

渲染三维对象的图像时，模型不仅应具有适当的几何形状，而且还应具有所需的视觉外观。根据应用程序的不同，其范围可以从照片写实（外观与真实对象的照片几乎相同）到出于创造性原因选择的各种类型的风格化外观。

### 着色模型 Shading Models
决定渲染物体的外观的第一步是选择一个渲染模型（shading model）用来描述物体的颜色应该怎样变化，相关的因素有表面方向（surface orientation），视角方向（view direction），以及光照（lighting）等等。






## Chapter 6 - Texturing - 纹理化
> 实时渲染最为强大的工具之一就是能够快速访问以及在表面(Surfaces)显示图像。这个过程被称为纹理化(Texturing)


## Chapter 7 - Shadows - 阴影
> 介绍了目前比较流行的快速计算阴影的算法


## Chapter 8 - Light and Color - 光与颜色
> 在实现基于物理的渲染之前，我们首先需要了解如何去量化光和颜色。在物理渲染过程完成后，我们需要将得到的数量值显示出来。<br>本章涵盖两个话题：计算屏幕参数（accounting for the properties of the screen）和观察环境（viewing environment）


## Chapter 9 - Physically Based Shading - 基于物理的着色
> 本章从物理现象背后的规律讲起，涵盖大量的渲染材质的模型，并且会在最后提出一个方法，此方法可以用来混合材质，对材质进行过滤以避免锯齿（走样），并且保持原有的表面外观


## Chapter 10 - Local Illumination - 局部光照
> 本章探索了描绘更精细光源的算法。在表面着色时我们会考虑到光是由具有特别形状的物理对象所发射出的


## Chapter 11 - Global Illumination - 全局光照
> 模拟光源与场景之间多重交互的算法大大提升了图像的真实感。我们会讨论环境和方向光遮挡，在漫反射和高光表面上渲染全局光照效果的实现方法，另外还有一些有前景的统一方法


## Chapter 12 - Image-Space Eﬀects - 图像空间特效
> 图形硬件擅长快速的图像处理。本章首先会讨论图像滤波（Image filtering）和重投影技术（reprojection techniques），然后会探讨几种常用的后处理效果：镜头光晕（lens flares）、动态模糊（motion blur）和景深（depth of field）


## Chapter 13 - Beyond Polygons - 多边形之外
> 三角形（Triangles）并不总是描述对象的最快或最真实的方式。基于使用图像（images）、点云（point clouds）、体素（voxels）和其他采样集的交替表现都有其各自的优点


## Chapter 14 - Volumetric and Translucency Rendering - 体积和半透明渲染
> 本章将聚焦于体积材质呈现以及其与光源相互作用的理论与实践。模拟的范围将从大尺度的大气层效果（large-scale atmospheric effects）到细的头发纤维内的光线散射（light scattering）


## Chapter 15 - Non-Photorealistic Rendering - 非真实感渲染
> 试图使场景看起来更逼真（realistic）只是渲染场景方法中的一种而已。本章会探讨一下其他的渲染风格，如卡通阴影和水彩画效果。此外，线框（line）和文本（text）生成技术也会在本章讨论


## Chapter 16 - Polygonal Techniques - 多边形技术
> 几何数据来源广泛，有时需要进行修改以便渲染得快速、准确。本章将会从多方面介绍多边形数据的呈现和压缩


## Chapter 17 - Curves and Curved Surfaces - 曲线和曲面
> 更复杂的曲面表示提供了一些优势，例如能够在图像质量和渲染速度之间进行权衡、更紧凑的描绘以及平滑的曲面生成


## Chapter 18 - Pipeline Optimization - 管线优化
> 一旦应用程序运行并使用了高效的算法，就可以使用各种优化技术使其变得更快。本章讨论的主题是怎样找到性能优化瓶颈（bottleneck）并如何去解决它。此外，本章还讨论了多进程（Multiprocessing）的相关内容


## Chapter 19 - Acceleration Algorithms - 加速算法
> 本章涵盖了各种形式的剔除（Culling）和细节层次渲染（LOD, Level Of Detail）方法


## Chapter 20 - Eﬃcient Shading - 高效着色
> 场景中的大量灯光会大大降低性能。另外，在确定表面片元（Fragment）是否会显示之前就进行完全的着色计算，也是性能浪费的一大来源。本章探索了一系列的方法来消除低效的着色操作


## Chapter 21 - Virtual and Augmented Reality - 虚拟现实与增强现实
> 这些领域有着特殊的挑战和技术，要求高效、快速、稳定地生成真实的图像


## Chapter 22 - Intersection Test Methods - 相交测试方法
> 相交测试（Intersection testing）对于渲染、用户交互和碰撞检测非常重要。本章将深度涵盖一系列最有效的通用几何相交测试算法


## Chapter 23 - Graphics Hardware - 图形硬件
> 这里的重点是一些组件（Components），如颜色深度（color depth）、帧缓冲区（framebuffers）和基本架构类型（basic architecture types）


## Chapter 24 - The Future - 展望未来
> 猜猜看未来有啥？
