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

   c服务->snlua服务(c语言代码实现加载lua虚拟机功能)->snaxd服务(lua服务  加载lua snax模块函数 执行init函数)->snax

   snax.newservice("名称"，“初始化参数”)  执行init初始化可以通过发消息 变长参数的方式发送参数到init函数执行

   

    #### 	 其他各种服务：

   ### gateserver:

   ​	早期版本使用c实现 目前用lua服务snax 的一个扩展 这个地方最开始看代码的时候回乱掉 因为有c服务的代码会导致分析流程的时候分析到c服务上面结果发现没实现

   ### 	agent,watchdog和gateserver

   ​			watchdog是agent和gateserver的管理服务 负责gateserver的启动 agent的增加和踢下线等工作	watchdog是学生和老师的管理员 可以负责学生agent入学 被开除等

   snax:

   ​	 response  需要返回函数（rpc调用）

   ​        accept       不需要返回函数

   ​        init() 启动

   ​        exit（）退出      




   https://github.com/cloudwu/skynet/wiki

   https://skynetclub.github.io/

   https://skynetclub.github.io/