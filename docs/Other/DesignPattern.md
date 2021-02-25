# Design Pattern

设计模式学习笔记

## 1 什么是设计模式
设计模式（Design pattern）是软件开发人员在软件开发过程中面临的一般问题的解决方案。这些解决方案是众多软件开发人员经过相当长的一段时间的试验和错误总结出来的。

设计模式是一套被反复使用的、多数人知晓的、经过分类编目的、代码设计经验的总结。使用设计模式是为了重用代码、让代码更容易被他人理解、保证代码可靠性。 每种模式都描述了一个在我们周围不断重复发生的问题，以及该问题的核心解决方案，这也是设计模式能被广泛应用的原因。

## 2 设计模式的类型
根据设计模式的参考书 《Design Patterns - Elements of Reusable Object-Oriented Software》中所述，设计模式总共有23种。这些模式可以分为三大类：<strong>创建型模式（Creational Patterns）、结构型模式（Structural Patterns）、行为型模式（Behavioral Patterns）</strong>。除此之外还有一类由Sun Java Center制定的J2EE 模式，这里暂不作详细记录。

<table class="reference notranslate">
<tbody><tr><th style="width:5%;">序号</th><th style="width:45%;">模式 &amp; 描述</th><th>包括</th></tr>
<tr><td>1</td><td><b>创建型模式</b><br>这些设计模式提供了一种在创建对象的同时隐藏创建逻辑的方式，而不是使用 new 运算符直接实例化对象。这使得程序在判断针对某个给定实例需要创建哪些对象时更加灵活。</td>
<td>
<ul>
<li>工厂模式（Factory Pattern）</li>
<li>抽象工厂模式（Abstract Factory Pattern）</li>
<li>单例模式（Singleton Pattern）</li>
<li>建造者模式（Builder Pattern）</li>
<li>原型模式（Prototype Pattern）</li>
</ul>
</td>
</tr>
<tr><td>2</td><td><b>结构型模式</b><br>这些设计模式关注类和对象的组合。继承的概念被用来组合接口和定义组合对象获得新功能的方式。</td>
<td>
<ul>
<li>适配器模式（Adapter Pattern）</li>
<li>桥接模式（Bridge Pattern）</li>
<li>过滤器模式（Filter、Criteria Pattern）</li>
<li>组合模式（Composite Pattern）</li>
<li>装饰器模式（Decorator Pattern）</li>
<li>外观模式（Facade Pattern）</li>
<li>享元模式（Flyweight Pattern）</li>
<li>代理模式（Proxy Pattern）</li>
</ul>
</td>
</tr>
<tr><td>3</td><td><b>行为型模式</b><br>这些设计模式特别关注对象之间的通信。</td>
<td>
<ul>
<li>责任链模式（Chain of Responsibility Pattern）</li>
<li>命令模式（Command Pattern）</li>
<li>解释器模式（Interpreter Pattern）</li>
<li>迭代器模式（Iterator Pattern）</li>
<li>中介者模式（Mediator Pattern）</li>
<li>备忘录模式（Memento Pattern）</li>
<li>观察者模式（Observer Pattern）</li>
<li>状态模式（State Pattern）</li>
<li>空对象模式（Null Object Pattern）</li>
<li>策略模式（Strategy Pattern）</li>
<li>模板模式（Template Pattern）</li>
<li>访问者模式（Visitor Pattern）</li>
</ul>
</td>
</tr>
<tr><td>4</td><td><b>J2EE 模式</b><br>这些设计模式特别关注表示层。这些模式是由 Sun Java Center 鉴定的。</td>
<td>
<ul>
<li>MVC 模式（MVC Pattern）</li>
<li>业务代表模式（Business Delegate Pattern）</li>
<li>组合实体模式（Composite Entity Pattern）</li>
<li>数据访问对象模式（Data Access Object Pattern）</li>
<li>前端控制器模式（Front Controller Pattern）</li>
<li>拦截过滤器模式（Intercepting Filter Pattern）</li>
<li>服务定位器模式（Service Locator Pattern）</li>
<li>传输对象模式（Transfer Object Pattern）</li>
</ul>
</td>
</tr>
</tbody></table>

## 3 设计模式之间的关系
<div align=center><img width="80%" src="Other/DesignPattern/the-relationship-between-design-patterns.jpg"/></div>

## 4 设计模式的六大原则
#### 1、开闭原则（Open Close Principle）

开闭原则的意思是：对扩展开放，对修改关闭。在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。简言之，是为了使程序的扩展性好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类，后面的具体设计中我们会提到这点。

#### 2、里氏代换原则（Liskov Substitution Principle）

里氏代换原则是面向对象设计的基本原则之一。 里氏代换原则中说，任何基类可以出现的地方，子类一定可以出现。LSP 是继承复用的基石，只有当派生类可以替换掉基类，且软件单位的功能不受到影响时，基类才能真正被复用，而派生类也能够在基类的基础上增加新的行为。里氏代换原则是对开闭原则的补充。实现开闭原则的关键步骤就是抽象化，而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。

#### 3、依赖倒转原则（Dependence Inversion Principle）

