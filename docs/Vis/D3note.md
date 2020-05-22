# D3 Note

D3.js 学习笔记

## 在项目中使用D3.js

学习D3.js涉及的知识点：
- HTML——超文本标记语言，用于设计网页内容
- CSS——层叠样式表，用于设计网页样式
- JavaScript——一种脚本语言，用于设计网页行为
- SVG——可放缩矢量图形，用于绘制可视化图形

官方API：http://d3js.org/

在代码中使用D3.js：
```
<head>
	<script type="text/javascript" src="http://d3js.org/d3.v5.min.js">
	</script>
</head>
```
在head标签中引入d3.js即可





## Hello World D3.js

第一个D3程序：<br>
利用D3.js在网页上显示一个Hello World文本
```
<body>
    <p></p>
    <p></p>
    <script>
        var p = d3.select("body").selectAll("p");
        p.text("Hello World");
    </script>
</body>
```

运行结果：<br>
Hello World<br>
Hello World

- ```上面的程序先在<body>标签中加入了两个<p>标签，当时没有写内容，然后再在<script>中动态生成Hello World;```
- ```.selectAll("p");这是D3中的选择集，从字面上的意思就是先选择<body>这个标签，然后在<body>标签中选择所有的<p>标签;```
- ```p.text("Hello World") 是为（所有）选中的<p>标签添上文字，因此运行结果就显示了两个Hello World.```





## 选择元素和绑定数据
### 选择元素
在D3.js中，选择元素的函数有两个：
- d3.select() 
- d3.selectAll()

这两个函数返回的是选择集，常见用法：
- var body = d3.select("body");//选择文档中的body元素
- var svg = body.select("svg");//选择body中的svg元素
- var p = body.selectAll("p"); //选择body中所有的p元素
- var p1 = body.select("p");   //选择body中第一个p元素

### 绑定数据
D3.js能将数据绑定到 DOM 上，也就是绑定到文档上。例如，如果网页中有一个P元素和一个整数5，我们可以将数据5和p绑定在一起。

D3.js中绑定数据的两个函数：
- data()：将一个数组绑定到选择集上，数组各项和选择集各元素绑定，也就是一一对应的关系
- datum()：将一个数据绑定到所有选择集上

datum()的使用:
```
<body>
    <p>dog</p>
    <p>cat</p>
    <p>pig</p>

    <script>
        var str = "is an animal";//新建一个字符串
    	var p = d3.select("body").selectAll("p");

    	p.datum(str).text(function (d, i) { //绑定
    		return "第"+i+"个元素"+d;
    	});
    </script>
</body>
```

运行结果：<br>
第0个元素is an animal<br>
第1个元素is an animal<br>
第2个元素is an animal

- ```本段代码的作用是将str这个字符串绑定到三个<p>选择集上，然后通过一个无名函数function(d,i)，访问到绑定的元素。```
- ```function(d,i)，其中d代表数据，也就是与某元素绑定的数据，i代表索引，代表数据的索引，从0开始```

data()的使用:
```
<body>
    <p>dog</p>
    <p>cat</p>
    <p>pig</p>

    <script>
        var dataset = ["so cute", "cute", "fat"];
    	var p = d3.select("body").selectAll("p");

    	p.data(dataset).text(function(d,i){
    		return "第"+i+"个动物"+d;
    	});
    </script>
</body>
```

运行结果：<br>
第0个动物so cute<br>
第1个动物cute<br>
第2个动物fat

- ```data()和datum()大体一样，只不过是数组元素和选择集有着对应关系，也更为常用```





## Update、Enter、Exit
- 在使用data()时，例如有一个数组[3,6,9,12,15],可以将数组每一项与一个```<p>```绑定
- 但数据集个数和选择集个数不匹配时，就需要Update、Enter、Exit


<center><img width="60%" src="Vis/d3pics/1.jpg"/></center>

