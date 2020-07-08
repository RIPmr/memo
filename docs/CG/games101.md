# Computer Graphics Note

GAMES101-现代计算机图形学入门-闫令琪

## Linear Algebra
- Magnitude (length) of a vector written as <img width="4%" src="CG/games101/1.jpg"/>
- Unit vector
	- A vector with magnitude of 1
	- Finding the unit vector of a vector (omalztion): (hat <strong>a</strong>)<img width="12%" src="CG/games101/2.jpg"/>
	- Used to represent directions

- Dot Production
	- Find angle between two vectors
	(e.g. cosine of angle between light source and surface)
	- Finding projection of one vector on another (perpendicular, ie. perp <strong>b</strong>)


<center><img width="50%" src="CG/games101/3.jpg"/></center>
<center>Dot(scalar) Product</center>
<br>
<center><img width="50%" src="CG/games101/4.jpg"/></center>
<center>Properties</center>
<br>
<center><img width="50%" src="CG/games101/5.jpg"/></center>
<center>Component-wise multiplication, then adding up</center>
<br>
<center><img width="70%" src="CG/games101/6.jpg"/></center>
<center><img width="70%" src="CG/games101/7.jpg"/></center>
<center>Dot Product for Projection</center>
<br>
<center><img width="70%" src="CG/games101/8.jpg"/></center>
<center>Determine direction</center>

- Cross Production
	- Cross product is orthogonal to two initial vectors
	- Direction determined by right-hand rule
	- Useful in constructing coordinate systems (later)
	
<center><img width="70%" src="CG/games101/9.jpg"/></center>
<center>Properties</center>
<br>
<center><img width="60%" src="CG/games101/10.jpg"/></center>
<center>Cross Product</center>
<br>
<center><img width="60%" src="CG/games101/11.jpg"/></center>
<center>叉乘的应用，计算在某坐标系下的分量（三方向上的投影）</center>



- Matrix
	- (number of) columns in A must = rows in B
	- (MxN)(NxP)=(MxP)
	
<center><img width="60%" src="CG/games101/12.jpg"/></center>
<center>Properties</center>
<br>
<center><img width="60%" src="CG/games101/13.jpg"/></center>
<center>Transpose of a Matrix</center>
<br>
<center><img width="40%" src="CG/games101/14.jpg"/></center>
<center>Identity Matrix anid Inverses</center>
<br>
<center><img width="60%" src="CG/games101/15.jpg"/></center>
<center>Vector multiplication in Matrix form</center>


## Transformation
### 2D Transformation
<center><img width="30%" src="CG/games101/16.jpg"/></center>
<center>Scale Matrix</center>
<br>
<center><img width="30%" src="CG/games101/17.jpg"/></center>
<center>Reflect Matrix</center>
<br>
<center><img width="30%" src="CG/games101/20.jpg"/></center>
<center>Rotate Matrix</center>
<br>
<center><img width="30%" src="CG/games101/18.jpg"/></center>
<center>Shear Matrix</center>

- Hints for shear:
	- Horizontal shift is 0 at y=0
	- Horizontal shift isa at y=1
	- Vertical shift is always 0
	
<center><img width="60%" src="CG/games101/19.jpg"/></center>
<center>Shear</center>

- Affine Transformations
<center><img width="60%" src="CG/games101/23.jpg"/></center>

- Homogeneous Coordinates
	- Translation cannot be represented in matrix form
	(translation is not linear transform)
	- But we don't want translation to be a special case
	
<center><img width="60%" src="CG/games101/21.jpg"/></center>
<br>
<center><img width="60%" src="CG/games101/22.jpg"/></center>

```*Hint: pointA + pointB = (pointA + pointB) / 2, because the w is 2```

<center><img width="60%" src="CG/games101/24.jpg"/></center>
<br>
<center><img width="60%" src="CG/games101/25.jpg"/></center>
<br>
<center><img width="60%" src="CG/games101/26.jpg"/></center>


### 3D Transformation

<center><img width="60%" src="CG/games101/27.jpg"/></center>
<br>
<center><img width="40%" src="CG/games101/28.png"/></center>
<center>Rotation around x,y or z axis</center>