这个原则是开闭原则的基础，具体内容：针对接口编程，依赖于抽象而不依赖于具体。

#### 4、接口隔离原则（Interface Segregation Principle）

这个原则的意思是：使用多个隔离的接口，比使用单个接口要好。它还有另外一个意思是：降低类之间的耦合度。由此可见，其实设计模式就是从大型软件架构出发、便于升级和维护的软件设计思想，它强调降低依赖，降低耦合。

#### 5、迪米特法则，又称最少知道原则（Demeter Principle）

最少知道原则是指：一个实体应当尽量少地与其他实体之间发生相互作用，使得系统功能模块相对独立。

#### 6、合成复用原则（Composite Reuse Principle）

合成复用原则是指：尽量使用合成/聚合的方式，而不是使用继承。

## 5 各设计模式详解
### 工厂模式（Factory Pattern）
>工厂模式（Factory Pattern）是最常用的设计模式之一。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。在工厂模式中，创建对象时不会对客户端暴露创建逻辑，而是通过使用一个共同的接口来指向新创建的对象。

#### 使用场景
1、日志记录器：记录可能记录到本地硬盘、系统事件、远程服务器等，用户可以选择记录日志到什么地方。 

2、数据库访问，当用户不知道最后系统采用哪一类数据库，以及数据库可能有变化时。 

3、Unity中的Primitive.Create方法。

#### 优点
1、一个调用者想创建一个对象，只要知道其名称就可以了。 

2、扩展性高，如果想增加一个产品，只要扩展一个工厂类就可以。 

3、屏蔽产品的具体实现，调用者只关心产品的接口。

#### 缺点
每次增加一个产品时，都需要增加一个具体类和对象实现工厂，使得系统中类的个数成倍增加，在一定程度上增加了系统的复杂度，同时也增加了系统具体类的依赖。这并不是什么好事。

#### 实现
创建一个 Shape 接口和实现 Shape 接口的实体类，定义工厂类 ShapeFactory。FactoryPatternDemo 类使用 ShapeFactory 来获取 Shape 对象。它将向 ShapeFactory 传递信息（CIRCLE / RECTANGLE / SQUARE），以便获取它所需对象的类型。
<div align=center><img width="80%" src="Other/DesignPattern/factory.jpg"/></div>



### 抽象工厂模式（Abstract Factory Pattern）
>抽象工厂模式（Abstract Factory Pattern）是围绕一个超级工厂创建其他工厂。该超级工厂又称为其他工厂的工厂。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。在抽象工厂模式中，接口是负责创建一个相关对象的工厂，不需要显式指定它们的类。每个生成的工厂都能按照工厂模式提供对象。

#### 使用场景
1、生成不同操作系统的程序。

2、游戏引擎中的场景管理器，下属不同类别object的工厂。

#### 优点
当一个产品族中的多个对象被设计成一起工作时，它能保证客户端始终只使用同一个产品族中的对象。

#### 缺点
产品族扩展非常困难，要增加一个系列的某一产品，既要在抽象的 Creator 里加代码，又要在具体的里面加代码。

#### 实现
创建 Shape 和 Color 接口和实现这些接口的实体类，创建抽象工厂类 AbstractFactory。接着定义工厂类 ShapeFactory 和 ColorFactory，这两个工厂类都是扩展了 AbstractFactory。然后创建一个工厂创造器/生成器类 FactoryProducer。

AbstractFactoryPatternDemo 类使用 FactoryProducer 来获取 AbstractFactory 对象。它将向 AbstractFactory 传递形状信息 Shape（CIRCLE / RECTANGLE / SQUARE），以便获取它所需对象的类型。同时它还向 AbstractFactory 传递颜色信息 Color（RED / GREEN / BLUE），以便获取它所需对象的类型。
<div align=center><img width="90%" src="Other/DesignPattern/abfactory.jpg"/></div>



### 单例模式（Singleton Pattern）
>单例模式（Singleton Pattern）也是非常常用的设计模式之一。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。单例类只能有一个实例，且必须自己创建自己的唯一实例，其他类可以无需实例化而直接通过这一实例访问该类。

#### 使用场景
1、要求生产唯一序列号。

2、WEB 中的计数器，不用每次刷新都在数据库里加一次，用单例先缓存起来。

3、创建的一个对象需要消耗的资源过多，比如 I/O 与数据库的连接等。

#### 优点
1、在内存里只有一个实例，减少了内存的开销，尤其是频繁的创建和销毁实例。

2、避免对资源的多重占用（比如写文件操作）。

#### 缺点
没有接口，不能继承，与单一职责原则冲突，一个类应该只关心内部逻辑，而不关心外面怎么样来实
例化。

#### 实现
创建一个 SingleObject 类。SingleObject 类有它的私有构造函数和本身的一个静态实例。SingleObject 类提供了一个静态方法，供外界获取它的静态实例。SingletonPatternDemo 类使用 SingleObject 类来获取 SingleObject 对象。
<div align=center><img width="50%" src="Other/DesignPattern/single.jpg"/></div>