update和enter (上左图)：
```
数组[3,6,9,12,15]绑定到三个<p>上。数组的最后两个数没有可以绑定的元素
这时D3会建立两个空的元素与数组最后的两个数据相对，这部分就称为Enter
而有元素与数据对应的部分就称为Update
```

exit (上右图)：
```
数组[3]绑定到三个<p>上，最后两个<p>没有可绑定的数据，那么没有数据绑定的部分就称为Exit
```

Update与Enter的使用：
```
<body>
    <p>dog</p>
    <p>cat</p>
    <p>pig</p>
    
    <script>
    	var dataset = [3,6,9,12,15];
    	var p = d3.select("body").selectAll("p");
    	var update = p.data(dataset)//绑定数据,并得到update部分
    	var enter = update.enter();//得到enter部分
    	//update的处理
    	update.text(function(d,i){
    		return "update: "+d+",index: "+i;
    	})
    	//enter的处理
    	//这里需要先添加足够多的<p>，然后添加文本
    	var pEnter = enter.append("p")//添加足够多的<p>
    	pEnter.text(function(d,i){
    		return "enter: "+d+",index: "+i;
    	})
    </script>
</body>
```

运行结果：<br>
update: 3,index: 0<br>
update: 6,index: 1<br>
update: 9,index: 2<br>
enter: 12,index: 3<br>
enter: 15,index: 4


Update与Exit的使用：
```
<body>
    <p>dog</p>
    <p>cat</p>
    <p>pig</p>
    <p>rat</p>

    <script>
        var dataset = [3, 6];
    	var p = d3.select("body").selectAll("p");
    	var update = p.data(dataset)//绑定数据,得到update部分
    	var exit = update.exit();//得到exit部分
    	//update的处理
    	update.text(function(d,i){
    		return "update: "+d+",index: "+i;
    	})
    	//对于exit的处理通常是删除 ，但这里并没有这么做
    	exit.text(function(d,i){
    		return "exit";
    	})
    </script>
</body>
```

运行结果：<br>
update: 3,index: 0<br>
update: 6,index: 1<br>
exit<br>
exit

- ```在得到exit部分后，不需要使用append("xx")来添加元素，而enter需要```
- ```对于exit部分的处理通常是删除exit.remove();```





## 元素增删改查
### 选择元素
设body中有四个元素：
```
	<p>dog</p>
    <p>cat</p>
    <p>pig</p>
    <p>rat</p>
```

选择第一个元素```<p>```：
```
<script>
	var p = d3.select("body").select("p");
    p.style("color","red")
</script>
```

运行结果：<br>
<font color="#FF0000">dog</font><br>
cat<br>
pig<br>
rat

选择全部元素：
```
<script>
	var p = d3.select("body").selectAll("p");
	p.style("color","red");
</script>
```

运行结果：<br>
<font color="#FF0000">dog</font><br>
<font color="#FF0000">cat</font><br>
<font color="#FF0000">pig</font><br>
<font color="#FF0000">rat</font>

选择任意元素（根据属性选择）：
```
<script>
	// 设定元素属性，注意访问时需要加点和#，如：.myP2 #myP3
	<p>dog</p>
    <p class="myP2">cat</p>
    <p id="myP3">pig</p>
    <p>rat</p>
</script>
```
```
<script>
	// 根据class属性来选择特定的元素，id属性用法类似
	var p = d3.select("body").selectAll(".myP2");
	p.style("color","red");
</script>
```

运行结果：<br>
dog<br>
<font color="#FF0000">cat</font><br>
pig<br>
rat

选择任意元素（根据ID选择）：
```
	// 如果知道元素索引号，那么可以利用条件语句来选择我们需要的元素
	var dataset = [3,6,9,12];
    var p = d3.select("body").selectAll("p").data(dataset).text(function(d,i){
    	if(i==3){
    		d3.select(this).style("color","red");
    	}
    	return d;
    })
```

运行结果：<br>
3<br>
6<br>
9<br>
<font color="#FF0000">12</font><br>

### 插入元素
D3.js中有两种插入函数
- append()：在选择集尾部插入元素
- insert()：在选择集前面插入元素    

