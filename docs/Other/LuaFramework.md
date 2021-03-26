# Lua Framework

Unity 3D - Lua Framework热更新框架学习笔记

## 1 什么是 Lua Framework
Lua Framework是一个基于toLua实现的Unity游戏纯Lua客户端完整框架。

## 2 Lua Framework 配置 & 快速入门
### 2-1 在github上下载LuaFramework_UGUI_V2
> LuaFramework_UGUI_V2中已经包含了toLua，不需要再单独下载toLua。

LuaFramework_UGUI_V2：https://github.com/jarjin/LuaFramework_UGUI_V2

toLua：https://github.com/topameng/tolua

!> LuaFramework是基于Unity 5.0 + UGUI + tolua构建的工程，对新版本Unity目前支持不是很好，导入会报错。

### 2-2 测试示例场景
下载解压后得到一个unity工程，直接打开，然后：

1. 单击菜单Lua/Clear Wrap Files（清除Wrap文件缓存，重新生成）
2. 单击菜单Lua/Generate All （生成Wrap文件，即将C#类注册到Lua）
3. 单击菜单LuaFramework/Build Windows Resources  (根据不同平台生成AssetBundle资源[必须])
4. 打开场景main，资源文件目录：LuaFramework/Scenes/main，点击运行
5. 场景中就可以看到由Lua动态创建的面板（但此时Lua文件还是从本地读取的）：

<div align=center><img width="60%" src="Other/LuaFramework/1.png"/></div>

### 2-3 添加自己的Lua代码
#### step 1
Main.lua是框架运行时会自动执行的Lua代码文件（路径：LuaFramework/Lua/Main.lua），我们在function Main()函数中添加一个Log语句：```LuaFramework.Util.Log("hello world!")```

<div align=center><img width="60%" src="Other/LuaFramework/6.png"/></div>

#### step 2
单击菜单中的LuaFramework/Build Windows Resources，把资源和代码打包生成相应的AssetBundle文件，这些文件全部存放在StreamingAssets目录，热更新就是从服务器上更新这些AssetBundle文件，然后解包成代码、资源并做出相应的执行。

<div align=center><img width="30%" src="Other/LuaFramework/7.png"/></div>

#### step 3
 把/StreamingAssets目录以及里面的AssetBundle文件，放到服务器里，这里我们用nodejs在本地搭一个简易的服务器，直接在对应目录下cmd打开控制台输入hs即可：

 <div align=center><img width="80%" src="Other/LuaFramework/8.png"/></div>

 搭建好了先测试一下从浏览器里访问StreamingAssets目录里的files.txt文件：
 
 <div align=center><img width="50%" src="Other/LuaFramework/9.png"/></div>

#### step 4
 配置热更新地址，并运行测试。首先打开App配置文件目录：LuaFramework/Scrips/ConstDefine/AppConst.cs ,然后找到这几行修改一下：
 
 <div align=center><img width="80%" src="Other/LuaFramework/10.png"/></div>

  运行工程，此时客户端自动下载服务器上/StreamingAssets目录里的所有AssetBundle文件，并解包和执行，我们打开Console窗口，可以看到我们之前在Main.l里ua写的Log也被解包和执行了：
  
 <div align=center><img width="50%" src="Other/LuaFramework/11.png"/></div>

### 2-4 部署自己的Asset
#### step 1
新建一个Scene，放在目录：LuaFramework/Scenes/下，然后在TestScene中添加一个GameObject,命名为GameManager，为这个对象添加上Main脚本（目录：LuaFramework/Scripts/Main，作用为启动热更新框架） 

接着创建一个UI/Canvas 对象，并把Main Camera对象放到其子目录，总体结构如下图：

 <div align=center><img width="80%" src="Other/LuaFramework/12.png"/></div>

!>注意要给Main Camera组件加上一个名叫GuiCamera的Tag，这个是必须的不然会报错

 <div align=center><img width="80%" src="Other/LuaFramework/13.png"/></div>

#### step 2
创建一个UGUI的界面框，并制成prefab，以及生成相应的AssetBundle

用UI/Image和UI/Button生成一个界面框，起名为TestPanel，如图

 <div align=center><img width="80%" src="Other/LuaFramework/14.png"/></div>
 
 然后在'/LuaFramework/Examples/Builds/'目录建立一个文件夹叫Test，并把场景中的TestPanel拖到Test文件夹生成一个预设体prefab，如图：
 
 <div align=center><img width="80%" src="Other/LuaFramework/15.png"/></div>

 打开/LuaFramework/Editor/Packager.cs,找到static void HandleExampleBundle()函数（位置大概在中间），在函数中加入这行
 ```
 AddBuildMap("test" + AppConst.ExtName, "*.prefab", "Assets/LuaFramework/Examples/Builds/Test");
 ```
 加了这行之后，假如点击Build Windows Resources之后，就会生成相应的Test的AssetBundle包了。
 
 <div align=center><img width="80%" src="Other/LuaFramework/16.png"/></div>

 点击菜单'LuaFramework/Build Windows Resources'，之后便能够在目录'/StreamingAssets/'找到test的AssetBundle包
 
 <div align=center><img width="35%" src="Other/LuaFramework/17.png"/></div>

 最后删除掉场景视图中TestPanel组件，之后我们会利用prefab和热更新重新加载出来。