```
*NOTE:
绕y轴旋转为何在符号上与其他两轴相反：
X×Y=Z，Y×Z=X，但X×Z=-Y，Z×X=Y，因此相反
```
<br>
<center><img width="60%" src="CG/games101/29.png"/></center>
<br>
<center><img width="60%" src="CG/games101/30.png"/></center>

```
*NOTE: 绕任意轴旋转为一个包含7步基本变换的级联变换：
1、将轴起始点移动到原点
2、旋转轴使其落入XOZ平面
3、旋转轴使其与z轴重合
4、执行对象绕z轴的θ角度旋转
5、还原轴向与轴点

R(θ)=T(-x,-y,-z)·Rx(a)·Ry(b)·Rz(θ)·Ry(-b)·Rx(-a)·T(x,y,z)
```

## Projection
### Orthographic Projection

<center><img width="80%" src="CG/games101/31.png"/></center>
<br>
<center><img width="80%" src="CG/games101/32.png"/></center>
<br>
<center><img width="60%" src="CG/games101/33.png"/></center>

### Perspective Projection
- Recall: property of homogeneous coordinates
	- (x, y,Z, 1), (kx, ky, kz, k!= 0), (xz, yz, z2,z != 0) all represent the same point (X, y, z) in 3D
	- e.g.(1,0, 0, 1) and (2, 0, 0, 2) both represent (1,0, 0)
	
<center><img width="80%" src="CG/games101/34.jpg"/></center>
<br>
<center><img width="80%" src="CG/games101/35.jpg"/></center>
<br>
<center><img width="80%" src="CG/games101/36.jpg"/></center>
<br>
<center><img width="80%" src="CG/games101/37.jpg"/></center>
<br>
<center><img width="80%" src="CG/games101/38.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/39.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/40.jpg"/></center>

```
*NOTE:
近平面与远平面处的点在变换中被挤压后其深度值保持不变，
但中间位置的点深度值会变大（向远平面方向移动）
例如，原深度为(n+f)/2，变换后则为n/2+f^2/2n，大于原深度
```


## Rasterization
### Drawing to Raster Displays
<br>
<center><img width="70%" src="CG/games101/41.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/42.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/43.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/44.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/45.jpg"/></center>
<center><img width="70%" src="CG/games101/46.jpg"/></center>
<center>Canonical Cube to Screen</center>
<br>
<center><img width="70%" src="CG/games101/48.jpg"/></center>
<center><img width="50%" src="CG/games101/47.jpg"/></center>
<center>Raster Display CRT (Television)</center>
<center>CRT:阴极射线管</center>
<br>
<center><img width="70%" src="CG/games101/49.jpg"/></center>
<center>Frame Buffer: Memory for a Raster Display</center>
<br>
<center><img width="70%" src="CG/games101/50.jpg"/></center>
<center>Flat Panel Displays</center>
<br>
<center><img width="70%" src="CG/games101/51.jpg"/></center>
<center>LCD(Liquid Crystal Display)Pixel:液晶显示器</center>

- 液晶会通过自己的不同排布影响光的极化（偏振方向）

<center><img width="70%" src="CG/games101/52.jpg"/></center>
<center>LED Array Display:发光二极管</center>
<br>
<center><img width="70%" src="CG/games101/53.jpg"/></center>
<center>Electrophoretic (Electronic Ink) Display:电子墨水屏</center>

- 墨水屏的缺陷：刷新率很低

<br>
<center><img width="70%" src="CG/games101/55.jpg"/></center>
<center>Real LCD Screen Pixels (Closeup)</center>
<br>
<center><img width="70%" src="CG/games101/56.jpg"/></center>
<center>Aside: What About Other Display Methods?</center>

<br>

- Triangles - Fundamental Shape Primitives

<center><img width="70%" src="CG/games101/54.jpg"/></center>


### Antialiasing
- Sampling theory
	- Sampling is Ubiquitous(无处不在的) in Computer Graphics

<center><img width="50%" src="CG/games101/57.jpg"/></center>
<center>Recap（回顾）: Testing in/out△at pixels' centers</center>

