### 关于微分方程

##### 一阶特殊 以及分离变量法：

$$
\frac{dy}{dx}=\lambda y \\\\ 
\quad \frac{1}{y}dy=\lambda dx \\\\ \quad\quad lny=(\lambda x+C)\\\\ \quad\quad y=Ce^{\lambda x}
$$

##### 一阶一般公式

​	
$$
y'+p(x)y=q(x)\\\\
e^{\int p(x)dx}(y'+p(x)y)=e^{\int p(x)dx}*q(x)\\\\
(ye^{\int p(x)dx})'=e^{\int p(x)dx}*q(x)\\\\
y=e^{\int -p(x)dx}(\int e^{\int p(x)dx}*q(x)+C)
$$


特殊：



##### 欧拉方程：

​	

##### 伯努利方程：

$\quad\quad y'+p(x)y=q(x)y^n$ 	两侧同时除$y^n$ 得：

$\quad\quad y'y^{-n}+p(x)y^{1-n}=q(x)$

​	然后令$r(x)=y^{(1-n)}$ 得：

$\quad\quad\frac{1}{1-n}r'+p(x)r=q(x)$

解$r(x)$ 最后就能得到y



#### 可以降低阶的情况

$\quad y''=f(x,y')$ 缺y型

$\quad\quad p(x)=y' \quad \quad=> \frac{dp}{dx}=p'=f(x,p)$

​	两次积分即可(p是x的函数直接替）

$\quad y''=f(y',y)$缺x型

$\quad\quad p(y)=y' \quad =>\quad y''=\frac{dp}{dx} =\frac{dp}{dy}*\frac{dy}{dx}=p\frac{dp}{dy}=f(y,p)$q

$y^{(n)}=f(x)$ 累次积分即可





#### 二阶齐次

​	
$$
y''+py'+qy=0
$$

$$
\begin{bmatrix}y''\\\\y'\end{bmatrix}=\begin{bmatrix}-p&-q\\\\1&0\end{bmatrix} *\begin{bmatrix}y'\\\\y\end{bmatrix}
$$

一般情况：

令 v=（y‘,y）则 v’=（y'',y'） 系数矩阵为得到方程组 
$v'=Av$

$\begin{bmatrix}\frac{dv_1}{dx}\\\\\frac{dv_2}{dx}\end{bmatrix}=\begin{bmatrix}av_1+bv_2\\\\cv_1+dv_2\end{bmatrix}$

设A的特征值是$\lambda_1\quad \lambda_2$ 特征向量为$p1\quad p2$ 则v可以分解为 $v=h_1(x)p_1+h_2(x)p_2$

左右求导得到：$v'=h_1'(x)p1+h_2'(x)p_2$

而带入v‘ 得到 $v'=h_1(x)Ap_1+h_2(x)Ap_2=\lambda_1h_1(x) p_1+\lambda_2h_2(x) p_2$

因此$h_1'(x)=\lambda_1h_1(x) \quad\quad h_2'(x)=\lambda_2h_2(x)$ 

解出$h_1(x)=C_1e^{\lambda_1 x}\quad h_2(x)=C_2e^{\lambda_2x}$

带入v 得到：$v=c_1e^{\lambda_1x}p_1+c_2e^{\lambda_2 x}p_2$



特殊情况$\begin{bmatrix}-p&-q\\\\1&0\end{bmatrix}$的特征值为$\lambda_1 \lambda_2$ 特征向量为$\begin{bmatrix}\lambda_1\\\\1\end{bmatrix}\quad \begin{bmatrix}\lambda_2\\\\1\end{bmatrix}$



因此：$\begin{bmatrix}y'\\\\y\end{bmatrix}=c_1e^{\lambda_1x}\begin{bmatrix}\lambda_1\\\\1\end{bmatrix}+c_2e^{\lambda_2x}\begin{bmatrix}\lambda_2\\\\1\end{bmatrix}$

即：$y=c_1e^{\lambda_1x}+c_2e^{\lambda_2x}​$





更加有意思的情况(目前查到的情况都是方阵 不知道这个东西是不是一定是方阵)

定义 $e^{At}=\begin{bmatrix}e^{a_{11}t}&e^{a_{12}t}&\cdots \quad e^{a_{1n}t}\\\\e^{a_{21}t}&\ddots \\\\\vdots\\\\e^{a_{n1}t} &\cdots&& e^{a_{nn}t}\end{bmatrix}$



$\frac{du}{dx}=Au$  令$u=sv$ 其中s是特征值列排成的矩阵或者理解为 $u(x)=s_1v_1(x)+s_2v_2(x)$

$s\frac{dv}{dx}=Asv$ 	s是常矩阵 所以带入的时候求导可以开出来

$\frac{dv}{dx}=s^{-1}Asv=\Lambda v$

解得：

$\quad\quad v=\begin{bmatrix}e^{\lambda_1x}&0\\\\0&e^{\lambda_2x}\end{bmatrix}\begin{bmatrix}C1\\\\C2\end{bmatrix}$

记录为$v=e^{\Lambda x}v(0)$ 	当x=0时候 能得到v(0)就是 c1 c2组成的向量

出现了$e^{Ax}$ 那么泰勒公式可以用矩阵相加证明 使用泰勒公式 +矩阵$A=s\Lambda s^{-1}$ 容易证明

$e^{At}=Se^{\Lambda t} S^{-1}$

$u(x)=e^{At}u(0)=se^{\Lambda x}s^{-1}u(0)$