append()：
```
<script>
	// 先选择<body>元素，然后在其内部的最后添加一个新的<p>
	var p = d3.select("body")
    		.append("p")
    		.text("another animal")
    		.style("color","red");
</script>
```

运行结果：<br>
dog<br>
cat<br>
pig<br>
rat<br>
<font color="#FF0000">another animal</font>

insert()：
```
<script>
	var p = d3.select("body")
    		.insert("p","#myP3")
    		.text("insert an animal")
    		.style("color","red");
</script>
```

运行结果：<br>
dog<br>
cat<br>
<font color="#FF0000">insert an animal</font><br>
pig<br>
rat

- ```.insert("p","#myP3")表示在属性id为myP3的元素前面插入一个新的元素<p>```

### 删除元素
使用remove();即可：
```
<script>
	var p = d3.select("body")
    		.select("#myP3")
    		.remove();
</script>
```
删除了属性id为myP3的元素





## 第一个简单图表
图表绘制涉及的知识点：
- svg画布：svg绘制的是矢量图（还有canvas画布，JavaScript用来绘制2D图像的，是位图）
- rect元素：是d3中在svg中绘制矩形的元素
- g元素：分组的时候使用

### 画一个柱状图
```
	<body>
        <svg width="960" height="600"></svg>
        <script>
            // 准备数据
            var marge = { top: 60, bottom: 60, left: 60, right: 60 }//设置边距
            var dataset = [250, 210, 170, 130, 90];  //数据（表示矩形的宽度）

            //获取svg画布
            var svg = d3.select("svg");
            //定义一个用来装整个图表的分组，并设置他的位置
            var g = svg.append("g").attr("transform", "translate(" + marge.top + "," + marge.left + ")");

            //画矩形
            var rectHeight = 30;//设置每一个矩形的高度
            g.selectAll("rect")
    		    .data(dataset)
    		    .enter()
    		    .append("rect")
    		    .attr("x",20)//设置左上点的x
    		    .attr("y",function(d,i){//设置左上点的y
    		        return i*rectHeight;
    		    })
    		    .attr("width",function(d){//设置宽
    		        return d;
    		    })
    		    .attr("height",rectHeight-5)//设置长
    		    .attr("fill","blue");//颜色填充
        </script>
    </body>
```
- 其中.attr(xxxx)是用来设置属性的，而“transform”是用来设置位置
- 注意："translate("+marge.top+","+marge.left+")" 本质上是一个字符串，因为其中有变量，所以使用字符串拼接
-  .append("rect") 表示添加足够的rect元素（也就是enter的用法）

运行结果：
<iframe src="Vis/d3demo/d1.html" onload="this.before((this.contentDocument.body||this.contentDocument).children[0]);this.remove()"></iframe>





## 比例尺
比例尺在D3.js中是很重要的，可以这样理解d3.js中的比例尺：<br>
一种映射关系，从domain映射到range域

### 线性比例尺
线性比例尺指domain域和range域都可以连续变化：
```
<body>
    <script>
    	var dataset = [1.2, 2.3, 0.9, 1.5, 3.3];
    	var min = d3.min(dataset);//得到最小值
    	var max = d3.max(dataset);//得到最大值
    	var scaleLinear = d3.scaleLinear()
    						.domain([min,max])
    						.range([0,300]);
    	document.write("scaleLinear(1)输出："+scaleLinear(1));
    	d3.select("body").append("br");//换行
    	document.write("scaleLinear(2)输出："+scaleLinear(2));
    	d3.select("body").append("br");
    	document.write("scaleLinear(3.3)输出："+scaleLinear(3.3));
    </script>
</body>
```

运行结果：<br>
scaleLinear(1)输出：12.499999999999996<br>
scaleLinear(2)输出：137.5<br>
scaleLinear(3.3)输出：300

- ```.range([0,300]); 也就是[0.9,3.3]从映射到[0,300]```
- ```scaleLinear(3.3)，由映射关系可以知道，这里的输出为300```