### 建造者模式（Builder Pattern）
>建造者模式（Builder Pattern）使用多个简单的对象一步一步构建成一个复杂的对象。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式，即将一个复杂的对象的构建与它的表示分离，使得<strong>同样的构建过程可以创建不同的表示。</strong>

#### 使用场景
 1、需要生成的对象具有复杂的内部结构。 
 
 2、需要生成的对象内部属性本身相互依赖。

#### 优点
1、建造者独立，易扩展。 

2、便于控制细节风险。

#### 缺点
1、产品必须有共同点，范围有限制。 

2、如内部变化复杂，会有很多的建造类。

#### 实现
一个快餐店的经典案例：其中，一个典型的套餐可以是一个汉堡（Burger）和一杯冷饮（Cold drink）。汉堡（Burger）可以是素食汉堡（Veg Burger）或鸡肉汉堡（Chicken Burger），它们是包在纸盒中。冷饮（Cold drink）可以是可口可乐（coke）或百事可乐（pepsi），它们是装在瓶子中。

我们将创建一个表示食物条目（比如汉堡和冷饮）的 Item 接口和实现 Item 接口的实体类，以及一个表示食物包装的 Packing 接口和实现 Packing 接口的实体类，汉堡是包在纸盒中，冷饮是装在瓶子中。

然后我们创建一个 Meal 类，带有 Item 的 ArrayList 和一个通过结合 Item 来创建不同类型的 Meal 对象的 MealBuilder。BuilderPatternDemo 类使用 MealBuilder 来创建一个 Meal。
<div align=center><img width="80%" src="Other/DesignPattern/builder.png"/></div>



### 原型模式（Prototype Pattern）
>原型模式（Prototype Pattern）是用于创建重复的对象，同时又能保证性能。这种类型的设计模式属于创建型模式，它实现了一个原型接口，该接口用于创建当前对象的克隆。当直接创建对象的代价比较大时，则采用这种模式。

#### 使用场景
 1、资源优化场景。 
 
 2、类初始化需要消化非常多的资源，这个资源包括数据、硬件资源等。 
 
 3、性能和安全要求的场景。 
 
 4、通过 new 产生一个对象需要非常繁琐的数据准备或访问权限，则可以使用原型模式。 
 
 5、一个对象多个修改者的场景。 
 
 6、一个对象需要提供给其他对象访问，而且各个调用者可能都需要修改其值时，可以考虑使用原型模式拷贝多个对象供调用者使用。 
 
 7、在实际项目中，原型模式很少单独出现，一般是和工厂方法模式一起出现，通过 clone 的方法创建一个对象，然后由工厂方法提供给调用者。

#### 优点
1、性能提高。 

2、逃避构造函数的约束。

#### 缺点
1、配备克隆方法需要对类的功能进行通盘考虑，这对于全新的类不是很难，但对于已有的类不一定很容易，特别当一个类引用不支持串行化的间接对象，或者引用含有循环结构的时候。 

2、必须实现 Cloneable 接口。

#### 实现
例如，一个对象需要在一个高代价的数据库操作之后被创建。我们可以缓存该对象，在下一个请求时返回它的克隆，在需要的时候更新数据库，以此来减少数据库调用。

一个快餐店的经典案例：其中，一个典型的套餐可以是一个汉堡（Burger）和一杯冷饮（Cold drink）。汉堡（Burger）可以是素食汉堡（Veg Burger）或鸡肉汉堡（Chicken Burger），它们是包在纸盒中。冷饮（Cold drink）可以是可口可乐（coke）或百事可乐（pepsi），它们是装在瓶子中。

我们将创建一个表示食物条目（比如汉堡和冷饮）的 Item 接口和实现 Item 接口的实体类，以及一个表示食物包装的 Packing 接口和实现 Packing 接口的实体类，汉堡是包在纸盒中，冷饮是装在瓶子中。

然后我们创建一个 Meal 类，带有 Item 的 ArrayList 和一个通过结合 Item 来创建不同类型的 Meal 对象的 MealBuilder。BuilderPatternDemo 类使用 MealBuilder 来创建一个 Meal。
<div align=center><img width="80%" src="Other/DesignPattern/builder.png"/></div>



### 适配器模式（Adapter Pattern）
>适配器模式（Adapter Pattern）是作为两个不兼容的接口之间的桥梁。这种类型的设计模式属于结构型模式，它结合了两个独立接口的功能。

这种模式涉及到一个单一的类，该类负责加入独立的或不兼容的接口功能。例如：读卡器是作为内存卡和笔记本之间的适配器，将内存卡插入读卡器，再将读卡器插入笔记本，这样就可以通过笔记本来读取内存卡。

#### 使用场景
有动机地修改一个正常运行的系统的接口，这时应该考虑使用适配器模式。

#### 优点
1、可以让任何两个没有关联的类一起运行。 

2、提高了类的复用。 

3、增加了类的透明度。 

4、灵活性好。

#### 缺点
过多地使用适配器，会让系统非常零乱，不易整体进行把握。

#### 实现
我们有一个 MediaPlayer 接口和一个实现了 MediaPlayer 接口的实体类 AudioPlayer。默认情况下，AudioPlayer 可以播放 mp3 格式的音频文件。

