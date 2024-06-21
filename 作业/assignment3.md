# Assignment #3: March月考

Updated 1537 GMT+8 March 6, 2024

2024 spring, Complied by 张宇，物理学院



**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:
- Learn about Time and Space complexities
- Learn the basics of individual Data Structures
- Learn the basics of Algorithms
- Practice Problems on DSA

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**


操作系统:Windows10

Python编程环境：Spyder(Anaconda)


## 1. 题目

**02945: 拦截导弹**

http://cs101.openjudge.cn/practice/02945/



思路：动态规划



##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
n=int(input())
l=list(map(int,input().split()))
a=[]
for i in range(n):
   a.append([l[i],1])
for i in range(n):
    for j in range(i):
        if a[j][0]>=a[i][0] and a[j][1]>=a[i][1]:
            a[i][1]=a[j][1]+1
c=[]
for i in range(n):
    c.append(a[i][1])
print(max(c))

```



代码运行截图 
![alt text](拦截导弹-1.png)




**04147:汉诺塔问题(Tower of Hanoi)**

http://cs101.openjudge.cn/practice/04147



思路：递归



##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
n,a,b,c=input().split()
def move(n,A,B,C):
    if n==1:
        l=[str(n),':',A,'->',C]
        print(''.join(l))
    else:
        move(n-1,A,C,B)
        l=[str(n),':',A,'->',C]
        print(''.join(l))
        move(n-1,B,A,C)
move(int(n),a,b,c) 
    

```

代码运行截图 
![alt text](汉诺塔-1.png)





**03253: 约瑟夫问题No.2**

http://cs101.openjudge.cn/practice/03253



思路：



##### 代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





**21554:排队做实验 (greedy)v0.2**

http://cs101.openjudge.cn/practice/21554



思路：排序，注意每个人对于每个前面的人都得等一次，自己做实验不用等。



##### 代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
n=int(input())
l=list(map(int,input().split()))
a=[]
for i in range(n):
    a.append([i+1,l[i]])
a.sort(key=lambda x:x[1])

T=0
for i in range(n-1):
    T=T+(n-1-i)*a[i][1]
t=T/n
o=[]
for i in range(n):
  o.append(str(a[i][0]))
print(" ".join(o))
print('%.2f'% t)

```



代码运行截图
![alt text](实验-1.png)




**19963:买学区房**

http://cs101.openjudge.cn/practice/19963



思路：排序，注意中位数在列表中的的位置参数与正整数稍有不同。



##### 代码

```python
# # -*- coding: utf-8 -*-
"""
Created on Tue Mar 12 17:10:18 2024

@author: 张宇20200808
"""
n=int(input())
p = [i[1:-1] for i in input().split()]
d = [ sum(map(int,i.split(','))) for i in p]
m=list(map(int,input().split()))
l=[0]*n
for i in range(n):
    l[i]=d[i]/m[i]
L=[]
M=[]
for i in range(n):
    L.append([i+1,l[i]])
    M.append([i+1,m[i]])
L.sort(key=lambda x:x[1])
M.sort(key=lambda x:x[1])

a=[]
b=[]
if n%2==0:
    j=(L[int(n/2)-1][1]+L[int(n/2)][1])/2
    k=(M[int(n/2)-1][1]+M[int(n/2)][1])/2
    for i in range(int(n/2),n):
        if L[i][1]>j:
            a.append(L[i][0])
    for i in range(int(n/2)):
        if M[i][1]<k:
            b.append(M[i][0])
else:
    j=L[int((n-1)/2)][1]
    k=M[int((n-1)/2)][1]
    for i in range(int((n+1)/2),n):
        if L[i][1]>j:
            a.append(L[i][0])
    for i in range(int((n-1)/2)):
        if M[i][1]<k:
            b.append(M[i][0])
A=set(a)
B=set(b)
print(len(A&B))

```



代码运行截图 
![alt text](学区房-1.png)





**27300: 模型整理**

http://cs101.openjudge.cn/practice/27300



思路：



##### 代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获
本次题目综合递归、贪心、动态规划等，具有一定难度，如果是上机考试，预计我只能在限时时间内完成2、3道，需要多加练习。不然相当长的时间花在打较长的代码上。