#### step 3
用Lua脚本以MVC框架的规则构建出TestPanel组件。首先用Lua脚本以MVC框架的规则构建出TestPanel组件：

1. 新建/LuaFramework/Lua/Controller/TestCtrl.lua 
2. 新建/LuaFramework/Lua/View/TestPanel.lua
3. /LuaFramework/Lua/Common/define.lua 增加条目
4. /LuaFramework/Lua/Logic/CtrlManager.lua  增加条目
5. 在/LuaFramework/Lua/Logic/Game.lua  中加上我们组件的运行的代码

一条一条来，首先新建文件/LuaFramework/Lua/Controller/TestCtrl.lua ，其中的内容为规定格式：
```
--这是TestCtrl.lua的代码
require "Common/define"
require "3rd/pblua/login_pb"
require "3rd/pbc/protobuf"
 
local sproto = require "3rd/sproto/sproto"
local core = require "sproto.core"
local print_r = require "3rd/sproto/print_r"
 
TestCtrl = {};
local this = TestCtrl;
 
 
local panel;
local test;
local transform;
local gameObject;
 
--构建函数--
function TestCtrl.New()
	logWarn("TestCtrl.New--->>");
	return this;
end
 
function TestCtrl.Awake()
	logWarn("TestCtrl.Awake--->>");
	panelMgr:CreatePanel('Test', this.OnCreate);
end
 
 
--启动事件--
function TestCtrl.OnCreate(obj)
	gameObject = obj;
	transform = obj.transform;
	logWarn("Start lua--->>"..gameObject.name);
end
```

 然后是新建/LuaFramework/Lua/View/TestPanel.lua，其中的内容也是规定格式：
 ```
 --这是TestPanel.lua的代码
local transform;
local gameObject;
 
TestPanel = {};
local this = TestPanel;
 
--启动事件--
function TestPanel.Awake(obj)
	gameObject = obj;
	transform = obj.transform;
 
	this.InitPanel();
	logWarn("Awake lua--->>"..gameObject.name);
end
 
--初始化面板--
function TestPanel.InitPanel()
end
 
--单击事件--
function TestPanel.OnDestroy()
	logWarn("OnDestroy---->>>");
end
 ```

 打开/LuaFramework/Lua/Common/define.lua ，在开头的CtrlNames,PanelNames表里添加上Test = "TestCtrl"与"TestPanel"。define.lua代码如下：

 ```
 --这是define.lua修改后的代码
CtrlNames = {
	Prompt = "PromptCtrl",
	Message = "MessageCtrl",
	Test = "TestCtrl",     --新增的条行
}
 
PanelNames = {
	"PromptPanel",
	"MessagePanel",
	"TestPanel",           --新增的条行
}
 
--协议类型--
ProtocalType = {
	BINARY = 0,
	PB_LUA = 1,
	PBC = 2,
	SPROTO = 3,
}
--当前使用的协议类型--
TestProtoType = ProtocalType.BINARY;
 
Util = LuaFramework.Util;
AppConst = LuaFramework.AppConst;
LuaHelper = LuaFramework.LuaHelper;
ByteBuffer = LuaFramework.ByteBuffer;
 
resMgr = LuaHelper.GetResManager();
panelMgr = LuaHelper.GetPanelManager();
soundMgr = LuaHelper.GetSoundManager();
networkMgr = LuaHelper.GetNetManager();
 
WWW = UnityEngine.WWW;
GameObject = UnityEngine.GameObject;
 ```

 打开/LuaFramework/Lua/Logic/CtrlManager.lua ，在开头添加上require "Controller/TestCtrl" ，并在function CtrlManager.Init()中添加上ctrlList[CtrlNames.Test] = TestCtrl.New();语句，CtrlManager代码如下：

 ```
 --这是CtrlManager.lua修改后的代码
 
require "Common/define"
require "Controller/PromptCtrl"
require "Controller/MessageCtrl"
require "Controller/TestCtrl"     --新增的条行
 
CtrlManager = {};
local this = CtrlManager;
local ctrlList = {};	--控制器列表--
 
function CtrlManager.Init()
	logWarn("CtrlManager.Init----->>>");
	ctrlList[CtrlNames.Prompt] = PromptCtrl.New();
	ctrlList[CtrlNames.Message] = MessageCtrl.New();
	ctrlList[CtrlNames.Test] = TestCtrl.New();           --新增的条行
	return this;
end
 
--添加控制器--
function CtrlManager.AddCtrl(ctrlName, ctrlObj)
	ctrlList[ctrlName] = ctrlObj;
end
 
--获取控制器--
function CtrlManager.GetCtrl(ctrlName)
	return ctrlList[ctrlName];
end
 
--移除控制器--
function CtrlManager.RemoveCtrl(ctrlName)
	ctrlList[ctrlName] = nil;
end
 
--关闭控制器--
function CtrlManager.Close()
	logWarn('CtrlManager.Close---->>>');
end
 ```

 打开/LuaFramework/Lua/Logic/Game.lua  ，引用部分加上 require "Controller/TestCtrl" ，在function Game.OnInitOK()中加入代码：（启动我们的TestPanel组件）
 ```
local ctrl = CtrlManager.GetCtrl(CtrlNames.Test);
if ctrl ~= nil and AppConst.ExampleMode == 1 then
	ctrl:Awake();
end
```
Game.lua完整代码如下：
```
--这是Game.lua修改后的代码
require "3rd/pblua/login_pb"
require "3rd/pbc/protobuf"
 
local lpeg = require "lpeg"
 
local json = require "cjson"
local util = require "3rd/cjson/util"
 
local sproto = require "3rd/sproto/sproto"
local core = require "sproto.core"
local print_r = require "3rd/sproto/print_r"
 
require "Logic/LuaClass"
require "Logic/CtrlManager"
require "Common/functions"
require "Controller/PromptCtrl"
require "Controller/TestCtrl"         --新增的条行
 
--管理器--
Game = {};
local this = Game;
 
local game;
local transform;
local gameObject;
local WWW = UnityEngine.WWW;
 
function Game.InitViewPanels()
	for i = 1, #PanelNames do
		require ("View/"..tostring(PanelNames[i]))
	end
end
 
--初始化完成，发送链接服务器信息--
function Game.OnInitOK()
    AppConst.SocketPort = 2012;
    AppConst.SocketAddress = "127.0.0.1";
    networkMgr:SendConnect();
 
    --注册LuaView--
    this.InitViewPanels();
 
    this.test_class_func();
    this.test_pblua_func();
    this.test_cjson_func();
    this.test_pbc_func();
    this.test_lpeg_func();
    this.test_sproto_func();
    coroutine.start(this.test_coroutine);
 
    CtrlManager.Init();
    local ctrl = CtrlManager.GetCtrl(CtrlNames.Prompt);
    if ctrl ~= nil and AppConst.ExampleMode == 1 then
        ctrl:Awake();
    end
 
    local ctrl = CtrlManager.GetCtrl(CtrlNames.Test);           --新增的条行
    if ctrl ~= nil and AppConst.ExampleMode == 1 then           --新增的条行
        ctrl:Awake();                                           --新增的条行
    end                                                         --新增的条行
 
 
    logWarn('LuaFramework InitOK--->>>');
end
 
--测试协同--
function Game.test_coroutine()
    logWarn("1111");
    coroutine.wait(1);
    logWarn("2222");
 
    local www = WWW("http://bbs.ulua.org/readme.txt");
    coroutine.www(www);
    logWarn(www.text);
end
 
--测试sproto--
function Game.test_sproto_func()
    logWarn("test_sproto_func-------->>");
    local sp = sproto.parse [[
    .Person {
        name 0 : string
        id 1 : integer
        email 2 : string
        .PhoneNumber {
            number 0 : string
            type 1 : integer
        }
        phone 3 : *PhoneNumber
    }
    .AddressBook {
        person 0 : *Person(id)
        others 1 : *Person
    }
    ]]
 
    local ab = {
        person = {
            [10000] = {
                name = "Alice",
                id = 10000,
                phone = {
                    { number = "123456789" , type = 1 },
                    { number = "87654321" , type = 2 },
                }
            },
            [20000] = {
                name = "Bob",
                id = 20000,
                phone = {
                    { number = "01234567890" , type = 3 },
                }
            }
        },
        others = {
            {
                name = "Carol",
                id = 30000,
                phone = {
                    { number = "9876543210" },
                }
            },
        }
    }
    local code = sp:encode("AddressBook", ab)
    local addr = sp:decode("AddressBook", code)
    print_r(addr)
end
 
--测试lpeg--
function Game.test_lpeg_func()
	logWarn("test_lpeg_func-------->>");
	-- matches a word followed by end-of-string
	local p = lpeg.R"az"^1 * -1
 
	print(p:match("hello"))        --> 6
	print(lpeg.match(p, "hello"))  --> 6
	print(p:match("1 hello"))      --> nil
end
 
--测试lua类--
function Game.test_class_func()
    LuaClass:New(10, 20):test();
end
 
--测试pblua--
function Game.test_pblua_func()
    local login = login_pb.LoginRequest();
    login.id = 2000;
    login.name = 'game';
    login.email = 'jarjin@163.com';
 
    local msg = login:SerializeToString();
    LuaHelper.OnCallLuaFunc(msg, this.OnPbluaCall);
end
 
--pblua callback--
function Game.OnPbluaCall(data)
    local msg = login_pb.LoginRequest();
    msg:ParseFromString(data);
    print(msg);
    print(msg.id..' '..msg.name);
end
 
--测试pbc--
function Game.test_pbc_func()
    local path = Util.DataPath.."lua/3rd/pbc/addressbook.pb";
    log('io.open--->>>'..path);
 
    local addr = io.open(path, "rb")
    local buffer = addr:read "*a"
    addr:close()
    protobuf.register(buffer)
 
    local addressbook = {
        name = "Alice",
        id = 12345,
        phone = {
            { number = "1301234567" },
            { number = "87654321", type = "WORK" },
        }
    }
    local code = protobuf.encode("tutorial.Person", addressbook)
    LuaHelper.OnCallLuaFunc(code, this.OnPbcCall)
end
 
--pbc callback--
function Game.OnPbcCall(data)
    local path = Util.DataPath.."lua/3rd/pbc/addressbook.pb";
 
    local addr = io.open(path, "rb")
    local buffer = addr:read "*a"
    addr:close()
    protobuf.register(buffer)
    local decode = protobuf.decode("tutorial.Person" , data)
 
    print(decode.name)
    print(decode.id)
    for _,v in ipairs(decode.phone) do
        print("\t"..v.number, v.type)
    end
end
 
--测试cjson--
function Game.test_cjson_func()
    local path = Util.DataPath.."lua/3rd/cjson/example2.json";
    local text = util.file_load(path);
    LuaHelper.OnJsonCallFunc(text, this.OnJsonCall);
end
 
--cjson callback--
function Game.OnJsonCall(data)
    local obj = json.decode(data);
    print(obj['menu']['id']);
end
 
--销毁--
function Game.OnDestroy()
	--logWarn('OnDestroy--->>>');
end
```

