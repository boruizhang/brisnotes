---
layout: post
title:  "Syntactic tips for constructing trees"
date:   2020-07-17 17:58:08 -0500
categories: jekyll update
---
The topic of the day: understanding the python syntax of binary tree datatype and recursives in the code.

Take a look at the code below. It is a function that construct a tree that as the result of two trees merge together. The goal here is not to code-solving the problem (for which leetcode has better answers), but to understand the python statements used in the answer code. Try to answer the following questions while reading the code. If you can answer all of them, then say BYE to this post and go enjoy something else today.

Q1: what's the relation between `TreeNode` and `self`, `val`, `left`, and `right`?

Q2: how to interpret `mergeTrees(self, t1: TreeNode, t2: TreeNode) -> TreeNode:`?

Q3: why should it be `ans = TreeNode(t1.val + t2.val)` but not `ans = t1.val + t2.val`?

Q4: where is the recursive part?


```python
# merge two trees
class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

class Solution:
    def mergeTrees(self, t1: TreeNode, t2: TreeNode) -> TreeNode:
      if t1 and t2:
        ans = TreeNode(t1.val + t2.val)
        ans.left = self.mergeTrees(t1.left, t2.left)
        ans.right = self.mergeTrees(t1.right, t2.right)
        return ans
      else:
        return t1 or t2
```


Here are the answers:

**Q1:** what's the relation between `TreeNode` and `self`, `val`, `left`, and `right`?

A1: `TreeNode` is the datatype we created, and `self` is one individual in this type. `val`, `left`, and `right`are the attributes (properties) that this type of data has.

**Q2:** how to interpret `def mergeTrees(self, t1: TreeNode, t2: TreeNode) -> TreeNode:`?

A2: Defining a function that called `mergeTrees`, which should be able to merge to existing trees (t1 and t2) to create a new tree. t1 and t2 have the TreeNode datatype (therefore, themselves have `val`, `left`, and `right` respectively). `-> TreeNode:` means the resulting merged tree should also follow the same datatype as t1 and t2.

**Q3:** why `ans = TreeNode(t1.val + t2.val)` but not `ans = t1.val + t2.val`?

A3: If it is `ans = t1.val + t2.val` then *ans* is a **number** but not a TreeNode, because it is the summed up result of the values of TreeNode t1 and t2. This violates the datatype we want to give to *ans* **TreeNode**.

The tricky part to understand this here is that value of each node seems to be the only property a node has. But no. Being a cute TreeNode also needs values of its left and right node, even those value can be null sometimes.  

**Q4:** where is the recursive part?

A4: `ans.left = self.mergeTrees(t1.left, t2.left)` namely the most beautiful part of the code - a short statement does large work. Be careful when write recursive to construct something, don't forget to add the **self** before the name of the function. Because the *mergeTree* here is designed as a method function under a [python class]. In contrast to a function written outside of a class, it will not need a self.

**try/except** Only put the necessary lines in between this function. Too many lines might lead to some lines never get executed.


```python

# try/except
a = "bri"
try:
  a_number = int(a)
except:
  a_number = -1

```

My learning source is from [leetcode].

[leetcode]: https://leetcode.com/
[python class]: http://127.0.0.1:4000/brisnotes/jekyll/update/2020/01/13/what-is-a-python-class.html