### 序数比例尺
 序数比例尺指domain域和range域是离散的，也就是数组
 ```
<body>
    <script>
    	var index = [0,1,2,3,4];
    	var color = ["red","blue","yellow","black","green"];
    	var scaleOrdinal = d3.scaleOrdinal()
    						 .domain(index)
    						 .range(color);
    	document.write("scaleOrdinal(1)输出："+scaleOrdinal(1));
    	d3.select("body").append("br");//换行
    	document.write("scaleOrdinal(2)输出："+scaleOrdinal(2));
    	d3.select("body").append("br");
    	document.write("scaleOrdinal(4)输出："+scaleOrdinal(4));
    </script>
</body>
 ```

运行结果：<br>
scaleOrdinal(1)输出：blue<br>
scaleOrdinal(2)输出：yellow<br>
scaleOrdinal(4)输出：green

- ```.range(color); 建立一个序数比例尺```

### 用比例尺改进柱状图
```
<body>
    <svg width="200" height="600"></svg>
    <script>
    	var marge = {top:60,bottom:60,left:60,right:60}
    	var dataset = [ 2.5 , 2.1 , 1.7 , 1.3 , 0.9 ];  
    	
    	//定义一个线性比例尺
    	var scaleLinear = d3.scaleLinear()
    		.domain([0,d3.max(dataset)])
    		.range([0,300]);
    	
    	var svg = d3.select("svg");
    	var g = svg.append("g")
    		.attr("transform","translate("+marge.top+","+marge.left+")");
    	
    	var rectHeight = 30;
    	
    	g.selectAll("rect")
    		.data(dataset)
    		.enter()
    		.append("rect")
    		.attr("x",20)
    		.attr("y",function(d,i){
    			return i*rectHeight;
    		})
    		.attr("width",function(d){
    			return scaleLinear(d);//设置宽,并在这里使用比例尺
    		})
    		.attr("height",rectHeight-5)
    		.attr("fill","blue");
    </script>
</body>
```





## 建立坐标轴
- D3中没有现成的坐标轴图形，需要自己用其他组件拼凑而成。
- D3中提供了坐标轴组件，使得在SVG中绘制一个坐标轴变得像添加一个普通元素那样简单

坐标轴绘制涉及的知识点：
- call()函数

### 定义一个坐标轴
坐标轴是有朝向的，下面建立一个向下朝向、水平方向的坐标轴为例，其他朝向的（比如向左朝向的、垂直的坐标轴）类似：
```
<script>
	//为坐标轴定义一个线性比例尺
    var xScale = d3.scaleLinear()
    			   .domain([0,d3.max(dataset)])
    			   .range([0,250]);
    //定义一个坐标轴
    var xAxis = d3.axisBottom(xScale)//定义一个axis，由bottom可知，是朝下的
    			  .ticks(7);//设置刻度数目
    g.append("g").attr("transform","translate("+20+","+(dataset.length*rectHeight)+")")
    			 .call(xAxis);
</script>
```

- ```.attr(...)是设置位置信息的```
- ```call(xAxis)：xAxis是我们定义的一个坐标轴，它本身也是一个函数，这句话将新建的分组<g>传给xAxis()函数，用以绘制```
```上面这句话等价于：xAixs (g.append("g"));```

### 为柱状图添加坐标轴
一个完整的柱状图应该包括的元素有—矩形、文字、坐标轴，涉及的新知识点：
- d3.scaleBand()：这也是一个坐标轴，可以根据输入的domain的长度，等分rangeRound域（类比range域）
- d3.range()：可以返回一个等差数列