#### step 4
点击菜单LuaFramework/Build Windows Resources，重新在目录：/StreamingAssets/ 生成AssetBundle包。重新把/StreamingAssets/文件夹，包括里面的这些AssetBundle包文件，扔服务器里，运行项目。

此时客户端从服务器的/StreamingAssets目录下载里面所有的AssetBundle资源包，解包并执行，发现此时我们的TestPanel已经被生成了：

<div align=center><img width="60%" src="Other/LuaFramework/18.png"/></div>

>Tips: 可以用代码把框架自带的演示PromptPanel屏蔽掉，在/LuaFramework/Lua/Logic/Game.lua中把这一段屏蔽掉，重新Build Windows Resources，重新把/StreamingAssets/文件夹扔服务器里再运行就没有PromptPanel了。

<div align=center><img width="60%" src="Other/LuaFramework/19.png"/></div>

## 3 Lua Framework 框架结构
### 3-1 文件结构
框架的完整文件结构是这样的：
- Editor：
	- customsetting：添加需要导出注册到Lua的类型列表
	- packager：资源打包

- Examples：自带例子
- Lua：框架自带的Lua源码目录，用户自定义的Lua脚本放这里面，打包的时候会将其按照目录结构生成到StreamingAssets中，再上传到Web服务器上，达到热更。
	- 3rd：第三方插件
		- cjson：json支持
		- luabitop：让lua支持位运算
		- pbc：云风大神早起对protobuf的解析库
		- pblua：网上流传的Lua方案，基于protobuf的protoc-gen-lua
		- sproto：云风大神新作，比pbc更小效率高
	- common：公用的Lua文件目录，就是全局用
		- define：包含变量声明，全局配置
		- functions：常用函数库
		- protocal：通讯协议
	- controller：控制器目录，处理数据，控制面板显示
	- logic：存放管理器类，新加的管理器可以放里面
		- ctrlmanager：管理控制controller层，进而控制view层
		- game：检索并require view文件夹下各个panel文件
		- luaclass：New方法，构建类
	- view：面板显示，走的是Unity GameObject的生命周期的事件调用
	- events：eventlib事件系统
