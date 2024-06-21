# Assignment #6: "树"算：Huffman,BinHeap,BST,AVL,DisjointSet

Updated 2214 GMT+8 March 24, 2024

2024 spring, Complied by 张宇 物理学院



**说明：**

1）这次作业内容不简单，耗时长的话直接参考题解。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**


操作系统：Windows 10

Python编程环境：Spyder(Anaconda)
C/C++编程环境：Mac terminal vi (version 9.0.1424), g++/gcc (Apple clang version 14.0.3, clang-1403.0.22.14.1)



## 1. 题目

### 22275: 二叉搜索树的遍历

http://cs101.openjudge.cn/practice/22275/



思路：递归



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
class Tree:
    def __init__(self,val):
        self.val=val
        self.left=None
        self.right=None
        
        
def tree(preo):
    if len(preo)==0:
        return None
    root=Tree(preo[0])
    l=len(preo)
    for i in range(1,len(preo)):
        if preo[i]>preo[0]:
            l=i
            break
    root.left=tree(preo[1:l])
    root.right=tree(preo[l:])
    return root

def posto(root):
    if root is None:
        return []
    out=[]
    out.extend(posto(root.left))
    out.extend(posto(root.right))
    out.append(root.val)
    return out

n=int(input())
preo=list(map(int,input().split()))
O=posto(tree(preo))
for i in range(len(O)):
    O[i]=str(O[i])
print(" ".join(O))

```



代码运行截图 
![alt text](搜索树遍历-1.png)





### 05455: 二叉搜索树的层次遍历

http://cs101.openjudge.cn/practice/05455/



思路：



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
class Tree:
    def __init__(self, val):
        self.val=val
        self.left=None
        self.right=None


def insert(node, val):
    if node is None:
       return Tree(val)
    if val<node.val:
       node.left=insert(node.left,val)
    elif val>node.val:
       node.right=insert(node.right,val)
    return node

def order(root):
    queue=[root]
    traversal=[]
    while queue:
        node=queue.pop(0)
        traversal.append(node.val)
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
    return traversal

l=list(map(int,input().split()))
l=list(dict.fromkeys(l)) 
root=None
for i in l:
    root=insert(root,i)
O=order(root)
for i in range(len(O)):
    O[i]=str(O[i])
print(" ".join(O))    

```



代码运行截图 
![alt text](层次遍历-1.png)





### 04078: 实现堆结构

http://cs101.openjudge.cn/practice/04078/

练习自己写个BinHeap。当然机考时候，如果遇到这样题目，直接import heapq。手搓栈、队列、堆、AVL等，考试前需要搓个遍。


思路：参考了教材。堆是优先级队列，利用位置为n的子节点的父节点的位置是n//2建立向堆插入元素和从堆中删除元素的方式。



代码

```python
# 
# -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
class BinHeap:
    def __init__(self):
        self.heap=[0]
        self.size=0
    
    def Up(self,i):
        while i//2>0:
            if self.heap[i]<self.heap[i//2]:
                tmp=self.heap[i//2]
                self.heap[i//2]=self.heap[i]
                self.heap[i]=tmp
            i=i//2
    def insert(self, k): 
        self.heap.append(k) 
        self.size=self.size+1 
        self.Up(self.size)   
        
    def Down(self,i):
        while (i*2)<=self.size:
            mc=self.min(i)
            if self.heap[i]>self.heap[mc]:
               tmp=self.heap[i]
               self.heap[i]=self.heap[mc]
               self.heap[mc]=tmp
            i=mc

    def min(self,i):
        if i*2+1>self.size:
            return i*2
        else:
            if self.heap[i*2]<self.heap[i*2+1]:
                return i *2
            else:
                return i*2+1

    def delmin(self): 
        retval=self.heap[1] 
        self.heap[1]=self.heap[self.size] 
        self.size=self.size-1 
        self.heap.pop() 
        self.Down(1) 
        return retval 


n=int(input())
B=BinHeap()
for i in range(n):
    a=list(map(int,input().split()))
    if a[0]==1:
        B.insert(a[1])
    else:
        print(B.delmin())

```



代码运行截图 
![alt text](二叉堆-1.png)




### 22161: 哈夫曼编码树

http://cs101.openjudge.cn/practice/22161/



思路：参考了题解。



代码

```python
# # -*- coding: utf-8 -*-
"""
@author: 张宇2000011526
"""
import heapq

class Node:
    def __init__(self, weight, char=None):
        self.weight = weight
        self.char = char
        self.left = None
        self.right = None
    def __lt__(self, other):
        if self.weight == other.weight:
            return self.char < other.char
        return self.weight < other.weight

def build_huffman_tree(characters):
    heap = []
    for char, weight in characters.items():
        heapq.heappush(heap, Node(weight, char))
        
    while len(heap) > 1:
        left = heapq.heappop(heap)
        right = heapq.heappop(heap)

        merged = Node(left.weight + right.weight, min(left.char, right.char))
        merged.left = left
        merged.right = right
        heapq.heappush(heap, merged)
    return heap[0]

def encode_huffman_tree(root):
    codes = {}
    def traverse(node, code):
        if node.left is None and node.right is None:
            codes[node.char] = code
        else:
            traverse(node.left, code + '0')
            traverse(node.right, code + '1')
    traverse(root, '')
    return codes

def huffman_encoding(codes, string):
    encoded = ''
    for char in string:
        encoded += codes[char]
    return encoded

def huffman_decoding(root, encoded_string):
    decoded = ''
    node = root
    for bit in encoded_string:
        if bit == '0':
           node = node.left
        else:
           node = node.right
        if node.left is None and node.right is None:
           decoded += node.char
           node = root
    return decoded

n = int(input())
characters = {}
for _ in range(n):
   char, weight = input().split()
   characters[char] = int(weight)

huffman_tree = build_huffman_tree(characters)

codes = encode_huffman_tree(huffman_tree)
strings = []
while True:
   try:
     line = input()
     strings.append(line)
   except EOFError:
     break
results = []

for string in strings:
   if string[0] in ('0','1'):
       results.append(huffman_decoding(huffman_tree, string))
   else:
       results.append(huffman_encoding(codes, string))
for result in results:
    print(result)

```



代码运行截图 
![alt text](哈夫曼-1.png)





### 晴问9.5: 平衡二叉树的建立

https://sunnywhy.com/sfbj/9/5/359



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 02524: 宗教信仰

http://cs101.openjudge.cn/practice/02524/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获

本次作业难度很高，较多参考了课件和题解。尤其是哈夫曼编码树，如果要求先创建堆这一结构，将会更繁琐。但本次作业加深了我对较复杂的数据结构的认识。希望自己能继续多多熟悉树，慢慢不再依赖教材。




