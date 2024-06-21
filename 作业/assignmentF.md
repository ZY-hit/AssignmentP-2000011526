# Assignment #F: All-Killed 满分

Updated 1844 GMT+8 May 20, 2024

2024 spring, Complied by  物理学院 张宇 


**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

2）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

3）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：Windows 10

Python编程环境：Spyder


## 1. 题目

### 22485: 升空的焰火，从侧面看

http://cs101.openjudge.cn/practice/22485/



思路：



代码

```python
# 
# -*- coding: utf-8 -*-
"""
张宇 2000011526
"""
n=int(input())
tree=[0]
for i in range(n):
    tree.append(list(map(int, input().split())))
stack=[1]
ans=[]
while stack:
    ans.append(str(stack[-1]))
    temp=[]
    for x in stack:
        if tree[x][0]!=-1:
            temp.append(tree[x][0])
        if tree[x][1]!=-1:
            temp.append(tree[x][1])
    stack=temp
print(" ".join(ans))
```



代码运行截图 
![alt text](烟花-1.png)




### 28203:【模板】单调栈

http://cs101.openjudge.cn/practice/28203/



思路：



代码

```python
# 
# -*- coding: utf-8 -*-
"""
张宇 2000011526
"""
n = int(input())
a = list(map(int, input().split()))
stack = []

for i in range(n):
    while stack and a[stack[-1]] < a[i]:
        a[stack.pop()] = i + 1
    stack.append(i)
while stack:
    a[stack[-1]] = 0
    stack.pop()   
print(*a)
```



代码运行截图
![alt text](单调栈-1.png)





### 09202: 舰队、海域出击！

http://cs101.openjudge.cn/practice/09202/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 04135: 月度开销

http://cs101.openjudge.cn/practice/04135/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 07735: 道路

http://cs101.openjudge.cn/practice/07735/



思路：



代码

```python
# 
# -*- coding: utf-8 -*-
"""
张宇 2000011526
"""
import heapq
k=int(input())
n=int(input())
r=int(input())
graph={i:[] for i in range(1, n+1)}
for _ in range(r):
    s,d,dl,dt=map(int, input().split())
    graph[s].append((dl,dt,d))
Q=[(0,0,1)]
F=[10000]*101
def dijkstra(g):
    while Q:
        l,t,d=heapq.heappop(Q)
        if d==n:
            return l
        if t>F[d]:
            continue
        F[d]=t
        for dl,dt,next_d in g[d]:
            if t+dt <= k:
                heapq.heappush(Q,(l+dl,t+dt,next_d))
    return -1
print(dijkstra(graph))
```



代码运行截图 
![alt text](道路-1.png)




### 01182: 食物链

http://cs101.openjudge.cn/practice/01182/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获

最近在忙毕业论文和答辩，有点忽视数算课，本次作业再次让我认识到数算想学好需要投入不小的精力。希望这几天为期末考试多做准备。