- Artifacts due to sampling -“Aliasing
	- Jaggies（锯齿） - sampling in space
	- Moire（摩尔纹） - undersampling images
	- Wagon((铁路)货车车厢，车皮) wheel effect（车轮效应） - sampling in time
	- [Many more]

- Behind the Aliasing Artifacts
	- Signals are changing too fast (high frequency), but sampled too slowly

- Antialiasing in practice
	- Antialiasing Idea: 
		- Blurring (Pre-Filtering) Before Sampling

<center><img width="60%" src="CG/games101/58.jpg"/></center>
<br>
<center><img width="60%" src="CG/games101/59.jpg"/></center>
<center>滤波和采用的顺序</center>

1. Why undersampling introduces aliasing?
2. Why pre-filtering then sampling can do antialiasing?<br>
Let's dig into fundamental reasons<br>
And look at how to implement antialiased rasterization

- Frequency Domain (频域)
	- 将函数描述成很多正弦、余弦项的和
<center><img width="70%" src="CG/games101/60.jpg"/></center>
<center>Fourier Transform</center>
<br>
<center><img width="70%" src="CG/games101/61.jpg"/></center>
<center>Fourier Tiransform Decomposes A Signal Into Frequencies</center>

<center><img width="70%" src="CG/games101/62.jpg"/></center>
<center>Higher Frequencies Need Faster Sampling</center>

- Filtering = Getting rid of certain trequency contents
- Filtering = Convolution (= Averaging)

<center><img width="70%" src="CG/games101/63.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/64.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/65.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/66.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/67.jpg"/></center>

- Convolution in the spatial domain is equal to multiplication in the frequency domain, and vice versa
	- Option 1:
		- Filter by convolution in the spatial domain
	- Option 2:
		- Transform to frequency domain (Fourier transform)
		- Multiply by Fourier transform of convolution kernel 
		- Transform back to spatial domain (inverse Fourier)
		
<center><img width="70%" src="CG/games101/68.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/69.jpg"/></center>
<center>Box Funiction = "Low Pass" Filter</center>
<br>
<center><img width="70%" src="CG/games101/70.jpg"/></center>
<center>Wider Filter Kernel = Lower Frequencies</center>

- Sampling = Repeating Frequency Contents (重复频域上的内容)

<center><img width="70%" src="CG/games101/71.jpg"/></center>

<strong>How Can We Reduce Aliasing Error?</strong>
- Option 1: Increase sampling rate
	- Essentially increasing the distance between replicas in the Fourier domain
	- Higher resolution displays, sensors, framebuffers...
	- But: costly & may need very high resolution
- Option 2: Antialiasing
	- Making Fourier contents "narrower" before repeating
	- i.e. Filtering out high frequencies before sampling
	
<center><img width="70%" src="CG/games101/72.jpg"/></center>
<center>Antialiasing = Limiting, then repeating</center>
<br>
<center><img width="70%" src="CG/games101/73.jpg"/></center>

<strong>Antialiasing By Averaging Values in Pixel Area</strong>
- Solution:
	- Convolve f(x,y) by a 1-pixel box-blur
	- Recall: convolving = filtering = averaging
	- Then sample at every pixel's center
	
<center><img width="70%" src="CG/games101/74.jpg"/></center>

<strong>Antialiasing By Supersampling(MSAA)</strong>

<center><img width="70%" src="CG/games101/75.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/76.jpg"/></center>
<center>Point Sampling: One Sample Per Pixel</center>
Supersarmpling: Step 1
<center><img width="70%" src="CG/games101/77.jpg"/></center>
Supersarmpling: Step 2
<center><img width="70%" src="CG/games101/78.jpg"/></center>
<center><img width="70%" src="CG/games101/79.jpg"/></center>
Supersampling: Result
<center><img width="70%" src="CG/games101/80.jpg"/></center>

<strong>No free lunch!</strong>
- What's the cost of MSAA?
- Milestones (personal idea)
	- FXAA (Fast Approximate AA)
	- TAA (Temporal AA)

- <strong>FXAA</strong>
得到带锯齿的图，通过图像匹配方法找到边界，模糊锯齿边界

- <strong>TAA</strong>
时空间上进行处理，每一帧采样时，采样像素内部不同位置的颜色值，然后复用前面的帧求平均<br>
也就是将MSAA的采样转移到了时间序列上，减少额外开销