我们还有另一个接口 AdvancedMediaPlayer 和实现了 AdvancedMediaPlayer 接口的实体类。该类可以播放 vlc 和 mp4 格式的文件。

我们想要让 AudioPlayer 播放其他格式的音频文件。为了实现这个功能，我们需要创建一个实现了 MediaPlayer 接口的适配器类 MediaAdapter，并使用 AdvancedMediaPlayer 对象来播放所需的格式。

AudioPlayer 使用适配器类 MediaAdapter 传递所需的音频类型，不需要知道能播放所需格式音频的实际类。AdapterPatternDemo 类使用 AudioPlayer 类来播放各种格式。
<div align=center><img width="90%" src="Other/DesignPattern/adaptor.png"/></div>



### 桥接模式（Bridge）
>桥接模式（Bridge）是用于把抽象化与实现化解耦，使得二者可以独立变化。这种类型的设计模式属于结构型模式，它通过提供抽象化和实现化之间的桥接结构，来实现二者的解耦。这种模式涉及到一个作为桥接的接口，使得实体类的功能独立于接口实现类。这两种类型的类可被结构化改变而互不影响。

#### 使用场景
1、如果一个系统需要在构件的抽象化角色和具体化角色之间增加更多的灵活性，避免在两个层次之间建立静态的继承联系，通过桥接模式可以使它们在抽象层建立一个关联关系。 

2、对于那些不希望使用继承或因为多层次继承导致系统类的个数急剧增加的系统，桥接模式尤为适用。 

3、一个类存在两个独立变化的维度，且这两个维度都需要进行扩展。对于两个独立变化的维度，使用桥接模式再适合不过了。

#### 优点
1、抽象和实现的分离。 

2、优秀的扩展能力。 

3、实现细节对客户透明。

#### 缺点
桥接模式的引入会增加系统的理解与设计难度，由于聚合关联关系建立在抽象层，要求开发者针对抽象进行设计与编程。

#### 实现
我们有一个作为桥接实现的 DrawAPI 接口和实现了 DrawAPI 接口的实体类 RedCircle、GreenCircle。Shape 是一个抽象类，将使用 DrawAPI 的对象。BridgePatternDemo 类使用 Shape 类来画出不同颜色的圆。
<div align=center><img width="80%" src="Other/DesignPattern/bridge.png"/></div>



### 过滤器模式（Filter Pattern）
>过滤器模式（Filter Pattern）允许开发人员使用不同的标准来过滤一组对象，通过逻辑运算以解耦的方式把它们连接起来。这种类型的设计模式属于结构型模式，它结合多个标准来获得单一标准。

#### 使用场景
需要制定不同的规则来对一组对象进行过滤，然后对过滤结果进行分组的场景：

1、敏感词过滤、舆情监测。

2、需要对对象列表（或数据列表）进行校验、审查或预处理的场景。

3、对网络接口的请求和响应进行拦截，例如对每一个请求和响应记录日志，一遍日后分析。

#### 优点
1、将对象的过滤、校验逻辑抽离出来，降低系统的复杂度。

2、过滤规则可实现重复利用。

#### 缺点
性能较低，每个过滤器对每一个元素都会进行遍历。如果有n个元素，m个过滤器，则负责度为O(mn)

#### 实现
创建一个 Person 对象、Criteria 接口和实现了该接口的实体类，来过滤 Person 对象的列表。CriteriaPatternDemo 类使用 Criteria 对象，基于各种标准和它们的结合来过滤 Person 对象的列表。
<div align=center><img width="90%" src="Other/DesignPattern/filter.png"/></div>



### 组合模式（Composite Pattern）
>组合模式（Composite Pattern），又叫部分整体模式，它依据树形结构来组合对象，用来表示部分以及整体层次。这种类型的设计模式属于结构型模式，它创建了对象组的树形结构。

这种模式创建了一个包含自己对象组的类。该类提供了修改相同对象组的方式。

#### 使用场景
部分、整体场景，如树形菜单，文件、文件夹的管理。

#### 优点
1、高层模块调用简单。 

2、节点自由增加。

#### 缺点
在使用组合模式时，其叶子和树枝的声明都是实现类，而不是接口，违反了依赖倒置原则。

#### 实现
我们有一个类 Employee，该类被当作组合模型类。CompositePatternDemo 类使用 Employee 类来添加部门层次结构，并打印所有员工。
<div align=center><img width="50%" src="Other/DesignPattern/composition.png"/></div>



### 装饰器模式（Decorator Pattern）
>装饰器模式（Decorator Pattern）允许向一个现有的对象添加新的功能，同时又不改变其结构。这种类型的设计模式属于结构型模式，它是作为现有的类的一个包装。

这种模式创建了一个装饰类，用来包装原有的类，并在保持类方法签名完整性的前提下，提供了额外的功能。

#### 使用场景
1、扩展一个类的功能。 

2、动态增加功能，动态撤销。

#### 优点
装饰类和被装饰类可以独立发展，不会相互耦合，装饰模式是继承的一个替代模式，装饰模式可以动态扩展一个实现类的功能。