```
	<body>
        <svg width="800" height="600"></svg>
        <script>
    	    var marge = {top:60,bottom:60,left:60,right:60}
    	    var svg = d3.select("svg");//得到SVG画布
    	    var width = svg.attr("width");//得到画布的宽
    	    var height = svg.attr("height");//得到画布的长
    	    var g = svg.append("g").attr("transform","translate("+marge.top+","+marge.left+")");
    	
    	    var dataset = [10,20,30,23,13,40,27,35,20];
   
    	    var xScale = d3.scaleBand()
    					   .domain(d3.range(dataset.length))
    					   .rangeRound([0,width-marge.left-marge.right]);
    	    var xAxis = d3.axisBottom(xScale);
    		
    	    var yScale = d3.scaleLinear()
    					   .domain([0,d3.max(dataset)])
    					   .range([height-marge.top-marge.bottom,0]);
    	    var yAxis = d3.axisLeft(yScale);
    	
    	    g.append("g").attr("transform","translate("+0+","+(height-marge.top-marge.bottom)+")").call(xAxis);
    	    g.append("g").attr("transform","translate(0,0)").call(yAxis);
    		
    	    //绘制矩形和文字
    	    var gs = g.selectAll(".rect").data(dataset).enter().append("g");
    	
    	    //绘制矩形
    	    var rectPadding = 20;//矩形之间的间隙
    	    gs.append("rect")
    		    .attr("x",function(d,i){ return xScale(i)+rectPadding/2; })	
    		    .attr("y",function(d){ return yScale(d); })
    		    .attr("width",function(){ return xScale.step()-rectPadding; })
    		    .attr("height",function(d){ return height-marge.top-marge.bottom-yScale(d); })
    		    .attr("fill", "blue");

    	    //绘制文字
    	    gs.append("text")
    		    .attr("x",function(d,i){ return xScale(i)+rectPadding/2; })
    		    .attr("y",function(d){ return yScale(d); })
        	    .attr("dx",function(){ (xScale.step()-rectPadding)/2; })
        	    .attr("dy",20)
        	    .text(function(d){ return d; })
        </script>
    </body>
```

### 运行结果
<iframe src="Vis/d3demo/d2.html" onload="this.before((this.contentDocument.body||this.contentDocument).children[0]);this.remove()"></iframe>






## 动态效果
制作动态效果需要以下新的知识点：
- .attr(xxx) .transition() .attr(xxx)，transition()表示添加过渡，也就是从前一个属性过渡到后一个属性
- .duration(2000)，表示过渡时间持续2秒
- .delay(500)，表示延迟0.4秒后再进行过渡
- .ease(d3.easeElasticInOut)表示过渡方式，这里和v3版本有区别

### 矩形过渡效果
```
	<script>
		gs.append("rect")
    	.attr("x",function(d,i){
    		return xScale(i)+rectPadding/2;
    	})	
    	.attr("y",function(d){//这里是要改变的，即初始状态
    		var min = yScale.domain()[0];
    		return yScale(min);//这里返回的是最大值
    	})
    	.attr("width",function(){
    		return xScale.step()-rectPadding;
    	})
    	.attr("height",function(d){//这里要改变，即初始状态
    		return 0;
    	})
    	.attr("fill","blue")
    	.transition()//添加过渡
    	.duration(2000)//持续时间
    	.delay(function(d,i){//延迟
    		return i*400;
    	})
    	.attr("y",function(d){//回到最终状态
    		return yScale(d);
    	})
    	.attr("height",function(d){//回到最终状态
    		return height-marge.top-marge.bottom-yScale(d);
    	})
	</script>
```

### 文字过渡效果
```
	<script>
		gs.append("text")
    	.attr("x",function(d,i){
    		return xScale(i)+rectPadding/2;
    	})
    	.attr("y",function(d){
           	var min = yScale.domain()[0];
    		return yScale(min);
        })
        .attr("dx",function(){
        	(xScale.step()-rectPadding)/2;
        })
        .attr("dy",20)
        .text(function(d){
        	return d;
        })
        .transition()
    	.duration(2000)
    	.delay(function(d,i){
    		return i*400;
    	})
        .attr("y",function(d){
    		return yScale(d);
    	});
	</script>
```

### 运行结果
<iframe src="Vis/d3demo/d3.html" scrolling="no" frameborder="0" height="300" width="100%"></iframe>