- Luajit：Lua编译器
- Scripts：框架的C#目录
	- common
		- luabehaviour
		- lualoader
	- constdefine
		- appconst
		- managername
		- noticonst
	- controller
	- framework
	- manager
	- network
	- objectpool
	- utility
	- view
- ToLua：tolua的核心目录

### 3-2 MVC框架
Lua Framework中使用了经典的MVC框架。

> MVC全名是Model View Controller，是模型(model)－视图(view)－控制器(controller)的缩写，一种软件设计典范，用一种业务逻辑、数据、界面显示分离的方法组织代码，将业务逻辑聚集到一个部件里面，在改进和个性化定制界面及用户交互的同时，不需要重新编写业务逻辑。

<div align=center><img width="70%" src="Other/LuaFramework/2.png"/></div>

所有的controller在CtrlManager中被注册：
```
-- CtrlManager.lua
function CtrlManager.Init()
	logWarn("CtrlManager.Init----->>>");
	ctrlList[CtrlNames.Prompt] = PromptCtrl.New();
	ctrlList[CtrlNames.Message] = MessageCtrl.New();
	return this;
end
```

通过CtrlManager获取对应的controler对象，调用Awake()方法：
```
-- CtrlManager.lua
local ctrl = CtrlManager.GetCtrl(CtrlNames.Prompt);
if ctrl ~= nil then
    ctrl:Awake();
end
```

