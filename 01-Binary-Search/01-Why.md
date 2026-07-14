# Why Binary Search?

## The Question

Why do we learn Binary Search instead of other searching algorithms?

---

## Linear Search is Too Slow, But That Is Not Enough

The first problem is obvious:

```text
Linear Search
↓
O(n)
↓
Too Slow
```

However, this **does not naturally lead to Binary Search**.

There are many other ways to speed up searching, such as Hash Tables, Jump Search, Exponential Search, and Interpolation Search.

So the real question is:

> Why Binary Search?

---

## The Turning Point Is Not "Fast"

The key observation is not that searching is slow.

The key observation is that **the data is ordered.**

Once the data is ordered, every comparison gives information about an entire region rather than a single element.

Example:

```text
1 3 5 7 9 11 13
```

If

```text
target > 7
```

then

```text
1 3 5 7
```

are **all impossible**.

One comparison eliminates an entire search space.

This is something Linear Search can never do.

---

## Binary Search Is About Elimination

Binary Search is not simply "checking the middle."

Its real purpose is:

> Continuously eliminate impossible candidates.

The search space becomes smaller after every comparison.

---

## Why Split in Half?

Many elimination strategies exist.

For example:

- Jump Search
- Exponential Search
- Interpolation Search

Binary Search is not the fastest under every condition.

Instead, it is the **simplest strategy that guarantees O(log n)** under LeetCode's assumptions:

- ordered data
- random access
- known boundaries

Splitting the search space in half minimizes the worst-case remaining search space after every decision.

---


## Related Search Algorithms

Binary Search is only one member of the searching algorithm family.
Different assumptions lead to different optimal solutions.

| Algorithm | Core Idea | Typical Use Case | Why Not Used in Most LeetCode Problems |
|-----------|-----------|------------------|----------------------------------------|
| Linear Search | Check every element | Unordered data | Too slow for large datasets |
| Binary Search | Eliminate half of the search space each step | Ordered array with random access | LeetCode's default assumption |
| Jump Search | Jump by fixed blocks, then perform linear search | Sequential storage (historically useful on storage devices with expensive random access) | Inferior to Binary Search on modern memory |
| Exponential Search | First find a valid search range, then apply Binary Search | Unknown or unbounded array size | LeetCode arrays always have known boundaries |
| Interpolation Search | Estimate the target's position based on value distribution | Uniformly distributed ordered data | Performance degrades when data distribution is uneven |
| Hash Table | Compute the location directly | Exact lookup | Requires extra memory and preprocessing |

## Takeaway

Binary Search is not born because searching is slow.

It exists because **order makes elimination possible**, and splitting the remaining search space in half makes that elimination optimal.


# 为什么是二分查找（Why Binary Search?）

## 问题

为什么我们学习的是 **Binary Search（二分查找）**，而不是其他搜索算法？

---

## 遍历太慢，但这还不足以推出二分查找

最容易想到的问题是：

```text
线性遍历
    ↓
O(n)
    ↓
太慢
```

然而，仅仅因为遍历太慢，并不能自然推出二分查找。

为了提高查找效率，还有很多其他方法，例如：

- Hash Table（哈希表）
- Jump Search（跳跃查找）
- Exponential Search（指数查找）
- Interpolation Search（插值查找）

所以真正的问题应该是：

> **为什么偏偏是 Binary Search？**

---

## 真正的关键不是「快」，而是「有序」

真正重要的观察，并不是遍历太慢。

而是：

> **数据具有有序性（Order）。**

一旦数据有序，每一次比较获得的信息，就不再只针对一个元素，而是针对**整个区域（Region）**。

例如：

```text
1 3 5 7 9 11 13
```

如果：

```text
target > 7
```

那么：

```text
1 3 5 7
```

就全部可以排除。

因为数组已经有序，它们都不可能是答案。

一次比较，就能排除整个搜索空间的一半。

而线性遍历永远做不到这一点，它每次只能确认：

> **当前这个元素不是答案。**

---

## 二分查找真正做的事情

很多人认为二分查找就是：

> 每次检查中间那个元素。

其实这只是它的实现方式。

二分查找真正做的事情是：

> **不断排除不可能的搜索空间（Search Space）。**

每进行一次比较，剩余需要搜索的区域都会缩小。

因此，Binary Search 的本质并不是「查找」，而是：

> **不断缩小搜索空间。**

---

## 为什么一定要「对半分」？

既然目标是不断排除搜索空间，

为什么不是：

- 每次排除三分之一？
- 每次排除四分之一？
- 或者采用其他搜索策略？

事实上，这些方法都存在。

例如：

- Jump Search（跳跃查找）
- Exponential Search（指数查找）
- Interpolation Search（插值查找）

因此，

**Binary Search 并不是任何情况下最快的搜索算法。**

它之所以成为最经典的方法，是因为：

在 LeetCode 的默认假设下：

- 数据有序（Ordered）
- 可以随机访问（Random Access）
- 已知边界（Known Boundaries）

**每次将搜索空间平分，可以保证最坏情况下剩余的搜索空间最小。**

因此，它能够稳定达到：

```text
O(log n)
```

---

## 相关搜索算法

Binary Search 只是搜索算法家族中的一种。

不同的数据特点和应用场景，会对应不同的最佳搜索策略。

| 算法 | 核心思想 | 典型应用场景 | 为什么 LeetCode 很少使用 |
|------|----------|--------------|--------------------------|
| Linear Search（线性查找） | 逐个检查每个元素 | 无序数据 | 时间复杂度 O(n)，效率较低 |
| Binary Search（二分查找） | 每次排除一半搜索空间 | 有序数组、支持随机访问 | LeetCode 默认假设 |
| Jump Search（跳跃查找） | 每次跳过固定长度，再在线性扫描 | 顺序访问成本低、随机访问成本高的存储 | 现代内存中 Binary Search 更优 |
| Exponential Search（指数查找） | 先确定搜索范围，再进行二分查找 | 数组长度未知、无限数据流 | LeetCode 的数组长度始终已知 |
| Interpolation Search（插值查找） | 根据数据分布估计目标位置 | 数据均匀分布 | 数据分布不均时性能可能退化 |
| Hash Table（哈希表） | 直接计算目标位置 | 精确查找、Key-Value 查询 | 需要额外空间，不适用于区间问题 |

---

## 实际计算机中的应用

LeetCode 更喜欢考察 Binary Search，

并不意味着现实世界只使用 Binary Search。

事实上，不同的问题会采用不同的数据结构和搜索策略。

例如：

- **Hash Table**：用于字典、缓存、数据库 Key 查询等精确查找。
- **B-Tree / B+ Tree**：数据库索引的核心数据结构。
- **Git Bisect**：利用二分思想快速定位引入 Bug 的 Commit。
- **Binary Search on Answer**：大量工程优化问题都会使用，例如寻找最优参数、资源配置、服务器容量等。

因此，

现实工程中真正重要的，并不是会写 Binary Search。

而是能够识别：

> **什么时候一个问题允许你不断排除大量不可能的答案。**

---

## 总结

Binary Search 的出现，并不是因为查找太慢。

真正的原因是：

> **有序性，让我们能够排除整片不可能的搜索空间；**

而：

> **对半划分，则是在当前假设下，使这种排除达到最优。**
