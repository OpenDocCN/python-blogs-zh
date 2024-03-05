# 冒泡排序:快速教程和实施指南

> 原文：<https://www.pythoncentral.io/bubble-sort-implementation-guide/>

## 先决条件

要了解冒泡排序，您必须知道:

1.  Python 3
2.  Python 数据结构-列表

## 什么是冒泡排序？

在上一个教程中，我们看到了如何在未排序和排序的列表中搜索元素。我们发现对列表进行排序后，搜索效率会更高。那么我们如何对列表进行排序呢？在本教程和接下来的教程中，我们将研究一些常用的列表排序算法。每种算法都有其优点和缺点，我们将在后面讨论。

**注意:所有这些算法都侧重于按升序对列表进行排序(降序被认为是未排序的)。**

首先，我们来看看最基本最简单的算法之一——冒泡排序。它可能不是最高效的，但是非常容易实现。冒泡排序接受一个未排序的列表，并不断将每个元素与其右侧的邻居进行比较，以便对数据进行排序。较小的元素会向左移动。一轮结束后，最大的数字会回到正确的位置。换句话说，在这种情况下，最大数量的气泡位于顶部或右侧。然后，一次又一次地重复这个过程，直到所有的数据都被排序。让我们看一个例子来更好地理解这一点。

a = [6，8，1，3，0，5]

第一轮:

0 - 6 < 8(无互换)-【6，8，1，3，0，5】

1 - 8 > 1(互换)-【6，1，8，3，0，5】

2 - 8 > 3(互换)-【6，1，3，8，0，5】

3 - 8 > 0(互换)-【6，1，3，0，8，5】

4 - 8 > 5(互换)-【6，1，3，0，5，8】

**注意:** 8 在其正确的位置

第二轮:

0 - 6 > 1(互换)-【1，6，3，0，5，8】

1 - 6 > 3(互换)-【1，3，6，0，5，8】

2 - 6 > 0(互换)-【1，3，0，6，8】

3 - 6 < 8(无交换)- [1，3，0，6，8] -不需要

**注意:** 6 在其正确的位置

第三轮:

0 - 1 < 3(无互换)-【1，3，0，6，8】

1 - 3 > 0(互换)-【1，0，3，6，8】

2 - 3 < 6(无互换)-【1，0，3，6，8】

3 - 6 < 8(无交换)- [1，0，3，6，8] -不需要

**注意:** 3 在其正确的位置

第四轮:

0 - 1 > 0(互换)-【0，1，3，6，8】

1 - 1 < 3(无互换)-【0，1，3，6，8】

2 - 3 < 6(无交换)- [0，1，3，6，8] -不需要

3 - 6 < 8(无交换)- [0，1，3，6，8] -不需要

**注意:** 1 在其正确的位置

第五轮:

0 - 0 < 1(无互换)-【0，1，3，6，8】

1 - 1 < 3(无交换)- [0，1，3，6，8] -不需要

2 - 3 < 6(无交换)- [0，1，3，6，8] -不需要

3 - 6 < 8(无交换)- [0，1，3，6，8] -不需要

注意:0 位于正确的位置。即使 0 在第 4 轮中处于正确的位置，我们的算法也不理解这一点，直到该过程完成。

上面的未排序列表不是最坏的情况，最坏的情况是未排序列表是降序列表。对于这样一个包含了 *n* 元素的列表，我们需要执行(n-1)次交换来对其进行升序排序。你自己试试这个。观察如何在第一轮中对所有的 *n* 元素进行排序，而在第二轮中对*(n-1)*元素进行排序，以此类推。

尝试这个动画来获得算法的可视化。

## 如何实现冒泡排序？

在我们进入算法和代码之前，理解交换是如何工作的是很重要的。为了交换两个元素 a = 10 和 b = 5 的值，我们需要一个 *temp* 变量。该变量暂时存储 *a* 的值，该值后来被赋给*b****。***

a = 10

b = 5

温度= a #a = 10，温度= 10，b = 5

a = b #a = 5，温度= 10，b = 5

b =温度#a = 5，温度= 10，b = 10

打印(a)#打印 5 张

打印(b)#打印 10 张

### 算法

现在，让我们看看如何实现优化版本的冒泡排序:

1.  对于第一次迭代，比较所有元素(n)。对于后续运行，比较(n-1) (n-2)等。
2.  将每个元素与其右侧的邻居进行比较。
3.  将最小的元素交换到左边。
4.  继续重复步骤 1-3，直到覆盖整个列表。

### 代码

```py
def bubbleSort(alist):

   #Setting the range for comparison (first round: n, second round: n-1  and so on)
   for i in range(len(alist)-1,0,-1):

      #Comparing within set range
       for j in range(i):

           #Comparing element with its right side neighbor
           if alist[j] > alist[j+1]:

               #swapping
               temp = alist[j]
               alist[j] = alist[j+1]
               alist[j+1] = temp

   return alist

print(bubbleSort([5,1,2,3,9,8,0]))
```

这个算法是 0(n^2 的(n 的 2 次方)

## 结论

你可以进一步优化上面的代码，检查输入列表是否已经排序。这可以通过检查给定回合中发生的交换次数来完成。如果没有交换，则列表被排序。这种算法适用于小列表，但总的来说，它显然不是一个有效的算法。本教程到此为止。请务必尝试自己编写这段代码，并了解它的应用。快乐的蟒蛇！