- Super resolution / super sampling (超分辨率)
	- From low resolution to high resolution
	- Essentially still "not enough samples" problem
	- DLSS (Deep Learning Super Sampling)


### Visibility/occlusion
- Painter's Algorithm
- Z-buffering
	- Z-buffering is the algorithm that eventually won.
	- Idea:
		- Store current min. z-value for each sample (pixel)
		- Needs an additional buffer for depth values
			- frame buffer stores color values
			- depth buffer (z-buffer) stores depth
	- IMPORTANT: For simplicity we suppose Z is always positive (smaller z -> closer, larger z -> further)
	- Complexity
		- O(n) for n triangles (assuming constant coverage)
		- How is it possible to sort n triangles in linear time?
			- Drawing triangles in different orders?
			- Most important visibility algorithm
		- Implemented in hardware for all GPUs

<center><img width="70%" src="CG/games101/81.jpg"/></center>
<center>Painter's Algorithm</center>
<br>
<center><img width="70%" src="CG/games101/83.jpg"/></center>
<center>Problem of the Painter's Algorithm</center>
<br>
<center><img width="70%" src="CG/games101/82.jpg"/></center>
<center>Z-buffering</center>



## Shading
### Diffuse
<center><img width="70%" src="CG/games101/84.jpg"/></center>
<center>Diffuse Reflection</center>
<br>
<center><img width="50%" src="CG/games101/85.jpg"/></center>
<center>Light Falloff</center>
<br>
<center><img width="70%" src="CG/games101/86.jpg"/></center>
<center>Lambertian (Diffuse) Shading</center>
<br>
<center><img width="70%" src="CG/games101/87.jpg"/></center>

### Specular
<center><img width="70%" src="CG/games101/88.jpg"/></center>
<center>Specular Term (Blinn-Phong)</center>
<center><img width="70%" src="CG/games101/89.jpg"/></center>
<center>Blinn-Phong Model</center>

### Ambient
<center><img width="70%" src="CG/games101/90.jpg"/></center>
<center>Ambient Term</center>

### Composite
<center><img width="70%" src="CG/games101/91.jpg"/></center>
<center>Blinn-Phong Reflection Model</center>

### Shading Frequency
<center><img width="70%" src="CG/games101/92.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/93.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/94.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/95.jpg"/></center>

- Shading Frequency: Face, Vertex or Pixel

<center><img width="70%" src="CG/games101/96.jpg"/></center>

### Graphics Pipeline
<center><img width="70%" src="CG/games101/98.jpg"/></center>

## Interpolation
- Why do we want to interpolate?
	- Specify values at vertices
	- Obtain smoothly varying values across triangles
- What do we want to interpolate?
	- Texture coordinates, colors, normal vectors, ...
<center><img width="70%" src="CG/games101/97.jpg"/></center>

### Barycentric Coordinates
- Interpolation Across Triangles: Barycentric Coordinates (重心坐标插值)

<center><img width="70%" src="CG/games101/99.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/100.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/102.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/101.jpg"/></center>
<center>Formulas</center>

```
*NOTE:
- 重心坐标插值没有投影不变性
- 投影变换后直接插值会得到不一样的结果
(需要在三维空间下插值时就需要用三维空间坐标，不能用投影后的坐标)
```

<center><img width="70%" src="CG/games101/103.jpg"/></center>
<center>Simple Texture Mapping: Diffuse Color</center>


### Texture Magnification
- texture is too small

<center><img width="70%" src="CG/games101/104.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/105.jpg"/></center>

- 双线性插值（水平和竖直方向都插值，做两次插值）
- 先水平和先竖直结果是一样的

<center><img width="70%" src="CG/games101/106.jpg"/></center>
<center><img width="70%" src="CG/games101/107.jpg"/></center>
<center><img width="70%" src="CG/games101/108.jpg"/></center>
<center><img width="70%" src="CG/games101/109.jpg"/></center>
<center>Bilinear Interpolation</center>

### Texture Zooming-out
- texture is too large

<center><img width="70%" src="CG/games101/110.jpg"/></center>
<center>Problem of Point Sampling</center>
<br>
<center><img width="70%" src="CG/games101/111.jpg"/></center>

