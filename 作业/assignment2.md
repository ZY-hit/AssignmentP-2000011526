# Assignment #2: 编程练习

Updated 0953 GMT+8 Feb 24, 2024

2024 spring, Complied by 张宇，物理学院



**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:
- Learn about Time and Space complexities
- Learn the basics of individual Data Structures
- Learn the basics of Algorithms
- Practice Problems on DSA

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**


操作系统：Windows 10

Python编程环境：Spyder(Anaconda)



## 1. 题目

### 27653: Fraction类

http://cs101.openjudge.cn/2024sp_routine/27653/




##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
def gcd(m,n):
    while m%n != 0:
        oldm = m
        oldn = n
        m = oldn
        n = oldm%oldn
    return n
class Fraction:
     def __init__(self,top,bottom):
     
         self.num=top
         self.den=bottom
     def show(self):
         print(self.num,'/',self.den)
     def __add__(self,otherfraction):
         
          newnum=(self.num*otherfraction.den)+(self.den*otherfraction.num)
          newden=(self.den*otherfraction.den)
          common=gcd(newnum,newden)
          
          return Fraction(newnum//common,newden//common)
     def __str__(self):
         return str(self.num)+"/"+str(self.den)

k=Fraction(0,1)
l=list(map(int,input().split()))
for i in range(int(len(l)/2)):
    k=k+Fraction(l[2*i],l[2*i+1])
print(k)


```



代码运行截图 
![alt text](1-1.png)




### 04110: 圣诞老人的礼物-Santa Clau’s Gifts

greedy/dp, http://cs101.openjudge.cn/practice/04110



思路：贪心



##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
n,m=map(int,input().split())
V=0
L=[]
k=0
j=0
for i in range(n):
    v,w=map(int,input().split())
    k=k+w
    j=j+v
    a=[v,w,v/w]
    L.append(a)
L.sort(key=lambda x:x[2],reverse=True)
if k<=m:
    V=j
else:
    p=0
    for i in range(n):
        p=p+L[i][1]
        if p<=m:
           V=V+L[i][0]
        else:
            V=V+(m+L[i][1]-p)*L[i][2]
            break
print('%.1f'%V)


```



代码运行截图 
![alt text](2-1.png)




### 18182: 打怪兽

implementation/sortings/data structures, http://cs101.openjudge.cn/practice/18182/



##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
N=int(input())
for i in range(N):
   n,m,b=map(int,input().split())
   l=[]
   for j in range(n):
      l1=[int(x)for x in input().split()]
      l.append(l1)
   l.sort(key=lambda x:(x[0],-x[1]))
   a=1
   c=0
   for j in l:
       if b<=0:
           break
       if j[0]==a and c<m:
           b=b-j[1]
           c=c+1
       elif j[0]>a or j[0]<a:
           c=1
           b=b-j[1]
           a=j[0]
   if b>0:
        print('alive')
   else:
        print(a)


```



代码运行截图 
![alt text](打怪兽-1.png)




### 230B. T-primes

binary search/implementation/math/number theory, 1300, http://codeforces.com/problemset/problem/230/B



思路：



##### 代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 1364A. XXXXX

brute force/data structures/number theory/two pointers, 1200, https://codeforces.com/problemset/problem/1364/A



思路：



##### 代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 18176: 2050年成绩计算

http://cs101.openjudge.cn/practice/18176/



思路：



##### 代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获

本次作业较上次难度增加，需要先考虑好采用何种方式解决问题，让问题更简单（防止超时）。