## 用户交互
所谓的交互操作也就是为图形元素添加监听事件，为了与图形元素进行交互操作，需要以下新的知识点：
- on("eventName",function)；该函数是添加一个监听事件，它的第一个参数是事件类型，第二个参数是响应事件的内容
- d3.select(this),选择当前元素

### 常见的事件类型
- click：鼠标单击某元素时触发，相当于mousedown和mouseup的组合
- mouseover：鼠标放在某元素上触发
- mouseout：鼠标移出某元素时触发
- mousemove：鼠标移动时触发
- mousedown：鼠标按钮被按下时触发
- mouseup：鼠标按钮被松开时触发
- dblclick：鼠标双击时触发

### 查看监听事件
```
<script>
	.on("click",function(){
    	console.log(d3.event);
    })
</script>
```
可以在chrome浏览器的控制台看到输出的event事件

### 为柱状图添加监听事件
```
<script>
	.on("mouseover",function(){
    	var rect = d3.select(this)
    		.transition()
    		.duration(1500)//当鼠标放在矩形上时，矩形变成黄色
    		.attr("fill","yellow");
    })
    .on("mouseout",function(){
    	var rect = d3.select(this)
    		.transition()
    		.delay(1500)
    		.duration(1500)//当鼠标移出时，矩形变成蓝色
    		.attr("fill","blue");
    })
</script>
```

### 运行结果
<iframe src="Vis/d3demo/d4.html" scrolling="no" frameborder="0" height="300" width="100%"></iframe>







## 物理效果
### 力导向图主要函数
- d3.forceSimulation() ，新建一个力导向图
- d3.forceSimulation().force(),添加或者移除一个力 
- d3.forceSimulation().nodes()，输入是一个数组，然后对这个输入的数组进行一定的数据转换，例如添加坐标什么的
- d3.forceLink.links()，这里输入的也是一个数组（边集），然后对输入的边集进行转换
- tick()，这个函数对于力导向图来说非常重要，因为力导向图是不断运动的，每一时刻都在发生更新，所以需要不断更新节点和连线的位置
- d3.drag(),设置力导向图可以被拖动

```d3.forceSimulation().force(name)，中只有一个参数，这个参数是某个力的名称，返回的是某个具体的力```
```例如d3.forceSimulation().force(“link”)，则返回的是d3.forceLink()这个力```

#### 数据准备
```
	<script>
		var marge = {top:60,bottom:60,left:60,right:60}
    	var svg = d3.select("svg")
    	var width = svg.attr("width")
    	var height = svg.attr("height")
    	var g = svg.append("g")
    		.attr("transform","translate("+marge.top+","+marge.left+")");
    		
    	//准备数据
    	var nodes = [//节点集
    		{name:"湖南邵阳"},
    		{name:"山东莱州"},
    		{name:"广东阳江"},
    		{name:"山东枣庄"},
    		{name:"泽"},
    		{name:"恒"},
    		{name:"鑫"},
    		{name:"明山"},
    		{name:"班长"}
    	];
    	
    	var edges = [//边集
    		{source:0,target:4,relation:"籍贯",value:1.3},
    		{source:4,target:5,relation:"舍友",value:1},
    		{source:4,target:6,relation:"舍友",value:1},
    		{source:4,target:7,relation:"舍友",value:1},
    		{source:1,target:6,relation:"籍贯",value:2},
    		{source:2,target:5,relation:"籍贯",value:0.9},
    		{source:3,target:7,relation:"籍贯",value:1},
    		{source:5,target:6,relation:"同学",value:1.6},
    		{source:6,target:7,relation:"朋友",value:0.7},
    		{source:6,target:8,relation:"职责",value:2}
    	];
	</script>
```

#### 设置颜色比例尺
```
	<script>
		var colorScale = d3.scaleOrdinal()
    		.domain(d3.range(nodes.length))
    		.range(d3.schemeCategory10);
	</script>
```

