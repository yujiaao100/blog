### 新坑：skynet分析



#### 本质：

​	c+lua实现的actor模型

#### 服务概念：

#### 	

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

### agent：watchdog和gateserver

​	watchdog是agent和gateserver的管理服务 负责gateserver的启动 agent的增加和踢下线等工作

 	watchdog是学生和老师的管理员 可以负责学生agent入学 被开除等

​	

