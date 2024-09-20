# Algorithms

Algorithms are defined as a series of instructions, specific enough that a computer can follow them, with some end condition at which point the algorithm is complete.

For A Level and GCSE, students need to be able to articulate how various algorithms operate (not necessarily be able to code them though).

The algorithms you need can be divided into the following categories:

* Searching
* Sorting
* Routing
* Traversal

The traversal algorithms for Trees and Graphs are demonstrated on the [Data Structures](data-structures.md#binary-tree) page. This page will restrict itself to the other families of algorithm. I will not describe the full operation of those algorithms (this can be found elsewhere) but I will provide code implementations that can be examined.

## Big-O Notation

Algorithms tend to be selected based on their performance characteristics, this can be measured in a number of ways

* Memory Consumption
* Processor Usage
* Implementation Complexity

One comparison that you need to be familiar with is the Big-O Notation, which attempts to characterise how an algorithms computational requirements increase with respect to the size of the data set going in. For example, does a list that is twice the size, take twice as long to sort? Does a graph that is double the size, take exponentially longer to route across?

The way this is measured for an algorithm is by identifying the key operations in an algorithm, and determining how often those operations are executed for a given input data size _n_.

Determining the Big-O Notation comes down to establishing a formula for the number of steps an algorithm requires, with _n_ as the term for size of input list. For example, imagine a student doing maths questions. They are given 10 simple arithmetic questions and they complete them in one minute, so they are taking 6 seconds per question. It takes 1 minute for them to get out their books to work, so the total calculation for the time taken is

$$
Time (seconds) = 6 * n + 60
$$

If they are given 20 questions, it will take them

$$
6 * 20 + 60 = 180 seconds.
$$

If they are given 1000 questions it will take them

$$
6 * 1000 + 60 = 6060 seconds
$$

The time taken is increasing in a linear fashion, and the fixed cost of getting out the books eventually becomes insignificant when compared to the time to answer the questions.

So the Big-O Notation for a student doing maths homework is $$0(n)$$.

This kind of simplification is something that may seem imprecise, but this is not about finding an exact formula for time taken, just indicating how the time taken to execute an algorithm grows with respect to input size. There are a series of terms you need to be familiar with, they are listed here in increasing complexity.

| Big O Notation | Description                                                      | Judgment |
| -------------- | ---------------------------------------------------------------- | -------- |
| $$O(1)$$       | Constant - input size does not affect time                       | Best     |
| $$O(log n)$$   | Logarithmic, algorithms that halve the work with each iteration, | Good     |
| $$O(n)$$       | Linear                                                           | Fair     |
| $$O(n^2)$$     | Polynomial - Work required is a power of the input list          | Poor     |
| $$O(2^n)$$     | Exponential - work doubles with each additional data item        | Bad      |
| $$O(n!)$$      | Factorial - Even small inputs cause lots of work                 | Very bad |

For each algorithm below, you will need to be familiar with it's Big-O Notation. It isn't as simple as knowing a single notation though, algorithms tend to have a worst case, best case and average case which can vary.

## Sorting

### Bubble Sort

Good for short lists, performs badly on large lists. Very simple to code.

{% embed url="https://repl.it/@MarlingSharp/bubble-sort-ts#index.ts" %}

#### Big O Notation

Best case is the list is already sorted (yes...seems odd) in which case every item is compared once and then it's done. Far more often, we have nested loops where every item is compared to nearly every other item. Removing the constants from this leaves us with polynomial complexity.

| Worst Case | Average Case | Best Case |
| ---------- | ------------ | --------- |
| $$O(n^2)$$ | $$O(n^2)$$   | $$O(n)$$  |

### Insertion Sort

Similar simplicity as the bubble sort.

{% embed url="https://repl.it/@MarlingSharp/insertion-sort-ts#index.ts" %}

#### Big O Notation

Basically the same as bubble sort

| Worst Case | Average Case | Best Case |
| ---------- | ------------ | --------- |
| $$O(n^2)$$ | $$O(n^2)$$   | $$O(n)$$  |

### Merge Sort

One of the many 'divide and conquer' algorithms.

{% embed url="https://repl.it/@MarlingSharp/merge-sort-ts#index.ts" %}

#### Big O Notation

We recursively divide the list into 2 until there is one item in each list, this should lead to log(n) layers, which then need reconstructing. Each reconstruction requires _n_ operations.

| Worst Case         | Average Case    | Best Case       |
| ------------------ | --------------- | --------------- |
| $$O(n * log (n))$$ | $$O(n*log(n))$$ | $$O(n*log(n))$$ |

### Quick Sort

Sorts a list in place by successively partitioning the data around a pivot.

{% embed url="https://repl.it/@MarlingSharp/quick-sort-ts#index.ts" %}

#### Big O Notation

* For a list of length n, if the split point always occurs in the middle of the list, there will be log n divisions
* In order to find the split point, each of the n items needs to be checked against the pivot value
* Therefore, in the best case, the time complexity is n log n
* An additional advantage over the merge sort is that it needs no additional memory

| Worst Case         | Average Case    | Best Case       |
| ------------------ | --------------- | --------------- |
| $$O(n * log (n))$$ | $$O(n*log(n))$$ | $$O(n*log(n))$$ |

## Searching

### Linear Search

By far the simplest search algorithm, just look at every single data item in order until you find a match. Works on unsorted lists. Performance is bad for large lists.

{% embed url="https://repl.it/@MarlingSharp/linear-search-ts#index.ts" %}

#### Big O Notation

Very simple, the best case is the first item is the one we are looking for, in which case the Big O is O(1). The worst case is that it is at the end which is O(n). The average case would be half that, but since we disregard the constant 1/2 the Big O is O(n).

| Worst Case | Average Case | Best Case |
| ---------- | ------------ | --------- |
| $$O(n)$$   | $$O(n)$$     | $$O(1)$$  |

### Binary Search

Much quicker than linear search, but requires the data to be sorted first (which incurs its own performance cost).

{% embed url="https://repl.it/@MarlingSharp/binary-search-ts#index.ts" %}

#### Big O Notation

Since the list is divided in two each time, the work is being halved. Best case is the item happens to the be in the middle.

Remember that in reality we may have to factor in the cost of sorting the list in the first place. But if you are asked for the Big O of the binary search alone, then these are the answers:

| Worst Case   | Average Case | Best Case |
| ------------ | ------------ | --------- |
| $$O(log n)$$ | $$O(log n)$$ | $$O(1)$$  |

## Routing

### Dijkstra's Shortest Path Algorithm

There is one algorithm that you must be familiar with here, it is Dijkstra's routing algorithm, there is also an enhancement of this you need to be able to briefly describe called A\*.

{% embed url="https://repl.it/@MarlingSharp/dijkstras-routing-ts#Graph.ts" %}

#### Big O Notation & Dijkstra

This is actually a fairly complex question, the answer comes down to how it is implemented. Dijkstra's algorithm is effectively a combination of smaller algorithms (such as traversals). For this reason the A Level does not require you to consider the Big O notation for Dijkstra's Routing Algorithm.

More important would be describing how the A\* enhances Dijkstra through the use of a heuristic.

### A \* Shortest Path Algorithm

This is essentially the same as Dijkstra's algorithm, but where the priority queue in Dijkstra only considers the cost of the path so far, A \* includes the cost of a heuristic 'guess' of the cost from the given point to the destination.

One example of how to implement this heuristic might be to consider the straight line distance between each node and the destination. The real cost must be more than this, but if we use straight line distance and factor that into our priority queue, it will cause the A \* algorithm to head towards the goal quicker than Dijkstra. Dijkstra will always just take the next easiest path no matter what direction it is heading in.
