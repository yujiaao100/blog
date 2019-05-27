python 数学计算：

符号计算： sympy



series：泰勒展开

diff：求导数

limit：求极限

Symbol 定义符号

atan: arctan(x)

**: n次方

integrate：求积分

log： 这里的默认底数是e

exp（）： e的n次方

pi：特殊值不展开

Matrix([[0,1],[1,x]])  甚至能建立带有符号的矩阵

感觉高数题目好像都可以用python去验证对错了：爽

```python
from sympy import *

x=Symbol('x')

#diff(f,x)求导数
#print(diff(x**2,x))
#limit(f,x,0) 求极限
#print(limit(sin(x)/x,x,0))
#表达式.series(x,0,3)
#print(exp(x).series(x,0,3))
#print(Matrix([[0,1],[1,1]]))  矩阵
#integrate
#print(integrate(x**2,x))

#f=(x/ln(1+x))**(1/x)
#f=1/(ln(1+x)*(x+1))
#f=((1+x)**(2/x)-exp(2))/x
#f=((1+tan(x))**(1/2)-(1+sin(x))**(1/2))/(x**2-x*ln(1+x))
f=(2/pi*atan(x))**(x**2)
print(limit(f,x,oo))

#g=(((exp(x)+exp(2*x)+exp(3*x))/3)**(1/x))

g=(1+x)**(2/x)-exp(2)
l=diff(atan(x),x)
print(l)


#print(exp(x).series(x,0,3))

print(integrate(log(x)**2,x))

```