#### 缺点
多层装饰比较复杂。

#### 实现
我们将创建一个 Shape 接口和实现了 Shape 接口的实体类。然后我们创建一个实现了 Shape 接口的抽象装饰类 ShapeDecorator，并把 Shape 对象作为它的实例变量。

RedShapeDecorator 是实现了 ShapeDecorator 的实体类。

DecoratorPatternDemo 类使用 RedShapeDecorator 来装饰 Shape 对象。
<div align=center><img width="80%" src="Other/DesignPattern/deco.png"/></div>



### 外观模式（Facade Pattern）
>外观模式（Facade Pattern）隐藏系统的复杂性，并向客户端提供了一个客户端可以访问系统的接口。这种类型的设计模式属于结构型模式，它向现有的系统添加一个接口，来隐藏系统的复杂性。

这种模式涉及到一个单一的类，该类提供了客户端请求的简化方法和对现有系统类方法的委托调用。

#### 使用场景
1、为复杂的模块或子系统提供外界访问的模块。 

2、子系统相对独立。 

3、预防低水平人员带来的风险。

#### 优点
1、减少系统相互依赖。 

2、提高灵活性。 

3、提高了安全性。

#### 缺点
不符合开闭原则，如果要改东西很麻烦，继承重写都不合适。

#### 实现
创建一个 Shape 接口和实现了 Shape 接口的实体类，定义一个外观类 ShapeMaker。

ShapeMaker 类使用实体类来代表用户对这些类的调用。FacadePatternDemo 类使用 ShapeMaker 类来显示结果。
<div align=center><img width="80%" src="Other/DesignPattern/facade.png"/></div>



### 享元模式（Flyweight Pattern）
>享元模式（Flyweight Pattern）主要用于减少创建对象的数量，以减少内存占用和提高性能。这种类型的设计模式属于结构型模式，它提供了减少对象数量从而改善应用所需的对象结构的方式。享元模式尝试重用现有的同类对象，如果未找到匹配的对象，则创建新对象。

#### 使用场景
1、系统有大量相似对象。 

2、需要缓冲池的场景。

#### 优点
大大减少对象的创建，降低系统的内存，使效率提高。

#### 缺点
提高了系统的复杂度，需要分离出外部状态和内部状态，而且外部状态具有固有化的性质，不应该随着内部状态的变化而变化，否则会造成系统的混乱。

#### 实现
创建一个 Shape 接口和实现了 Shape 接口的实体类 Circle，定义工厂类 ShapeFactory。

ShapeFactory 有一个 Circle 的 HashMap，其中键名为 Circle 对象的颜色。无论何时接收到请求，都会创建一个特定颜色的圆。ShapeFactory 检查它的 HashMap 中的 circle 对象，如果找到 Circle 对象，则返回该对象，否则将创建一个存储在 hashmap 中以备后续使用的新对象，并把该对象返回到客户端。

FlyWeightPatternDemo 类使用 ShapeFactory 来获取 Shape 对象。它将向 ShapeFactory 传递信息（red / green / blue/ black / white），以便获取它所需对象的颜色。
<div align=center><img width="60%" src="Other/DesignPattern/flywei.png"/></div>



### 代理模式（Proxy Pattern）
>代理模式（Proxy Pattern）中，一个类代表另一个类的功能。这种类型的设计模式属于结构型模式，创建具有现有对象的对象，以便向外界提供功能接口。

#### 使用场景
按职责来划分，通常有以下使用场景： 

1、远程代理。 

2、虚拟代理。 

3、Copy-on-Write 代理。 

4、保护（Protect or Access）代理。 

5、Cache代理。 

6、防火墙（Firewall）代理。 

7、同步化（Synchronization）代理。 

8、智能引用（Smart Reference）代理。

#### 优点
1、职责清晰。 

2、高扩展性。 

3、智能化。

#### 缺点
1、由于在客户端和真实主题之间增加了代理对象，因此有些类型的代理模式可能会造成请求的处理速度变慢。 

2、实现代理模式需要额外的工作，有些代理模式的实现非常复杂。

#### 实现
创建一个 Image 接口和实现了 Image 接口的实体类。ProxyImage 是一个代理类，减少 RealImage 对象加载的内存占用。

ProxyPatternDemo 类使用 ProxyImage 来获取要加载的 Image 对象，并按照需求进行显示。
<div align=center><img width="80%" src="Other/DesignPattern/proxy.png"/></div>



### 责任链模式（Chain of Responsibility Pattern）
>责任链模式（Chain of Responsibility Pattern）为请求创建了一个接收者对象的链。这种模式给予请求的类型，对请求的发送者和接收者进行解耦。这种类型的设计模式属于行为型模式。

在这种模式中，通常每个接收者都包含对另一个接收者的引用。如果一个对象不能处理该请求，那么它会把相同的请求传给下一个接收者，依此类推。

#### 使用场景
1、有多个对象可以处理同一个请求，具体哪个对象处理该请求由运行时刻自动确定。 

2、在不明确指定接收者的情况下，向多个对象中的一个提交一个请求。 

3、可动态指定一组对象处理请求。