controller类中，Awake()方法中调用C#的PanelManager的CreatePanel方法：
```
-- PromptCtrl.lua
function PromptCtrl.Awake()
	logWarn("PromptCtrl.Awake--->>");
	panelMgr:CreatePanel('Prompt', this.OnCreate);
end
```

C#的PanelManager的CreatePanel方法去加载界面预设，并挂上LuaBehaviour脚本（LuaBehaviour脚本，主要是管理panel的生命周期，调用lua中panel的Awake，获取UI元素对象）：
```
-- PromptPanel.lua
local transform;
local gameObject;

PromptPanel = {};
local this = PromptPanel;

--启动事件--
function PromptPanel.Awake(obj)
	gameObject = obj;
	transform = obj.transform;

	this.InitPanel();
	logWarn("Awake lua--->>"..gameObject.name);
end

--初始化面板--
function PromptPanel.InitPanel()
	this.btnOpen = transform:Find("Open").gameObject;
	this.gridParent = transform:Find('ScrollView/Grid');
end

--单击事件--
function PromptPanel.OnDestroy()
	logWarn("OnDestroy---->>>");
end
```

panel的Awake执行完毕后，就会执行controller的OnCreate()，在controller中对UI元素对象添加一些事件和控制：
```
-- PromptCtrl.lua
--启动事件--
function PromptCtrl.OnCreate(obj)
	gameObject = obj;
	transform = obj.transform;

	panel = transform:GetComponent('UIPanel');
	prompt = transform:GetComponent('LuaBehaviour');
	logWarn("Start lua--->>"..gameObject.name);

	prompt:AddClick(PromptPanel.btnOpen, this.OnClick);
	resMgr:LoadPrefab('prompt', { 'PromptItem' }, this.InitPanel);
end
```

### 3-3 LuaManager核心管理器
LuaManager这个管理器是必须的，掌管整个lua虚拟机的生命周期。它主要是加载lua库，加载lua脚本，启动lua虚拟机，执行Main.lua。

### 3-4 GameManager游戏管理器
GameManager负责检测lua逻辑代码的更新检测和加载（Main.lua是在LuaManager中执行的），我们可以在GameManager中DoFile我们自定义的lua脚本，比如Game.lua脚本。

### 3-5 AppConst常量定义
AppConst定义了一些常量。其中AppConst.LuaBundleMode是lua代码AssetBundle模式。它会被赋值给LuaLoader的beZip变量，在加载lua代码的时候，会根据beZip的值去读取lua文件，false则去search path中读取lua文件，否则从外部设置过来的bundle文件中读取lua文件。默认为true。

## 4 Lua Framework 运行流程
### 4-1 执行入口
<div align=center><img width="100%" src="Other/LuaFramework/3.png"/></div>

首先通过Main.cs中的```AppFacade.Instance.StartUp()```启动游戏，这个接口会抛出一个NotiConst.START_UP事件，对应的响应类是StartUpCommand，这里初始化了各种管理器，我们可以根据具体需求进行改造和自定义：
```
using UnityEngine;
using System.Collections;
using LuaFramework;

public class StartUpCommand : ControllerCommand {

    public override void Execute(IMessage message) {
        if (!Util.CheckEnvironment()) return;

        GameObject gameMgr = GameObject.Find("GlobalGenerator");
        if (gameMgr != null) {
            AppView appView = gameMgr.AddComponent<AppView>();
        }
        //-----------------关联命令-----------------------
        AppFacade.Instance.RegisterCommand(NotiConst.DISPATCH_MESSAGE, typeof(SocketCommand));

        //-----------------初始化管理器-----------------------
        AppFacade.Instance.AddManager<LuaManager>(ManagerName.Lua);
        AppFacade.Instance.AddManager<PanelManager>(ManagerName.Panel);
        AppFacade.Instance.AddManager<SoundManager>(ManagerName.Sound);
        AppFacade.Instance.AddManager<TimerManager>(ManagerName.Timer);
        AppFacade.Instance.AddManager<NetworkManager>(ManagerName.Network);
        AppFacade.Instance.AddManager<ResourceManager>(ManagerName.Resource);
        AppFacade.Instance.AddManager<ThreadManager>(ManagerName.Thread);
        AppFacade.Instance.AddManager<ObjectPoolManager>(ManagerName.ObjectPool);
        AppFacade.Instance.AddManager<GameManager>(ManagerName.Game);
    }
}
```

