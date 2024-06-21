# Assignment #7: April 月考

Updated 1557 GMT+8 Apr 3, 2024

2024 spring, Complied by 张宇 物理学院


**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

2）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

3）如果不能在截止前提交作业，请写明原因。



**编程环境**


操作系统：Windows10

Python编程环境：Spyder(Anaconda)

C/C++编程环境：Mac terminal vi (version 9.0.1424), g++/gcc (Apple clang version 14.0.3, clang-1403.0.22.14.1)



## 1. 题目

### 27706: 逐词倒放

http://cs101.openjudge.cn/practice/27706/



思路：



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
l=list(map(str,input().split()))
o=[]
for i in range(len(l)):
    o.append(l[len(l)-i-1])
print(" ".join(o))
```



代码运行截图
![alt text](反序-1.png)





### 27951: 机器翻译

http://cs101.openjudge.cn/practice/27951/



思路：列表apppend，pop（0）



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
l,n=map(int,input().split())
I=list(map(int,input().split()))
c=[0]*l
k=0
for i in range(n):
    if I[i] not in c:
            k=k+1
            c.append(I[i])
            c.pop(0)
print(k)

```



代码运行截图 
![alt text](机器翻译-1.png)




### 27932: Less or Equal

http://cs101.openjudge.cn/practice/27932/



思路：排序，注意k=0的特殊情况。如果k不为0.则按第k个数和第k+1个数是否相等讨论。



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
n,k=map(int,input().split())
l=list(map(int,input().split()))
l.sort()

if k!=0:
    if k==n:
        print(l[k-1])
    else:
        if l[k-1]==l[k]:
           print(-1)
        else:
           print(l[k-1])
else:
    if l[0]>1:
        print(1)
    else:
        print(-1)

```



代码运行截图 
![alt text](less-1.png)




### 27948: FBI树

http://cs101.openjudge.cn/practice/27948/



思路：因为s必定是2的n次方，给递归建树提供了方便，然后后序遍历。



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
class Tree:
    def __init__(self):
         self.val=None
         self.left=None
         self.right=None

def tree(s):
    root=Tree()
    if "1" not in s:
        root.val="B"
    elif "0" not in s:
        root.val="I"
    else:
        root.val="F"
    a=len(s)//2
    if a>0:
        root.left=tree(s[:a])
        root.right=tree(s[a:])
    return root

def postorder(root):
    O=[]
    if root:
        O.extend(postorder(root.left))
        O.extend(postorder(root.right))
        O.append(root.val)
    return ''.join(O)

n=int(input())
s=input()
print(postorder(tree(s)))

```



代码运行截图 
![alt text](FBI-1.png)




### 27925: 小组队列

http://cs101.openjudge.cn/practice/27925/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 27928: 遍历树

http://cs101.openjudge.cn/practice/27928/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获
复习了栈队列和树的知识，预计2h能独立完成4道题目。图的章节继续努力。




