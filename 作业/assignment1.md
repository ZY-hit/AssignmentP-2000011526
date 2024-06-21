# Assignment #1: 拉齐大家Python水平

Updated 0940 GMT+8 Feb 19, 2024

2024 spring, Complied by 张宇,物理学院



**说明：**

1）数算课程的先修课是计概，由于计概学习中可能使用了不同的编程语言，而数算课程要求Python语言，因此第一周作业练习Python编程。如果有同学坚持使用C/C++，也可以，但是建议也要会Python语言。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：Windows 10

Python编程环境：Spyder(Anaconda)


## 1. 题目

### 20742: 泰波拿契數

http://cs101.openjudge.cn/practice/20742/



思路：由前几项递推



##### 代码

```python
#
a=0
b=1
c=1
T=[a,b,c]
n=int(input())
for i in range(29):
    t=T[i]+T[i+1]+T[i+2]
    T.append(t)
print(T[n])

```


代码运行截图 
![alt text](数列-1.png)



### 58A. Chat room

greedy/strings, 1000, http://codeforces.com/problemset/problem/58/A



思路：循环，检索字符串中的字母



##### 代码

```python
# -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""

s=input()
l=len(s)
S=[]
for i in range(l):
    S.append(s[i])
A=0

for i in range(l):
    if S[i]=='h':
        for j in range(i+1,l):
           if S[j]=='e':
                for k in range(j+1,l):
                   if S[k]=='l':
                        for m in range(k+1,l):
                           if S[m]=='l':
                              for n in range(m+1,l):
                                  if S[n]=='o':
                                     A=1

if A==1:
    print('YES')
else:
    print('NO')

```


代码运行截图 
![alt text](<chat room-1.png>)


### 118A. String Task

implementation/strings, 1000, http://codeforces.com/problemset/problem/118/A




##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""

s=input().lower()
l=len(s)
S=[]
for i in range(l):
    if s[i]!='e'and s[i]!='a'and s[i]!='i'and s[i]!='o'and s[i]!='u'and s[i]!='y':
        S.append('.')
        S.append(s[i])
        
print(''.join(S))


```

代码运行截图
![alt text](<string task-1.png>)





### 22359: Goldbach Conjecture

http://cs101.openjudge.cn/practice/22359/



思路：



##### 代码

```python
# 

```



代码运行截图





### 23563: 多项式时间复杂度

http://cs101.openjudge.cn/practice/23563/



思路：根据多项式的特定符号分割字符串，找到需要的幂指数



##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
I=input()
l=[]
for i in I:
    l.append(i)
l.append('+')
l.append('a')
l.append('a')
L=len(l)
a=[]
for i in range(L):
    if l[i]=='^':
        if l[i-2]!='0':
           b=[]
           for j in range(10):
              if l[i+j+1]!="+":
                 b.append(l[i+j+1])
              else:
                 a.append(''.join(b))
                 break
        else:
            a.append(0)
for i in range(len(a)):
    a[i]=int(a[i])
M=str(max(a))
m='n^'+M
print(m)

```



代码运行截图 
![alt text](<string task-2.png>)




### 24684: 直播计票

http://cs101.openjudge.cn/practice/24684/



思路：混合使用字典和元组



##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""


T=list(map(int,input().split()))
S=set(T)
D={}
O=[]
for i in S:
    D.update({i:T.count(i)})
N=list(D.items())
N.sort(key=lambda x:x[1],reverse=True)
O.append(N[0][0])
for i in range(len(N)-1):
    if N[i+1][1]!=N[0][1]:
        break
    else:
        O.append(N[i+1][0])
O.sort()
O=[str(i) for i in O]
o=" ".join(O)
print(o)

```



代码运行截图 
![alt text](计票-1.png)




## 2. 学习总结和收获

复习了被搁置已久的python编程，熟悉了openjudge和codeforces的应用。