### 4-2 Lua代码读取
LuaLoader和LuaResLoader都继承LuaFileUtils。lua代码会先从LuaFramework.Util.AppContentPath目录解压到LuaFramework.Util.DataPath目录中，lua文件列表信息记录在files.txt中，此文件也会拷贝过去。然后从LuaFramework.Util.DataPath目录中读取lua代码。

<div align=center><img width="70%" src="Other/LuaFramework/4.png"/></div>

之后，再进行远程更新检测，看看用不用热更lua代码，远程url就是AppConst.WebUrl，先下载files.txt，然后再读取lua文件列表进行下载。
启动框架后，会创建GameManager游戏管理器，GameManager可以获取到LuaManager对象，通过LuaManager.CallFunction接口调用。

### 4-3 C#中如何调用lua方法
可以通过LuaManager.CallFunction接口调用，也可以用Util.CallMethod接口调用，两个接口的参数有差异，需要注意。
```
/// LuaManager.CallFunction接口
public object[] CallFunction(string funcName, params object[] args) {
      LuaFunction func = lua.GetFunction(funcName);
      if (func != null) {
          return func.LazyCall(args);
      }
      return null;
  }

/// Util.CallMethod接口
public static object[] CallMethod(string module, string func, params object[] args) {
    LuaManager luaMgr = AppFacade.Instance.GetManager<LuaManager>(ManagerName.Lua);
    if (luaMgr == null) return null;
    return luaMgr.CallFunction(module + "." + func, args);
}
```

### 4-4 lua中如何调用C#方法
假设现在我们有一个C#类：
```
public class MyTest : MonoBehaviour {
    public int myNum;

    public void SayHello() {
        Debug.Log("Hello,I am MyTest,myNum: " + myNum);
    }

    public static void StaticFuncTest() {
        Debug.Log("I am StaticFuncTest");
    }
}
```
我们想在lua中访问这个MyTest类的函数。首先，我们需要在CustomSettings.cs中的customTypeList数组中添加类的注册：```_GT(typeof(MyTest))```

然后然后再单击菜单【Lua】-【Generate All】生成Wrap，生成完我们会看到一个MyTestWrap类：

<div align=center><img width="50%" src="Other/LuaFramework/5.png"/></div>

接下来就可以在lua中访问了。

!>注意AppConst.LuaBundleMode的值要设为false，方便Editor环境下运行lua代码，否则需要先生成AssetBundle才能运行。

调用Game.TestFunc()：
```
function Game.TestFunc()
    -- 静态方法访问
    MyTest.StaticFuncTest()
   
    local go = UnityEngine.GameObject("go")
    local myTest = go:AddComponent(typeof(MyTest))
    
    -- 成员变量
    myTest.myNum = 5
    -- 成员方法
    myTest:SayHello()
end
```

!>注意，静态方法、静态变量、成员变量、成员属性使用 “.” 来访问，比如上面的 myTest.myNum，成员函数使用 “:” 来访问，比如上面的 myTest:SayHello()

## 5 其他lua小技巧
### 5-1 lua中如何使用协程
例：
```
function fib(n)
    local a, b = 0, 1
    while n > 0 do
        a, b = b, a + b
        n = n - 1
    end

    return a
end

function CoFunc()
    print('Coroutine started')    
    for i = 0, 10, 1 do
        print(fib(i))                    
        coroutine.wait(0.1)                     
    end 
    print("current frameCount: "..Time.frameCount)
    coroutine.step()
    print("yield frameCount: "..Time.frameCount)

    local www = UnityEngine.WWW("http://www.baidu.com")
    coroutine.www(www)
    local s = tolua.tolstring(www.bytes)
    print(s:sub(1, 128))
    print('Coroutine ended')
end
```

调用：```coroutine.start(CoFunc)```

如果要stop协程，则需要这样：
```
local co = coroutine.start(CoFunc)
coroutine.stop(co)
```

