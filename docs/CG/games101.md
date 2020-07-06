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
- Z-buffering





