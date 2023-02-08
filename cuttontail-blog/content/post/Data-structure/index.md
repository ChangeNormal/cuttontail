---
title: "数据结构算法学习-算法图解-第一日"
date: 2023-02-07T22:20:57+08:00
description: "经过考研，数据结构这门课算是完整的了解，但是要说掌握程度肯定还是不太行，只停留在基础阶段（算法思想的理解），并未经常动手实践代码，而这篇文章旨在于帮助我记录平时学习数据结构算法的心得。"
categories: ["数据结构","算法图解"]
tags: [
    "DataStructure","算法学习","二分查找","大O表示法"
]
image: "2.png"
---

数据结构是一门基础学科，你只有将数据结构知识掌握牢固才能够在以后的工作中得心应手，而且现在各大厂第一道就是笔试卡了不少初级程序员，所以作为计算机的从业者不得不重视数据结构算法的学习！而我则是打算先将数据结构书面知识思想掌握再去力扣进行系统刷题，是因为我觉得这样的学习更加科学，更加有效率也更加扎实。

<!--more-->

# 初识算法-二分查找及大O表示法

开始学习前你最好需要有：数据结构知识，基础编程语言经验（Python即可）

## 一、二分查找

二分查找？没错，就是你像的那样！其实还真的就是从中间的数开始找起，如果没有找到对应的数就将`low`和`high`的值进行修改，当你要寻找的值小于`mid`处值时我们令`high = mid - 1`,而当(这里你要找的值设为`item`)`item > mid`时我们令`low = mid + 1`(此处应当注意是>,<号而不带等号,可以先自行思考为何，后面我会作出解释)。而当`low <= high`时`while`循环将会继续进行，直至`low > high`跳出循环`return mid或者None`。

我可以形象的用一个例子来告诉你为什么有的时候我们使用二分查找会更合适。

```python
def binary_search(list, item):
    low = 0
    high = len(list)-1
    while low <= high:
        mid = (low + high) // 2 # 这个地方注意Python3.x与Python2.x有差异
        guess = list[mid]
        if guess == item:
            return mid
        if guess < item:
            low = mid + 1
        else:
            high = mid -1
    return None

my_list = [1, 3, 5, 7, 9]

print(binary_search(my_list, 3))
print(binary_search(my_list, -1))
```

