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
