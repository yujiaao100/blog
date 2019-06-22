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

##### 伯努利方程：

$y'+p(x)y=q(x)y^n$ 	两侧同时除$y^n$ 得：

$y'y^{-n}+p(x)y^{1-n}=q(x)$

然后令$r(x)=y^{(1-n)}$ 得：

$\frac{1}{1-n}r'+p(x)r=q(x)$

解$r(x)$ 最后就能得到y





#### 二阶非齐次

​	
$$
y''+py'+qy=0
$$

$$
\begin{bmatrix}y''\\\\y'\end{bmatrix}=\begin{bmatrix}-p&-q\\\\1&0\end{bmatrix} *\begin{bmatrix}y'\\\\y\end{bmatrix}
$$

令 v=（y‘,y）则 v’=（y'',y'） 系数矩阵为得到方程组 
$$
v'=Av
$$
使用特征值 特征向量相关方法 可以得到  （y‘’，y）= （$\lambda_1$ y',$\lambda_2$ y） 即

y'=C1$e^{\lambda_1x}$ => $y=C_3e^{\lambda_1 x}+C4$ 但是 带入 $y''+py'+qy=0$ C4 一定是0 

 $y=C_2e^{\lambda_2x}$

所以 $e^{\lambda_1x}\quad\quad​$ $e^{\lambda_2x}​$	是 微分方程的两个通解



