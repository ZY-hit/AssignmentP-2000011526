# Assignment #5: "树"算：概念、表示、解析、遍历

Updated 2124 GMT+8 March 17, 2024

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

### 27638: 求二叉树的高度和叶子数目

http://cs101.openjudge.cn/practice/27638/



思路：



代码

```python
# 

```



代码运行截图 ==（至少包含有"Accepted"）==





### 24729: 括号嵌套树

http://cs101.openjudge.cn/practice/24729/



思路：



代码

```python
# 
class Tree:
      def __init__(self, val):
         self.val=val
         self.down=[]
         
def tree(s):
    L=[]
    node=None
    for i in s:
        if i.isalpha(): 
           node=Tree(i)
           if L: 
              L[-1].down.append(node)
        elif i=='(':
           if node:
              L.append(node) 
              node=None
        elif i==')': 
           if L:
              node=L.pop() 
    return node

def preorder(node):
    preo=[node.val]
    for i in node.down:
        preo.extend(preorder(i))
    return ''.join(preo)
def postorder(node):
    posto=[]
    for i in node.down:
       posto.extend(postorder(i))
    posto.append(node.val)
    return ''.join(posto)

s=input()
root=tree(s)
print(preorder(root)) 
print(postorder(root))
```



代码运行截图
![alt text](嵌套括号-1.png)





### 02775: 文件结构“图”

http://cs101.openjudge.cn/practice/02775/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 25140: 根据后序表达式建立队列表达式

http://cs101.openjudge.cn/practice/25140/



思路：先由后序表达式建立树，再对树按层次遍历建立队列表达式。



代码

```python
# 
class Tree:
      def __init__(self, val):
         self.val=val
         self.left=None
         self.right=None
         
def tree(A):
    stack=[]
    for i in A:
       node=Tree(i)
       if i.isupper():
          node.right=stack.pop()
          node.left=stack.pop()
       stack.append(node)
    return stack[-1]

def output(root):
    queue=[root]
    B=[]
    while queue:
       node=queue.pop(0)
       B.append(node.val)
       if node.left:
          queue.append(node.left)
       if node.right:
          queue.append(node.right)
    return B

n=int(input())
for i in range(n):
    A=input()
    print(''.join(output(tree(A))[::-1]))        
```
代码运行截图 
![alt text](后序队列-1.png)



### 24750: 根据二叉树中后序序列建树

http://cs101.openjudge.cn/practice/24750/



思路：递归，使用根节点在中序的位置作区分



代码

```python
# 
# -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
def tree(ino,posto):
    if not ino or not posto:
        return[]
    root_val=posto[-1]
    root_index=ino.index(root_val)
    
    inoleft=ino[:root_index]
    inoright=ino[root_index+1:]
    postoleft=posto[:len(inoleft)]
    postoright=posto[len(inoleft):-1]
    
    root=[root_val]
    root.extend(tree(inoleft,postoleft))
    root.extend(tree(inoright,postoright))
    return root

ino=input()
posto=input()
preo=tree(ino, posto)
print(''.join(preo))
```



代码运行截图 
![alt text](中后转前-1.png)




### 22158: 根据二叉树前中序序列建树

http://cs101.openjudge.cn/practice/22158/



思路：



代码

```python
# 
# -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
class Tree:
    def __init__(self,val):
        self.val=val
        self.left=None
        self.right=None
        
def tree(preo,ino):
    if not ino or not preo:
        return None
    root_val=preo[0]
    root_index=ino.index(root_val)
    
    inoleft=ino[:root_index]
    inoright=ino[root_index+1:]
    preoleft=preo[1:len(inoleft)+1]
    preoright=preo[len(inoleft)+1:]
    
    root=Tree(root_val)
    root.left=(tree(preoleft,inoleft))
    root.right=(tree(preoright,inoright))
    return root

def postoder(root):
    if root is None:
        return ''
    return postoder(root.left)+postoder(root.right)+root.val
while True:
    try:
       preo=input()
       ino=input()
       root=tree(preo, ino)
       print(postoder(root))
    except EOFError:
        break
```


代码运行截图 
![alt text](前中转后-1.png)




## 2. 学习总结和收获

本次课程的作业侧重对树的性质和存储功能的理解，有一定难度，但通过做题加深了对树的认知。
同时，较多使用函数、将复杂问题分步进行（例如先构建出树）的思想是我受益颇多。




