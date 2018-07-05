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
| service     | lua服务                                               |
| examples    | 样例例子                                              |
| test        | 测试功能的示例代码                                    |
| skynet-src  | 编译配置 readme等常用配置文件                         |
| 其他文件    | Makefile readme.md等配置文件                          |

#### 编译：

​	目前支持*nix系统 windows可以考虑用wsl子系统编译使用测试

#### 通讯协议：sproto

​		



#### 内置服务：

##### 	大类型：

- ##### 	 c服务：

   ##### 	 	这部底层服务比较少 logger 和snlua（也就是lua虚拟机的服务）    我觉得除了非常消耗性能的服务 其他的应该都可以挂lua虚拟机了  gate服务曾经用c实现过一个版本 后来也被云凤大大改成了snlua的版本 不过可以用service-src里面的代码作为一个底层服务的参考

- ##### 	  lua服务：snlua 本质上是c服务+lua虚拟机

   ##### 	 	service下所有 example下面的watchdog agent的demo(我觉得service下的服务基本不需要修改了 demo需要根据需求自己调整)

- ##### 	 snax：本质上是特殊的snlua服务 化简了snlua服务的一些操作

   

### agent：watchdog和gateserver

​	watchdog是agent和gateserver的管理服务 负责gateserver的启动 agent的增加和踢下线等工作

 	watchdog是学生和老师的管理员 可以负责学生agent入学 被开除等