### 5-2 lua如何解析json
需要解析的json文件：
```
{
    "glossary": {
        "title": "example glossary",
            "GlossDiv": {
				"title": "S",
                "GlossList": {
					"GlossEntry": {
						"ID": "SGML",
                        "SortAs": "SGML",
                        "GlossTerm": "Standard Generalized Mark up Language",
                        "Acronym": "SGML",
                        "Abbrev": "ISO 8879:1986",
                        "GlossDef": {
							"para": "A meta-markup language.",
                            "GlossSeeAlso": ["GML", "XML"]
						},
                        "GlossSee": "markup"
					}
                }
            }
        }
    }
}
```
假设我们已经把上面的json文件的内容保存到变量jsonStr字符串中，现在在lua中要解析它可以这样做：
```
local json = require 'cjson'

function Test(str)
    local data = json.decode(str)
    print(data.glossary.title)
    s = json.encode(data)
    print(s)
end
```
然后调用```Test(jsonStr)```即可。

### 5-3 lua如何调用C#的托管
例：
```
// c#传托管给lua
System.Action<string> cb = (s) => { Debug.Log(s); };
Util.CallMethod("Game", "TestCallBackFunc", cb);
```
```
-- lua调用C#的托管
function Game.TestCallBackFunc(cb)
    if nil ~= cb then
       System.Delegate.DynamicInvoke(cb,"Hello, I am lua, I call Delegate")
    end
end
```

### 5-4 lua如何通过反射调用C#
有时候，我们没有把我们的C#类生成Wrap，但是又需要在lua中调用，这个时候，可以通过反射来调用。

假设我们有一个C#类：
```
// MyClass.cs
public sealed class MyClass {
    // 字段
    public string myName;
    // 属性
    public int myAge { get; set; }
	
	// 静态方法
    public static void SayHello() {
        Debug.Log("Hello, I am MyClass's static func: SayHello");
    }

    public void SayNum(int n) {
        Debug.Log("SayNum: " + n);
    }

    public void SayInfo() {
        Debug.Log("SayInfo, myName: " + myName + ",myAge: " + myAge);
    }
}
```

在lua中可以这样调用：
```
-- Game.lua
function Game.TestReflection()
    require 'tolua.reflection'
    tolua.loadassembly('Assembly-CSharp')
    local BindingFlags = require 'System.Reflection.BindingFlags'

    local t = typeof('MyClass')
    -- 调用静态方法
    local func = tolua.getmethod(t, 'SayHello')
    func:Call()
    func:Destroy()
    func = nil

    -- 实例化
    local obj = tolua.createinstance(t)
    -- 字段
    local field = tolua.getfield(t, 'myName')
    -- 字段Set
    field:Set(obj, "linxinfa")
    -- 字段Get
    print('myName: ' .. field:Get(obj))
	field:Destroy()
	
    -- 属性
    local property = tolua.getproperty(t, 'myAge')
    -- 属性Set
    property:Set(obj, 29, null)
    -- 属性Get
    print('myAge: ' .. property:Get(obj, null))
    property:Destroy()
    
    --public成员方法SayNum
    func = tolua.getmethod(t, 'SayNum', typeof('System.Int32'))
    func:Call(obj, 666)
	func:Destroy()
	
    --public成员方法SayInfo
    func = tolua.getmethod(t, 'SayInfo')
    func:Call(obj)
    func:Destroy()
end
```

### 5-5 nil和null
!>nil是lua对象的空，null表示c#对象的空。假设我们在c#中有一个GameObject对象传递给了lua的对象a，接下来我们把这个GameObject对象Destroy了，并在c#中把这个GameObject对象赋值为null，此时lua中的对象a并不会等于nil
>如果要在lua中判断一个对象是否为空，安全的做法是同时判断nil和null
```
-- lua中对象判空
function IsNilOrNull(o)
	return nil == o or null == o
end
```

### 5-6 查询星期几/年月日
星期查询：
```
-- 1是周日，2是周一，以此类推
function GetTodayWeek()
	local t = os.date("*t", math.floor(os.time()))
	return t.wday
end
```
年月日查询：
```
-- 方法一
function GetTodayYMD()
	local t = os.date("*t", math.floor(os.time()))
	return t.year .. "/" .. t.month .. "/" .. t.day
end

-- 方法二
function GetTodayYMD()
	-- 如果要显示时分秒，则用"%H:%M:%S"
	return os.date("%Y/%m%d", math.floor(os.time()))
end
```

### 5-7 字符串分割
```
-- 参数str是你的字符串，比如"小明|小红|小刚"
-- 参数sep是分隔符，比如"|"
-- 返回值为{"小明","小红","小刚"}
function SplitString(str, sep)
	local sep = sep or " "
	local result = {}
	local pattern = string.format("([^%s]+)", sep)
	string.gsub(s, pattern, function(c) result[#result + 1] = c end)
	return result 
end
```