#### 优点
1、降低耦合度。它将请求的发送者和接收者解耦。 

2、简化了对象。使得对象不需要知道链的结构。 

3、增强给对象指派职责的灵活性。通过改变链内的成员或者调动它们的次序，允许动态地新增或者删除责任。 

4、增加新的请求处理类很方便。

#### 缺点
1、不能保证请求一定被接收。 

2、系统性能将受到一定影响，而且在进行代码调试时不太方便，可能会造成循环调用。 

3、可能不容易观察运行时的特征，有碍于除错。

#### 实现
创建抽象类 AbstractLogger，带有详细的日志记录级别。然后我们创建三种类型的记录器，都扩展了 AbstractLogger。每个记录器消息的级别是否属于自己的级别，如果是则相应地打印出来，否则将不打印并把消息传给下一个记录器。
<div align=center><img width="80%" src="Other/DesignPattern/responsibility.png"/></div>



### 命令模式（Command Pattern）
>命令模式（Command Pattern）是一种数据驱动的设计模式，它属于行为型模式。请求以命令的形式包裹在对象中，并传给调用对象。调用对象寻找可以处理该命令的合适的对象，并把该命令传给相应的对象，该对象执行命令。

在这种模式中，通常每个接收者都包含对另一个接收者的引用。如果一个对象不能处理该请求，那么它会把相同的请求传给下一个接收者，依此类推。

#### 使用场景
认为是命令的地方都可以使用命令模式，比如： 

1、GUI 中每一个按钮都是一条命令。 

2、模拟 CMD。

#### 优点
1、降低了系统耦合度。 

2、新的命令可以很容易添加到系统中去。

#### 缺点
使用命令模式可能会导致某些系统有过多的具体命令类。

#### 实现
首先创建作为命令的接口 Order，然后创建作为请求的 Stock 类。实体命令类 BuyStock 和 SellStock，实现了 Order 接口，将执行实际的命令处理。创建作为调用对象的类 Broker，它接受订单并能下订单。

Broker 对象使用命令模式，基于命令的类型确定哪个对象执行哪个命令。CommandPatternDemo 类使用 Broker 类来演示命令模式。
<div align=center><img width="80%" src="Other/DesignPattern/command.png"/></div>



### 解释器模式（Interpreter Pattern）
>解释器模式（Interpreter Pattern）提供了评估语言的语法或表达式的方式，它属于行为型模式。这种模式实现了一个表达式接口，该接口解释一个特定的上下文。这种模式被用在 SQL 解析、符号处理引擎等。

#### 使用场景
1、可以将一个需要解释执行的语言中的句子表示为一个抽象语法树。 

2、一些重复出现的问题可以用一种简单的语言来进行表达。 

3、一个简单语法需要解释的场景。

#### 优点
1、可扩展性比较好，灵活。 

2、增加了新的解释表达式的方式。 

3、易于实现简单文法。

#### 缺点
1、可利用场景比较少。 

2、对于复杂的文法比较难维护。 

3、解释器模式会引起类膨胀。 

4、解释器模式采用递归调用方法。

#### 实现
创建一个接口 Expression 和实现了 Expression 接口的实体类。定义作为上下文中主要解释器的 TerminalExpression 类。其他的类 OrExpression、AndExpression 用于创建组合式表达式。

InterpreterPatternDemo，我们的演示类使用 Expression 类创建规则和演示表达式的解析。
<div align=center><img width="60%" src="Other/DesignPattern/interpreter_pattern_uml_diagram.jpg"/></div>



### 迭代器模式（Iterator Pattern）
>迭代器模式（Iterator Pattern）是 Java 和 .Net 编程环境中非常常用的设计模式。这种模式用于顺序访问集合对象的元素，不需要知道集合对象的底层表示。迭代器模式属于行为型模式。

#### 使用场景
1、访问一个聚合对象的内容而无须暴露它的内部表示。 

2、需要为聚合对象提供多种遍历方式。 

3、为遍历不同的聚合结构提供一个统一的接口。

#### 优点
1、它支持以不同的方式遍历一个聚合对象。 

2、迭代器简化了聚合类。 

3、在同一个聚合上可以有多个遍历。 

4、在迭代器模式中，增加新的聚合类和迭代器类都很方便，无须修改原有代码。

#### 缺点
由于迭代器模式将存储数据和遍历数据的职责分离，增加新的聚合类需要对应增加新的迭代器类，类的个数成对增加，这在一定程度上增加了系统的复杂性。

#### 实现
创建一个叙述导航方法的 Iterator 接口和一个返回迭代器的 Container 接口。实现了 Container 接口的实体类将负责实现 Iterator 接口。

IteratorPatternDemo，我们的演示类使用实体类 NamesRepository 来打印 NamesRepository 中存储为集合的 Names。
<div align=center><img width="70%" src="Other/DesignPattern/iterator_pattern_uml_diagram.jpg"/></div>



### 中介者模式（Mediator Pattern）
>中介者模式（Mediator Pattern）是用来降低多个对象和类之间的通信复杂性。这种模式提供了一个中介类，该类通常处理不同类之间的通信，并支持松耦合，使代码易于维护。中介者模式属于行为型模式。

