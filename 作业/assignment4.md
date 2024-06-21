# Assignment #4: 排序、栈、队列和树

Updated 0005 GMT+8 March 11, 2024

2024 spring, Complied by 张宇 物理学院



**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:

Learn about Time complexities, learn the basics of individual Data Structures, learn the basics of Algorithms, and practice Problems.

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：Windows 10

Python编程环境：Spyder(Anaconda)

## 1. 题目

### 05902: 双端队列

http://cs101.openjudge.cn/practice/05902/



思路：利用list创建双端队列，双端队列的进出用list的append、insert、pop定义，但我自己写的不知为何总是WA，遂参考老师答案。



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526（参考老师题解）
"""
from collections import deque
for _ in range(int(input())):
    n=int(input())
    q=deque([])
    for i in range(n):
        a,b=map(int,input().split())
        if a==1:
            q.append(b)
        else:
            if b==0:
              q.popleft()
            else:
              q.pop()
    if q:
       print(*q)
    else:
       print('NULL')

# -*- coding: utf-8 -*-
"""
@author: 张宇2000011526（自己写的）
"""
class Deque:
    def __init__(self):
        self.items=[]
    def isempty(self):
        return self.items==[]
    def addfront(self,item):
        self.items.append(item)
    def addrear(self,item):
        self.items.insert(0,item)
    def removefront(self):
        return self.items.pop()
    def removerear(self):
        return self.items.pop(0)
    def size(self):
        return len(self.items)       
n=int(input())
A=[]
for i in range(n):
    m=int(input())
    d=Deque()
    for j in range(m):
        a,b=map(int,input().split())
        if a==1:
           d.addrear(b)
        else:
            if b==0:
                d.removefront()
            else:
                d.removerear()
    if d.isempty():
        A.append("NULL")
    else:
        c=[]
        for i in range(d.size()):
            c.append(str(d.removefront()))
            A.append(' '.join(c))
for i in range(len(A)):
    print(A[i])          
            
```



代码运行截图
![alt text](队列-1.png)




### 02694: 波兰表达式

http://cs101.openjudge.cn/practice/02694/



思路：使用栈存储



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""

l=list(input().split())
a=[]
n=len(l)
for i in range(n):
    if l[i]!='*' and l[i]!='+' and l[i]!='-' and l[i]!='/':
        l[i]=float(l[i])

for i in range(n):
    if isinstance(l[n-1-i],float):
        a.append(l[n-1-i])
    else:
        c=len(a)
        if l[n-1-i]=='+':
            b=a[c-2]+a[c-1]
        elif l[n-1-i]=='-':
            b=a[c-1]-a[c-2]
        elif l[n-1-i]=='/':
            b=a[c-1]/a[c-2]
        else:
            b=a[c-2]*a[c-1]
        a.pop()
        a.pop()
        a.append(b)
if len(a)==1:
    print('%.6f' % a[0])
else:
    d=a[0]+a[1]
    print('%.6f' % d)

```



代码运行截图
![alt text](波兰-1.png)





### 24591: 中序表达式转后序表达式

http://cs101.openjudge.cn/practice/24591/



思路：使用两个栈，一个存储运算符，一个存储数字。刚开始做本题时因为忽略了将初始字符串准确分割成数字和符号浪费了时间。



代码

```python
# def midtosuf(s):
    l,a=[],[]
    priority = {"/":1,"*":1,"+":2,"-":2}
    for item in s:
        if item=="(":
            l.append(item)
        elif item==")":
            while l[-1]!="(":
                a.append(l.pop())
            l.pop()
        elif item in "/*+-":
            while len(l)>=1 and l[-1]!="(" and priority[l[-1]]<=priority[item]:
                a.append(l.pop())
            l.append(item)
        else:
            a.append(item)
    while l!=[]:
        a.append(l.pop())
    return " ".join(a)
n=int(input())
for i in range(n):
    c=input()
    s=[""]
    for j in range(len(c)):
        if c[j] in "()/*+-":
           s.append(c[j])
        else:          
           s[-1]=s[-1]+c[j]
    a=[]
    if c[0]=="(":
       s.pop(0)  
    for i in range(len(s)):
        if len(s[i])==1:
            a.append(s[i])  
             
        else:
           if s[i][0] in "/*+-(":
              a.append(s[i][0])
              a.append(s[i][1:])
           else:
              a.append(s[i])  
    print(midtosuf(a))        

```



代码运行截图 
![alt text](表达式-1.png)




### 22068: 合法出栈序列

http://cs101.openjudge.cn/practice/22068/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 06646: 二叉树的深度

http://cs101.openjudge.cn/practice/06646/



思路：自己做的时候比较懵圈，自习、、仔细阅读了课件，递归。



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
class TreeNode:
    def __init__(self):
        self.left = None
        self.right = None

def tree_depth(node):
    if node is None:
        return 0
    left_depth = tree_depth(node.left)
    right_depth = tree_depth(node.right)
    return max(left_depth, right_depth) + 1

n = int(input())  
nodes = [TreeNode() for _ in range(n)]

for i in range(n):
    left_index, right_index = map(int, input().split())
    if left_index != -1:
        nodes[i].left = nodes[left_index-1]
    if right_index != -1:
        nodes[i].right = nodes[right_index-1]

root = nodes[0]
depth = tree_depth(root)
print(depth)


```



代码运行截图 
![alt text](深度-1.png)





### 02299: Ultra-QuickSort

http://cs101.openjudge.cn/practice/02299/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获

本次作业题目较难，代码较长，花费时间较长，尤其树是计算概论理所没有的内容，理解起来花费时间。希望自己能尽快跟上。