#### 新建一个力导向图
```
	<script>
		//新建力导向图
		var forceSimulation = d3.forceSimulation()
    		.force("link",d3.forceLink())
    		.force("charge",d3.forceManyBody())
    		.force("center",d3.forceCenter());
		//生成节点数据
    	forceSimulation.nodes(nodes).on("tick",ticked);
		//生成边数据
    	forceSimulation.force("link")
    		.links(edges)
    		.distance(function(d){//每一边的长度
    			return d.value*100;
    		})
		//设置图形的中心位置	
    	forceSimulation.force("center")
    		.x(width/2)
    		.y(height/2);
	</script>
```

#### 绘制边
```
	<script>
		var links = g.append("g")
    		.selectAll("line")
    		.data(edges)
    		.enter()
    		.append("line")
    		.attr("stroke",function(d,i){
    			return colorScale(i);
    		})
    		.attr("stroke-width",1);
	</script>
```

```*注意：应该先绘制边再绘制顶点，在d3中各元素是有层级关系的，先绘制的会被后绘制的遮挡```

#### 添加文字
```
	<script>
		var linksText = g.append("g")
    		.selectAll("text")
    		.data(edges)
    		.enter()
    		.append("text")
    		.text(function(d){
    			return d.relation;
    		})
		var gs = g.selectAll(".circleText")
    		.data(nodes)
    		.enter()
    		.append("g")
    		.attr("transform",function(d,i){
    			var cirX = d.x;
    			var cirY = d.y;
    			return "translate("+cirX+","+cirY+")";
    		})
    		.call(d3.drag()
    			.on("start",started)
    			.on("drag",dragged)
    			.on("end",ended)
    		);
	</script>
```

#### 绘制节点和文字
```
	<script>
		//绘制节点
    	gs.append("circle")
    		.attr("r",10)
    		.attr("fill",function(d,i){
    			return colorScale(i);
    		})
    	//文字
    	gs.append("text")
    		.attr("x",-10)
    		.attr("y",-20)
    		.attr("dy",10)
    		.text(function(d){
    			return d.name;
    		})
	</script>
```

#### 实现tick函数
```
	<script>
		function ticked(){
    		links.attr("x1",function(d){return d.source.x;})
    			.attr("y1",function(d){return d.source.y;})
    			.attr("x2",function(d){return d.target.x;})
    			.attr("y2",function(d){return d.target.y;});
    			
    		linksText.attr("x",function(d){
    			return (d.source.x+d.target.x)/2;
    		})
    		.attr("y",function(d){
    			return (d.source.y+d.target.y)/2;
    		});
    			
    		gs.attr("transform",function(d) { return "translate(" + d.x + "," + d.y + ")"; });
    	}
	</script>
```

```这里写的都是位置信息，但在绘制相应的图形元素的时候，位置信息就不那么重要了```

#### 实现drag函数
```
	<script>
		function started(d){
    		if(!d3.event.active){
    			forceSimulation.alphaTarget(0.8).restart();设置衰减系数，对节点位置移动过程的模拟，数值越高移动越快，数值范围[0，1]
    		}
    		d.fx = d.x;
    		d.fy = d.y;
    	}
    	function dragged(d){
    		d.fx = d3.event.x;
    		d.fy = d3.event.y;
    	}
    	function ended(d){
    		if(!d3.event.active){
    			forceSimulation.alphaTarget(0);
    		}
    		d.fx = null;
    		d.fy = null;
    	}
	</script>
```

- drag中有三个函数，其中d.fx和d.fy表示固定坐标
- 例如，d.fx = d3.event.x;  d.fy = d3.event.y;
也就是在拖动节点的时候，鼠标位置在哪里（d3.event），节点的固定位置就在哪里
- 再看ended函数，也就是结束拖动的时候触发，可以发现固定坐标都为空（也就是不固定），这样模拟的效果比较好


### 运行结果
<iframe src="Vis/d3demo/d5.html" scrolling="no" frameborder="0" height="400" width="100%"></iframe>