#### 使用场景
1、系统中对象之间存在比较复杂的引用关系，导致它们之间的依赖关系结构混乱而且难以复用该对象。 

2、想通过一个中间类来封装多个类中的行为，而又不想生成太多的子类。

#### 优点
1、降低了类的复杂度，将一对多转化成了一对一。 

2、各个类之间的解耦。 

3、符合迪米特原则。

#### 缺点
中介者会庞大，变得复杂难以维护。

#### 实现
聊天室实例：多个用户可以向聊天室发送消息，聊天室向所有的用户显示消息。我们将创建两个类 ChatRoom 和 User。User 对象使用 ChatRoom 方法来分享他们的消息。
<div align=center><img width="70%" src="Other/DesignPattern/mediator_pattern_uml_diagram.jpg"/></div>



### 备忘录模式（Memento Pattern）
>备忘录模式（Memento Pattern）保存一个对象的某个状态，以便在适当的时候恢复对象。备忘录模式属于行为型模式。

#### 使用场景
1、需要保存/恢复数据的相关状态场景。 

2、提供一个可回滚的操作。

#### 优点
 1、给用户提供了一种可以恢复状态的机制，可以使用户能够比较方便地回到某个历史的状态。 
 
 2、实现了信息的封装，使得用户不需要关心状态的保存细节。

#### 缺点
消耗资源。如果类的成员变量过多，势必会占用比较大的资源，而且每一次保存都会消耗一定的内存。

#### 实现
备忘录模式使用三个类 Memento、Originator 和 CareTaker。Memento 包含了要被恢复的对象的状态。Originator 创建并在 Memento 对象中存储状态。Caretaker 对象负责从 Memento 中恢复对象的状态。
<div align=center><img width="70%" src="Other/DesignPattern/memento_pattern_uml_diagram.jpg"/></div>



### 观察者模式（Observer Pattern）
>当对象间存在一对多关系时，则使用观察者模式（Observer Pattern）。比如，当一个对象被修改时，则会自动通知依赖它的对象。观察者模式属于行为型模式。

#### 使用场景
1、一个抽象模型有两个方面，其中一个方面依赖于另一个方面。将这些方面封装在独立的对象中使它们可以各自独立地改变和复用。

2、一个对象的改变将导致其他一个或多个对象也发生改变，而不知道具体有多少对象将发生改变，可以降低对象之间的耦合度。

3、一个对象必须通知其他对象，而并不知道这些对象是谁。

4、需要在系统中创建一个触发链，A对象的行为将影响B对象，B对象的行为将影响C对象……，可以使用观察者模式创建一种链式触发机制。

#### 优点
1、观察者和被观察者是抽象耦合的。 

2、建立一套触发机制。

#### 缺点
1、如果一个被观察者对象有很多的直接和间接的观察者的话，将所有的观察者都通知到会花费很多时间。 

2、如果在观察者和观察目标之间有循环依赖的话，观察目标会触发它们之间进行循环调用，可能导致系统崩溃。 

3、观察者模式没有相应的机制让观察者知道所观察的目标对象是怎么发生变化的，而仅仅只是知道观察目标发生了变化。

#### 实现
观察者模式使用三个类 Subject、Observer 和 Client。Subject 对象带有绑定观察者到 Client 对象和从 Client 对象解绑观察者的方法。我们创建 Subject 类、Observer 抽象类和扩展了抽象类 Observer 的实体类。
<div align=center><img width="70%" src="Other/DesignPattern/observer_pattern_uml_diagram.jpg"/></div>



### 状态模式（State Pattern）
>在状态模式（State Pattern）中，类的行为是基于它的状态改变的。这种类型的设计模式属于行为型模式。

#### 使用场景
1、行为随状态改变而改变的场景。 

2、条件、分支语句的代替者。

#### 优点
1、封装了转换规则。 

2、枚举可能的状态，在枚举状态之前需要确定状态种类。 

3、将所有与某个状态有关的行为放到一个类中，并且可以方便地增加新的状态，只需要改变对象状态即可改变对象的行为。 

4、允许状态转换逻辑与状态对象合成一体，而不是某一个巨大的条件语句块。 

5、可以让多个环境对象共享一个状态对象，从而减少系统中对象的个数。

#### 缺点
1、状态模式的使用必然会增加系统类和对象的个数。 

2、状态模式的结构与实现都较为复杂，如果使用不当将导致程序结构和代码的混乱。 

3、状态模式对"开闭原则"的支持并不太好，对于可以切换状态的状态模式，增加新的状态类需要修改那些负责状态转换的源代码，否则无法切换到新增状态，而且修改某个状态类的行为也需修改对应类的源代码。

#### 实现
在状态模式中，我们创建表示各种状态的对象和一个行为随着状态对象改变而改变的 context 对象。
下面例子中创建了一个 State 接口和实现了 State 接口的实体状态类。Context 是一个带有某个状态的类。

<div align=center><img width="70%" src="Other/DesignPattern/state_pattern_uml_diagram.png"/></div>



