### 新坑：skynet分析



#### 本质：

​	c+lua实现的actor模型

#### 服务概念：

​	

##### 目录结构：

| 3rd         | 第三方库 目前有lua jemalloc lua-md5 lpeg 四个第三方库 |
| ----------- | :---------------------------------------------------- |
| cservice    | c服务（so文件）                                       |
| service-src | c服务源码                                             |
| lualib      | lua库                                                 |
| luaclib     | lua调用的c库                                          |
| lualib-src     | lua调用的c库源码                                       |
| service     | lua服务                                               |
| examples    | 样例例子                                              |
| test        | 测试功能的示例代码                                    |
| skynet-src  | skynet核心源码             |
| 其他文件    | Makefile readme.md等配置文件                          |

#### 关于lua 和c：

​	这是lua的特色所在 lua和c可以相互调用 可以用c语言开一个lua虚拟机直接调用lua代码返回到交互栈 同时lua本身也可以动态调用so（dll）库的代码 

#### 编译：

​	目前支持*nix系统 windows可以考虑用wsl子系统编译使用测试

#### 通讯协议：sproto



#### 相关库：

#### 内置服务：

- ##### 	 c服务：
   ​	这部底层服务比较少 logger 和snlua（也就是lua虚拟机的服务）    我觉得除了非常消耗性能的服务 其他的应该都可以挂lua虚拟机了  gate服务曾经用c实现过一个版本 后来也被云凤大大改成了snlua的版本 不过可以用service-src里面的代码作为一个底层服务的参考 （每个服务有四个函数 名称+create 名称__+init 名称+cb 名称+release 分别对应创建 初始化 回调函数（callback） 释放）

   ##### 	 	lua服务：snlua 本质上是c服务+lua虚拟机

   ​	service下所有 example下面的watchdog agent的demo(我觉得service下的服务基本不需要修改了 demo需要根据需求自己调整)

    ##### 	 snax系列：

   ​	snaxd服务 ->snlua服务

    	本质上是特殊的snlua服务 化简了snlua服务的一些操作 用于实现rpc调用热更新等功能 参考test里面的testping 和pingserver testping产生

   ​	当然 除了普通snax外 云风大大给默认的gateserver loginserver和msrserver 提供了两个通用模板 也归入snax目录里面去了 （lualib/snax/ ）

   PTYPE_RESERVED_SNAX 这是核心源码给snax预留的处理宏定义 

   ##### 级别分析:

   ​	c服务->snlua服务(c语言代码实现加载lua虚拟机功能)->snaxd服务(lua服务  加载lua snax模块函数 执行init函数)->snax

   snax.newservice("名称"，“初始化参数”)  执行init初始化可以通过发消息 变长参数的方式发送参数到init函数执行

   底层（skynet-src）定义的重要信息

   最底层的服务：
   	#define THREAD_WORKER 0
   	#define THREAD_MAIN 1
   	#define THREAD_SOCKET 2
   	#define THREAD_TIMER 3
   	#define THREAD_MONITOR 4

   消息类型：这里的类型有些用到了 有些没用到 也可以注册其他的但是默认提供了一些有固定的容易理解的语义而且某些系统库会发送某些消息

   	#define PTYPE_TEXT 0
   	#define PTYPE_RESPONSE 1
   	#define PTYPE_MULTICAST 2
   	#define PTYPE_CLIENT 3
   	#define PTYPE_SYSTEM 4
   	#define PTYPE_HARBOR 5
   	#define PTYPE_SOCKET 6
   	// read lualib/skynet.lua examples/simplemonitor.lua
   	#define PTYPE_ERROR 7
   	// read lualib/skynet.lua lualib/mqueue.lua lualib/snax.lua
   	#define PTYPE_RESERVED_QUEUE 8
   	#define PTYPE_RESERVED_DEBUG 9
   	#define PTYPE_RESERVED_LUA 10
   	#define PTYPE_RESERVED_SNAX 11

    #### 	 其他各种服务：

   ### gateserver:

   ​	早期版本使用c实现 目前用lua服务snax 的一个扩展 这个地方最开始看代码的时候回乱掉 因为有c服务的代码会导致分析流程的时候分析到c服务上面结果发现没实现

   ### 	agent,watchdog和gateserver

   ​			watchdog是agent和gateserver的管理服务 负责gateserver的启动 agent的增加和踢下线等工作	watchdog是学生和老师的管理员 可以负责学生agent入学 被开除等

   #### snax:

   ​	 response  需要返回函数（rpc调用）

   ​        accept       不需要返回函数

   ​        init() 启动

   ​        exit（）退出  

   #### 关于socket：

   ​	skynet提供了一个socketdriver 这个是最底层的socket服务器（lua-socket(capi)->skynet-src）

   ​	socketdriver.start()之后会将发送socket消息到服务进行处理 然后服务绑定注册socket消息的处理方式（参考默认gateserver）

   ​	因为socketdriver处理起来比较麻烦因此提供默认方式socket socket底层是调用socketdriver 也会绑定默认socket消息处理方式

   ​	小坑：socket.start(id,func)后 需要在函数内部和转发后的服务再次socket.start(id)才能使用服务这时候start不传递函数就是允许服务接受对应id的消息 只要连接后获得了id 就可以在任何其他服务中使用：参考testsocket.lua

   #### 关于message消息：

   ​	skynet的本质是一个lightuserdata 也就是c指针（lightuserdata连gc都没有） 代码里面一般用msg，sz即指针和数据长度 

   ​	相关函数：

   ​	1.function pack()（返回msg,sz的消息指针+长度）（）

   ​	2.function unpack(msg,sz){--将c指针msg和长度转换为 dispatch 的 。。。参数}

   ​	3.function dispatch（session，source，cmd，...）回调函数前两个参数是固定的  后面的参数由unpack 执行后函数提供

   ```lua
   skynet.register_protocol {
     name = "text",
     id = skynet.PTYPE_TEXT,
     pack = function(m) return tostring(m) end,--return msg,sz
     unpack = skynet.tostring,--function(msg,size)
     --dispatch=function(id,session,...)
   }
   ```

```lua
local CMD = {}

skynet.dispatch("lua", function(session, source, cmd, ...)
  local f = assert(CMD[cmd])
  f(...)
end)
```


   https://github.com/cloudwu/skynet/wiki

   https://skynetclub.github.io/

   https://skynetclub.github.io/