# 定义

# 学习策略

# 算法实现
## 原始形式
```python
import matplotlib.pyplot as plt
import numpy as np

f1 = plt.figure(1)
data_set = np.array([[3,3,1],[4,3,1],[1,1,-1],[2,4,1],[0,0,-1],[2,0,-1],[6,1,-1]])
plt.scatter(data_set[np.where(data_set[:,2] == 1)][:,0],data_set[np.where(data_set[:,2] == 1)][:,1],marker = 'x', color = 'm')
plt.scatter(data_set[np.where(data_set[:,2] == -1)][:,0],data_set[np.where(data_set[:,2] == -1)][:,1],marker = 'o', color = 'g')
length = len(data_set)
rate = 1
w = np.array([0,0])
b = 0
flag = True
x = np.linspace(-1,5,10)

while flag == True :
	flag = False
	for i in range(length) :
		if ( data_set[i][2] * (w.dot(data_set[i,0:2]) + b )) <= 0 :
			w = w + rate * data_set[i][2] * data_set[i,0:2]
			b = b + rate * data_set[i][2]
			flag = True
			print(w,b)

plt.plot(x,(-b - w[0] * x) / w[1],'r')
plt.show()
print(w,b)
```
输出结果：
```
[3 3] 1
[2 2] 0
[2 2] -1
[0 2] -2
[-6  1] -3
[-3  4] -2
[1 7] -1
[0 6] -2
[-6  5] -3
[-3  8] -2
[-4  7] -3
[-5  6] -4
[-2  9] -3
[-3  8] -4
[-4  7] -5
[ 0 10] -4
[-1  9] -5
[-2  8] -6
[-3  7] -7
```
![](https://github.com/CHYbeta/chybeta.github.io/blob/master/images/pic/20170708/1.jpg?raw=true)

## 对偶形式

## 利用tensorflow

## 利用sklearn