### 空对象模式（Null Object Pattern）
>在空对象模式（Null Object Pattern）中，一个空对象取代 NULL 对象实例的检查。Null 对象不是检查空值，而是反应一个不做任何动作的关系。这样的 Null 对象也可以在数据不可用的时候提供默认的行为。

在空对象模式中，我们创建一个指定各种要执行的操作的抽象类和扩展该类的实体类，还创建一个未对该类做任何实现的空对象类，该空对象类将无缝地使用在需要检查空值的地方。

#### 使用场景
需要空判断的场景，避免空指针异常。

#### 优点
1、省去代码中对 Null 值的判断和检查；

2、让代码显的更加优雅和可读性更高；

3、让系统更加稳定，避免程序抛出 NullPointerException 异常。

#### 缺点
因为增加了更多的类信息，从而使系统更复杂。

#### 实现
创建一个定义操作（在这里，是客户的名称）的 AbstractCustomer 抽象类，和扩展了 AbstractCustomer 类的实体类。工厂类 CustomerFactory 基于客户传递的名字来返回 RealCustomer 或 NullCustomer 对象。

```
class ObjectFactory {
    public static AbstractObject creator(final String name) {
        AbstractObject result = null;
        switch (name) {
            case "Java":
                result = new ConcreteObject("Java");
                break;
            case "SQL":
                result = new ConcreteObject("SQL");
                break;
            default:
                result = new NullObject();
                break;
        }
        return result;
    }
}
```

<div align=center><img width="70%" src="Other/DesignPattern/null_pattern_uml_diagram.jpg"/></div>



### 策略模式（Strategy Pattern）
>在策略模式（Strategy Pattern）中，一个类的行为或其算法可以在运行时更改。这种类型的设计模式属于行为型模式。

在策略模式中，我们创建表示各种策略的对象和一个行为随着策略对象改变而改变的 context 对象。策略对象改变 context 对象的执行算法。

#### 使用场景
1、如果在一个系统里面有许多类，它们之间的区别仅在于它们的行为，那么使用策略模式可以动态地让一个对象在许多行为中选择一种行为。 

2、一个系统需要动态地在几种算法中选择一种。 

3、如果一个对象有很多的行为，如果不用恰当的模式，这些行为就只好使用多重的条件选择语句来实现。

#### 优点
1、算法可以自由切换。 

2、避免使用多重条件判断。 

3、扩展性良好。

#### 缺点
1、策略类会增多。

2、所有策略类都需要对外暴露。

#### 实现
创建一个定义活动的 Strategy 接口和实现了 Strategy 接口的实体策略类。Context 是一个使用了某种策略的类。

<div align=center><img width="70%" src="Other/DesignPattern/strategy_pattern_uml_diagram.jpg"/></div>



### 模板模式（Template Pattern）
>在模板模式（Template Pattern）中，一个抽象类公开定义了执行它的方法的方式/模板。它的子类可以按需要重写方法实现，但调用将以抽象类中定义的方式进行。这种类型的设计模式属于行为型模式。

#### 使用场景
1、有多个子类共有的方法，且逻辑相同。 

2、重要的、复杂的方法，可以考虑作为模板方法。

#### 优点
1、封装不变部分，扩展可变部分。 

2、提取公共代码，便于维护。 

3、行为由父类控制，子类实现。

#### 缺点
每一个不同的实现都需要一个子类来实现，导致类的个数增加，使得系统更加庞大。

#### 实现
创建一个定义操作的 Game 抽象类，其中，模板方法设置为 final，这样它就不会被重写。Cricket 和 Football 是扩展了 Game 的实体类，它们重写了抽象类的方法。

<div align=center><img width="70%" src="Other/DesignPattern/template_pattern_uml_diagram.jpg"/></div>



### 访问者模式（Visitor Pattern）
>在访问者模式（Visitor Pattern）中，我们使用了一个访问者类，它改变了元素类的执行算法。通过这种方式，元素的执行算法可以随着访问者改变而改变。这种类型的设计模式属于行为型模式。根据模式，元素对象已接受访问者对象，这样访问者对象就可以处理元素对象上的操作。

#### 使用场景
1、对象结构中对象对应的类很少改变，但经常需要在此对象结构上定义新的操作。 

2、需要对一个对象结构中的对象进行很多不同的并且不相关的操作，而需要避免让这些操作"污染"这些对象的类，也不希望在增加新操作时修改这些类。

#### 优点
1、符合单一职责原则。 

2、优秀的扩展性。 

3、灵活性。

#### 缺点
1、具体元素对访问者公布细节，违反了迪米特原则。 

2、具体元素变更比较困难。 

3、违反了依赖倒置原则，依赖了具体类，没有依赖抽象。

#### 实现
创建一个定义接受操作的 ComputerPart 接口。Keyboard、Mouse、Monitor 和 Computer 是实现了 ComputerPart 接口的实体类。我们将定义另一个接口 ComputerPartVisitor，它定义了访问者类的操作。Computer 使用实体访问者来执行相应的动作。

<div align=center><img width="70%" src="Other/DesignPattern/visitor_pattern_uml_diagram.jpg"/></div>



