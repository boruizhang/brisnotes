---
layout: post
title:  "Python programming note"
date:   2020-01-13 23:51:08 -0500
categories: jekyll update
---

*This is a collection of syntactic movements, and still on-going: (last updated Feb 13th, 2020)*

The topic of the day: `python class`, is a tool to create your own data type. This is not the data types such as string, number, list, etc., which we already know and usually do not need to create a datatype for those. But the "new" datatypes we create using `class` are based on these basic types.

Like the example below, we first give a name of this data type we are going to create. `TreeNode` is the name I give.\
`def __init__` defines a function which initializes this data type so that later the real data of this type can be stored in the memory.\
`self` must be the parameter for the initializing function. It means this datatype itself.\
`x` is a value of this datatype. You can do `def __init__(self, x, y, z, c, d, e):` as you need theoretically. We only need one value for constructing one tree node, as the code showing the value of x `def __init__(self, x)`.\
`self` is followed by its attributes `.val`, `.left`, and `.right`. The entire `self.val = x` means the value of the attribute `val` of this datatype is `x`. Later when we import data entries, the values will be passed to `x`.\

Now, the datatype I created by using Python `class` is completed.

```python
class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

```
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