### 5-8 大数字加逗号分割（数字会转成字符串）
```
-- 参数num是数字，如3428439，转换结果"3,428,439"
function FormatNumStrWithComma(num)
	local numstr = tostring(num)
	local strlen = string.len(numstr)
	local splitStrArr = {}
	for i = strlen, 1, -3 do
		local beginIndex = (i - 2 >= 1) and (i - 2) or 1
		table.insert(splitStrArr, string.sub(numstr, beginIndex, i))
	end
	local cnt = #splitStrArr
	local result = ""
	for i = cnt, 1, -1 do
		if i == cnt then
			result = result .. splitStrArr[i]
		else
			result = result .. "," .. splitStrArr[i]
		end
	end
	return result
end
```

### 5-9 通过组件名字添加组件
```
-- 缓存
local name2Type = {}
-- 参数gameObject物体对象
-- 参数componentName，组件名字，字符串
function AddComponent(gameObject, componentName)
	local component = gameObject:GetComponent(componentName)
	if nil ~= component then return component end

	local componentType = name2Type[componentName]
	if nil == componentType then
		componentType  = System.Type.GetType(componentName)
		if nil == componentType then
			print("AddComponent Error: " .. componentName)
			return nil
		else
			name2Type[componentName] = componentType 
		end
	end
	return gameObject:AddComponent(componentType)
end
```

### 5-10 深拷贝
lua中的table是引用类型，有时候我们为了不破坏原有的table，可能要用到深拷贝：
```
function DeepCopy(t)
	if nil == t then return nil end
	local result = ()
	for k, v in pairs(t) do
		if "table" == type(v) then
			result[k] = DeepCopy(v)
		else
			result[k] = v
		end
	end
	return result
end
```

### 5-11 四舍五入
```
function Round(fnum)
	return math.floor(fnum + 0.5)
end
```

### 5-12 检测字符串是否含有中文
```
-- 需要把C#的System.Text.RegularExpressions.Regex生成Wrap类
function CheckIfStrContainChinese(str)
	return System.Text.RegularExpressions.Regex.IsMatch(str, "[\\u4e00-\\u9fa5]")
end
```

### 5-13 数字的位操作get、set
```
-- 通过索引获取数字的某一位，index从1开始
function GetBitByIndex(num, index)
    if nil == index then
        print("LuaUtil.GetBitByIndex Error, nil == index")
        return 0
    end
    local b = bit32.lshift(1,(index - 1))
    if nil == b then
        print("LuaUtil.GetBitByIndex Error, nil == b")
        return 0
    end
    return bit32.band(num, b)
end

-- 设置数字的某个位为某个值，num：目标数字，index：第几位，从1开始，v：要设置成的值，0或1
function SetBitByIndex(num, index, v)
    local b = bit32.lshift(1,(index - 1))
    if v > 0 then
        num = bit32.bor(num, b)
    else
        b = bit32.bnot(b)
        num = bit32.band(num, b)
    end
    return num
end
```

### 5-14 限制字符长度，超过进行截断
有时候，字符串过长需要截断显示，比如有一个昵称叫“我的名字特别长一行显示不下”，需求上限制最多显示5个字，超过的部分以…替代，即"我的名字特…"。首先要计算含有中文的字符串长度，然后再进行截断：
```
-- 含有中文的字符串长度
function StrRealLen(str)
    if str == nil then return 0 end
    local count = 0
    local i = 1
    while (i < #str) do
        local curByte = string.byte(str, i)
        local byteCount = 1
        if curByte >= 0 and curByte <= 127 then
            byteCount = 1
        elseif curByte >= 192 and curByte <= 223 then
            byteCount = 2
        elseif curByte >= 224 and curByte <= 239 then
            byteCount = 3
        elseif curByte >= 240 and curByte <= 247 then
            byteCount = 4
        end
        local char = string.sub(str, i, i + byteCount - 1)
        i = i + byteCount
        count = count + 1
    end
    return count
end

-- 限制字符长度（多少个字）
-- 参数str，为字符串
-- 参数limit为限制的字数，如8
-- 参数extra为当超过字数时，在尾部显示的字符串，比如"..."
function LimitedStr(str, limit, extra)
    limit = limit or 8
    extra = extra or ""
    local text = ""
	-- 含有中文的字符串长度
    if StrRealLen(str) > limit then
        text = LuaUtil.sub_chars(str, limit) .. "..." .. extra
    else
        text = str .. extra
    end
    return text
end
```

### 5-15 判断字符串A是否以某个字符串B开头
```
-- 判断字符串str是否是以某个字符串start开头
function StringStartsWith(str, start)
    return string.sub(str, 1, string.len(start)) == start
end
```