- Will supersampling work?
	- Yes, high quality, but costly
	- When highly minified, many texels in pixel footprint
	- Signal frequency too large in a pixel
	- Need even higher sampling frequency

<center><img width="70%" src="CG/games101/112.jpg"/></center>

- Let's understand this problem in another way
	- What if we don't sample?
	- Just need to get the average value within a range!

- Mipmap
	- Allowing (fast, approx., square) range queries
	
<center><img width="70%" src="CG/games101/113.jpg"/></center>
<center>Mlipmap (L. Williams 83)</center>

<center><img width="50%" src="CG/games101/114.jpg"/></center>

- What is the storage overhead of a mipmap?
```*NOTE:Mipmap所有低分辨率纹理的存储空间之和为原图的1/3```

- Estimate texture footprint using texture coordinates of neighboring screen samples

<center><img width="70%" src="CG/games101/115.jpg"/></center>
<center><img width="70%" src="CG/games101/116.jpg"/></center>
<center>Computing Mipmap Level D</center>
<center><img width="70%" src="CG/games101/117.jpg"/></center>
<center>Visuaiization of Mipmap Level</center>

- Trilinear Interpolation (三线性插值)
	- 对Mipmap采样时，若采样点在两层之间
	- 两层各做双线性插值，层之间再对插值结果线性插值

<center><img width="70%" src="CG/games101/118.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/119.jpg"/></center>
<center>Visuaiization of Mipmap Level</center>
<br>
<center><img width="50%" src="CG/games101/120.jpg"/></center>

- Mipmap Limitations
	- Overblur, and Why?

<center><img width="50%" src="CG/games101/121.jpg"/></center>
<center>Anisotropic Filtering (各向异性过滤)</center>

- 各向异性过滤能够解决部分问题
- 可以对长条形区域做快速查询（屏幕空间方形映射到贴图为长条形的情况）
- Ripmaps and summed area tables
	- Can look up axis-aligned
- rectangular zones
	- Diagonal footprints still a problem

<center><img width="30%" src="CG/games101/122.jpg"/></center>
<center>各向异性过滤预计算，比Mipmap多了一些区域</center>
<br>
<center><img width="70%" src="CG/games101/123.jpg"/></center>
<center>Irregular Pixel Footprint in Texture</center>

- 但各向异性过滤仍有限制
	- 对于斜着的长条状映射区域，效果依然不好
	
<center><img width="70%" src="CG/games101/124.jpg"/></center>
<center>解决方案之一，但需多次查询，耗时</center>


## Geometry
### Explicit Representations
<center><img width="70%" src="CG/games101/125.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/126.jpg"/></center>
<center>Polygone Mesh (Explicit)</center>
<br>
<center><img width="70%" src="CG/games101/127.jpg"/></center>
<center>The Wavefront Object File (.obj) Format</center>

### Curves
#### Bezier Curve
- Evaluating Bezier Curves (de Casteljau Algorithm)

<center><img width="60%" src="CG/games101/128.jpg"/></center>
<br>
<center><img width="60%" src="CG/games101/129.jpg"/></center>
<br>
<center><img width="60%" src="CG/games101/130.jpg"/></center>
<br>
<center><img width="60%" src="CG/games101/131.jpg"/></center>
<br>
<center><img width="60%" src="CG/games101/132.jpg"/></center>

- Evaluating Bezier Curves, Algebraic Formula

<center><img width="70%" src="CG/games101/133.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/134.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/135.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/136.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/137.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/138.jpg"/></center>

	- Beizer Curve具有仿射不变性
	- Bezier Curve一定在其控制点构成的凸包内

- Piecewise Bezier Curve (分段Bezier曲线)

<center><img width="70%" src="CG/games101/139.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/140.jpg"/></center>
<br>
<center><img width="70%" src="CG/games101/141.jpg"/></center>

- C0连续性：曲线端点值相等
- C1连续性：曲线交点处一阶导相等（切线相同）
- C2连续性：曲线交点处一阶、二阶导相等

- B-splines
	- Short for basis splines
		- Require more information than Bezier curves
	- Satisfy all important properties that Bezier curves have (i.e. superset)











