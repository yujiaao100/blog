### 重新整理线性代数相关知识

##### 线性代数两个基础工具（研究内容）

1. ##### 向量：

   本质：一堆数字的排列

2. ##### 矩阵：

  本质：一堆行向量列排or一堆列向量横着排列or一个二维数字表

##### 方阵的特殊值：

1. 特征值：

   

2. 行列式：

   

##### 核心内容1：矩阵乘法：

​	矩阵*列向量:方程组形式：

$\quad\quad\begin{bmatrix}a&b\\\\c&d\end{bmatrix}\begin{bmatrix}x_1\\\\x_2\end{bmatrix}=\begin{bmatrix}y_1\\\\y_2\end{bmatrix}$$\quad\quad\begin{cases}ax_1+bx_2=y_1\\\\cx_1+dx_2=y_2\end{cases}$

​	矩阵*列向量:线性组合形式：

$\quad\quad\begin{bmatrix}a&b\\\\c&d\end{bmatrix}\begin{bmatrix}x_1\\\\x_2\end{bmatrix}=\begin{bmatrix}y_1\\\\y_2\end{bmatrix} $ $\quad\quad\begin{bmatrix}a\\\\c\end{bmatrix}x_1+\begin{bmatrix}b\\\\d\end{bmatrix}x_2=\begin{bmatrix}y_1\\\\y_2\end{bmatrix}$

​	矩阵和多个列向量乘积：假设A是矩阵 v{1...n}是**列向量** 而$(v_1,v_2,\cdots,v_n)$是一个矩阵

$\quad\quad A(v_1,v_2,\cdots,v_n)=(Av_1,Av_2,\cdots,Av_n)$

​	

​	行向量*矩阵的方程形式：

$\quad\quad[x_1,x_2]\begin{bmatrix}a&b\\\\c&d\end{bmatrix}=[y_1,y_2]$$\quad\quad \begin{cases}ax_1+cx_2=y_1\\\\bx_1+dx_2=y_2\end{cases}$

​	行向量*矩阵的线性组合形式：(因为通常大家都将列向量为默认 所以立起来看好像舒服点 不过容易错 因为都				是转置)

$\quad\quad[x_1,x_2]\begin{bmatrix}a&b\\\\c&d\end{bmatrix}=[y_1,y_2]$$\quad\quad[a,b]x_1+[c,d]x_2=[y_1,y_2]$$\quad\begin{bmatrix}a\\\\b\end{bmatrix}x_1+\begin{bmatrix}c\\\\d\end{bmatrix}x_2=\begin{bmatrix}y_1\\\\y_2\end{bmatrix}$

​	多行和矩阵乘积：假设矩阵为A $\overline{v_1}\overline{v_2}\cdots\overline{v_n}$ 是行向量 则：

$\quad\quad\begin{bmatrix}\overline{v_1}\\\\\overline{v_2}\\\\\vdots\\\\\overline{v_n}\end{bmatrix}A=\begin{bmatrix}\overline{v_1}A\\\\\overline{v_2}A\\\\\vdots\\\\\overline{v_n}A\end{bmatrix}$



​	列向量*行向量：——类似二次型

$\quad\quad\begin{bmatrix}x_1\\\\x_2\\\\\vdots\\\\x_n\end{bmatrix}[x_1,x_2,\cdots,x_n]=\begin{bmatrix}x_1*x_1&x_1*x_2&\cdots&x_1*x_n\\\\x_2*x_1&\ddots&&\vdots\\\\\vdots\\\\x_n*x_1&\cdots&\cdots&x_n*x_n\end{bmatrix}$

​	假设 $x_1,x_2,\cdots x_n$是列向量 $y_1^T,y_2^T,\cdots y_n^T$是行向量(一个按照列分块 一个按照行分块 将矩阵乘法表示为简单的乘积形式)

$\quad\quad\begin{bmatrix}x_1&x_2&\cdots&x_n\end{bmatrix}*\begin{bmatrix}y_1^T\\\\y_2^T\\\\\vdots\\\\y_n^T\end{bmatrix}=x_1y_1^T+x_2y_2^T+\cdots x_ny_n^T$

​	

​       **矩阵乘积可以分块，只要分块满足可以乘即可:**

​	普通形式：

$\quad\quad sum_{ij}=\sum_{m=1}^{m=max}a_{im}*b_{mj}$

​	

##### 核心内容2 行列式：



1. det |E|=1  单位方阵行列式为1

2. 交换行/列 行列式符号发生改变

3. 行列线性可拆分
   $$
   \begin{bmatrix}
   (a+x)^T\\\\b^T\\\\c^T
   \end{bmatrix}  =\quad\quad 
   \begin{bmatrix}
   a^T\\\\b^T\\\\c^T
   \end{bmatrix} +\quad\quad
   \begin{bmatrix}
   x^T\\\\b^T\\\\c^T
   \end{bmatrix}
   $$

4. 两行或两列相等 行列式值为0

5. 可以进行初等行变换或者列变换（消元） 行列式不变

6. 某行或某列全部是0 对应秩<n 矩阵不可逆

7. 上/下三角行列式的值为对角线元素乘积

8. det|AB|=det|A|*det|B|

9. det|A|=0 不可逆

10. 提取公因式（这里和矩阵不同 只要一行或列有公因式那么就能提取） 
    $$
    det|2A|=2^n*det|A|
    $$

11. 转置行列式值不变

12. 某个元素的余子式不受到该元素所在行/列影响
    $$
    \begin{matrix}
    a_{11}&a_{12}&a_{13}\\\\
    a_{21}&a_{22}&a_{23}\\\\
    a_{31}&a_{32}&a_{33}
    \end{matrix}
    $$
    比如这样一个矩阵 a11的余子式A11和a11 a12 a21等元素无关 只是和a22 a23 a32 a33有关

    这样可以替换某一行某一列  比如a11\*A11+a12\*A12+a13\*A13 和b11\*A11+b12*A12+b13\*A13

    这种情况下A11和b里面的A11是相同的 
    $$
    \begin{matrix}
    a_{11}&a_{12}&a_{13}\\\\
    a_{21}&a_{22}&a_{23}\\\\
    a_{31}&a_{32}&a_{33}
    \end{matrix} \quad\quad
    \begin{matrix}
    b_{11}&b_{12}&b_{13}\\\\
    a_{21}&a_{22}&a_{23}\\\\
    a_{31}&a_{32}&a_{33}
    \end{matrix}
    $$
    eg：求a21\*A11+a22\*A12+a23\*A13  （第二行*第一行余子式） 那么只要将行列式的第二行替换为a11 a12 a13 就行了 行列式的值为0 即替换第二行为第一行 按照第二行展开
    $$
    \begin{matrix}
    a_{11}&a_{12}&a_{13}\\\\
    a_{11}&a_{12}&a_{13}\\\\
    a_{31}&a_{32}&a_{33}
    \end{matrix}
    $$





