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

