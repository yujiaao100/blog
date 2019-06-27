##### 1.各种版本

​	最早的cocos是oc的ios版本 然后国人王哲改了一个cocos2dx cpp版本用各种cpp的黑魔法让cpp 看起来像是oc 这个版本其实也是当年最火的手游引擎 （2.x版本）

##### 	关于3.0版本：

​	当然 这个版本特别不cpp  为了满足看起来像是oc各种乱七八糟的宏定义 之后王哲找来了ios版本的开发者共同开发了3.0+  虽然满足cpp风格 看起来也不错 但是和2.0+ 完全不兼容 这样流失了大量用户 因为引擎这种东西不像是操作系统 而是够用就好 一般公司都会拉过来基础引擎做大量改造 而旧版本停止维护很多轮子又很难升级 加上unity在2d领域的完善 结果比较惨

##### 	关于cocos creater：

​	早期的时候有官方有一个开发工具cocosstudio 这个工具很尴尬 因为cocos引擎 是cpp写的 支持lua js binding 但是studio的技术方案居然是微软wpf（c#）同时维护4种语言你敢信？我觉得这个技术选型非常失败

此时cocos已经被unity3d打的节节败退 不得不去抢web的市场（h5小游戏） 所以有了全新架构的cocos creater

​	首先将cocos 的3d部分 lua绑定等一堆功能去掉形成 cocos-lite 然后使用这个引擎+web套壳+基于Electron（的不开源）的ide 整合到了一起 全部使用前端技术栈 完全放弃lua  

​	大概是这样：开发游戏使用electron的creater 用vscode写代码 然后chrome调试 当web应用去写（毕竟有webgl和canvas）  而发布的时候可以正常发布到web 也可以发布到手机上（使用cocos-lite作为底层）

​	我觉得这就基本上等于将cocos2dx整个砍掉重新弄了一遍 而且将重心完全放在了web上和白鹭去拼 对于大型游戏支持大砍特砍（毕竟手机性能 如果还要上web 那么性能更是个问题） 

​	当然 好处是有的 比如给微信 百度小程序做了一堆适配 你懂得

##### 关于cocosbuilder 和quick cocos

​	因为cocosstudio不好用 所以有人在mac开发了cocosbuilder 

​	因为2.0升级到3.0期间很多人觉得升级麻烦 而且cocos也在放弃lua 用js抢web市场  有人开了一个新的quickcocos项目（算是cocos2dx lua社区版） 据说触控请quick项目发起人廖大去给cocos重新做lua部分 结果没给钱 于是就尴尬了

#### 如何选择

​	现在选择已经很清晰了  全js方向是趋势（虽然我个人还是喜欢lua）cocos creater 一站式完成所有需求 而且还有插件可以导出到cocos2dx（注意 不是lite那个轻量级版本 而是正常的2dx） 

​	当然 如果不想折腾 更好的方案是选择unity3d 唯一的小问题就是不开源 不免费（不过商用的话2w多我记得 并不贵）  白鹭和layabox（默认as3 flash年代的一套工具都可以使用）这两个cocos的竞品也可以考虑下 毕竟没那么多历史负担和不必要的选项干扰