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
