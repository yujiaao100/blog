## 概率论和数理统计相关

##### 基本概念:

##### 离散or连续：

##### 基本分布：

##### 函数分布：

##### 多个随机变量的分布：

##### 大数定律和中心极限定理：

##### 抽样分布：

##### 假设检验和参数估计：

​	



##### 难以理解的地方：

​	二维随机变量及其分布：

​	假设X Y是两个随机变量  他们的联合分布函数是f(x,y)  那么这个分布是二维的（废话） 但是 Z=X+Y 是1维度随机变量（X+Y=1 X+Y=2 整体是一个事件）这个概率分布（大写求和）如下

$\quad\quad F_Z(z)=\iint_{x+y<=z}f(x,y)dxdy=\int^{+oo}_{-oo}dx\int^{z-x}_{-oo}f(x,y)dy$

​	这个表达式是关于z的函数 可以对z求导 令$G(z,x)=\int^{z-x}_{-oo}f(x,y)dy$:则原式可以变为$\int^{+oo}_{-oo}G(z,x)dx$

然后求导 我们假设区间范围是a，b （OO不太好讨论）那么定积分的定义是分割代替求和取极限 就是将G（z，x）在a 到b上分割成了无数的小函数每一个小段都可以看成z的函数 因为代替 所以x是常数 那么总的导数就是每一小段的导数的和 如果将G(z,x) 看成二元函数 也就是偏导数  即 $\int^{+oo}_{-oo} \frac{\partial G(z,x)}{\partial z}dx$

$G(z,x)=\int^{z-x}_{-oo}f(x,y)dy$ 对z求偏导 那么这个地方就是变限积分函数求导 带入即可 不过要注意 z-x 这个表达式也需要求导 （假如z-2x 那么就要带系数）即  $\frac{\int^{z-x}_{-oo}f(x,y)dy}{\partial z}=f(x,z-x)$ 带入替换然后

整理得：

$\quad\quad F_Z(z)=\iint_{x+y<=z}f(x,y)dxdy=\int^{+oo}_{-oo}dx\int^{z-x}_{-oo}f(x,y)dy$

$\quad f_Z(z)=F_Z^{'}(z)==\int^{+oo}_{-oo}f(x,z-x)dx$

特殊情况：

​	若X，Y 独立则$f(x,y)=f_X(x)f_Y(y)$ 因此：

$\quad f_Z(z)=\int^{+oo}_{-oo}f_X(x)f_Y(z-x)dx$



##### 关于样本自由度 n-1 $\chi^2$分布 t分布的n-1

+ 方差：

$\quad S^2=\frac{1}{n-1}\Sigma_{i=1}^{n}(X-\overline x)^2$

$\quad\quad E\Sigma_{i=1}^{n}(X-\overline x)=E\Sigma(X-u+u-\overline x)^2$

$\quad\quad=E\Sigma\{(X-u)^2+(u-\overline x)^2+2(X-u)(u-\overline x)\}$

因为$\Sigma X=\Sigma\overline x=n\overline x$  

所以复杂部分$\Sigma(X-u)(u-\overline x)=\Sigma(Xu-X\overline x-u^2+u\overline x)=\Sigma \overline xu-\Sigma \overline x^2-\Sigma u^2+\Sigma u\overline x=-\Sigma (\overline x-u)^2$

带入得到$E\Sigma_{i=1}^{n}(X-\overline x)^2=E\{\Sigma(X-u)^2-\Sigma(u-\overline x)^2\}$

而$X\sim N(u,\sigma^2)\quad \overline x\sim (u,\frac{\sigma^2}{n})$

$\quad\quad \Sigma Dx=\Sigma E(X-u)^2=n\sigma^2 \quad \Sigma D\overline x=\Sigma(\overline x-u)^2=\sigma^2$

即$E\Sigma_{i=1}^{n}(X-\overline x)=(n-1)\sigma^2$

所以这里的$S^2$  的系数为n-1	

+ $\chi^2分布$

  $\frac{(n-1)S^2}{\sigma^2}=\frac{\Sigma(X-\overline x)^2}{\sigma^2}=\frac{\Sigma(X-u+u-\overline x)^2}{\sigma^2}$

  同方差的证明方法一样：

  原式=$\frac{\Sigma(X-u)^2}{\sigma^2}-\frac{\Sigma(\overline x-u)^2}{\sigma^2}$

  $\overline x \sim N(u,\frac{\sigma^2}{n})$

  $\frac{\sqrt n \Sigma(\overline x-u)^2}{\sigma^2} \sim \chi^2(n)$

  n=1时

  $\frac{\Sigma(\overline x-u)^2}{\sigma^2} \sim \chi^2(1)$

  原式=$\chi^2(n)-\chi^2(1)=\chi^2(n-1)$

+ t分布(有了前面的基础非常容易理解) （有问题）

  $\overline x \sim N(u,\frac{\sigma^2}{n}) \quad  \frac{\sqrt n(\overline x-u)}{\sigma} \sim N(0,1)$

  $\frac{(n-1)S^2}{\sigma^2}=\chi^2(n-1)\quad  \frac{\chi^2(n-1)}{n-1}=\frac{S^2}{\sigma^2}$

  $\frac{(\overline x -u)}{S/\sqrt n}=\frac{\sqrt n(\overline x -u)}{\sqrt {\frac{S^2}{\sigma^2}}} \sim \frac{N(0,1)}{\sqrt \frac{\chi^2(n-1)}{n-1} }=t(n-1)$

  

  ​	

