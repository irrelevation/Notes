# Algorithms & Data Structures

## Glossary

<sub>(a)</sub> - amortised time (aka "on average" example: resizing dynamic arrays)</br>
<sub>(e)</sub> - expected time (aka "there is some random part here: usually the hashing part of a hashtable")</br>
SSSP - Single Source Shortest Path, i.e. the shortest paths from a single vertex to all other verteces in the graph</br>
DAG - Directed Acyclic Graph, i.e. A graph without cycles and with edges that have a direction.

## Sort

| Algorithm      | Time O(·)                | In-place? | Stable? | Comments                                    |
| -------------- | ------------------------ | :-------: | :-----: | ------------------------------------------- |
| Insertion Sort | n<sup>2</sup>            |     ✔     |    ✔    | O(nk) for k-proximate                       |
| Selection Sort | n<sup>2</sup>            |     ✔     |   ❌    | O(n) swaps - choose if writes are expensive |
| Merge Sort     | n log n                  |    ❌     |    ✔    | stable, optimal comparison                  |
| AVL Sort       | n log n                  |    ❌     |    ✔    | good if also need dynamic                   |
| Heap Sort      | n log n                  |     ✔     |   ❌    | low space, optimal comparison               |
| Counting Sort  | n + u                    |    ❌     |    ✔    | O(n) when u = O(n)                          |
| Radix Sort     | n + n log <sub>n</sub> u |    ❌     |    ✔    | O(n) when u = O(nc)                         |

- Bubble Sort
- Quick Sort

### Data Structure Sorts

see [Binary Heaps Lecture](https://www.youtube.com/watch?v=Xnpo1atN-Iw)

- Array Sort (is selection sort)
- Sorted Array Sort (is insertion sort)
- Priority Queue Sort

## Search

### Rabin-Karp

# Datastructures

implicit (no pointers, just an array) vs explicit

## Interfaces

### Sequence

Sequence data structures support **extrinsic** operations that maintain, query, and modify an externally imposed order on items.

| Data Structure | `build(X)` | `get/set_at(i)` | `insert/delete_first(x)` | `insert/delete_last(x)` | `insert/delete_at(i,x)` |
| -------------- | :--------: | :-------------: | :----------------------: | :---------------------: | :---------------------: |
| Array          |     n      |        1        |            n             |            n            |            n            |
| Linked List    |     n      |        n        |            1             |            n            |            n            |
| Dynamic Array  |     n      |        1        |            n             |     1<sub>(a)</sub>     |            n            |
| Sequence AVL   |     n      |      log n      |          log n           |          log n          |          log n          |

### Set

Set data structures support **intrinsic** operations that maintain, query, and modify a set of items
based on what the items are, i.e., based on the **unique key** associated with each item.

| Data Structure |   `build(X)`    |    `find(x)`    | `insert/delete(x)` | `find_min/max()` | `find_prev/next(x)` |
| :------------- | :-------------: | :-------------: | :----------------: | :--------------: | :-----------------: |
| Array          |        n        |        n        |         n          |        n         |          n          |
| Sorted Array   |        n        |      log n      |         n          |        1         |        log n        |
| Direct Access  |        u        |        1        |         1          |        u         |          u          |
| Hash Table     | n<sub>(e)</sub> | 1<sub>(e)</sub> | 1<sub>(a)(e)</sub> |        n         |          n          |
| Set AVL        |     n log n     |      log n      |       log n        |      log n       |        log n        |

### Priority Queue

Priority Queues support a limited number of Set operations.

| Data Structure       | `build(X)` |     `insert(x)`     |   `delete_max()`    | `find_max()` |
| :------------------- | :--------: | :-----------------: | :-----------------: | :----------: |
| Dynamic Array        |     n      |   1<sub>(a)</sub>   |          n          |      n       |
| Sorted Dynamic Array |  n log n   |          n          |   1<sub>(a)</sub>   |      1       |
| Set AVL Tree         |  n log n   |        log n        |        log n        |    log n     |
| Binary Heap          |     n      | log n<sub>(a)</sub> | log n<sub>(a)</sub> |      1       |

### Changable Priority Queue

A Priority Queue augmented with a method to find an item and change it's priority.

| Data Structure | `build(X)` |   `delete_max()`    | `change_priority(item, priority)` | Dijkstra O(?) for `n = \|V\| = O(\|E\|)` |
| :------------- | :--------: | :-----------------: | :-------------------------------: | :--------------------------------------: |
| Array          |     n      |          n          |                 1                 |            \|V\|<sup>2</sup>             |
| Binary Heap    |     n      | log n<sub>(a)</sub> |               log n               |             \|E\| log \|V\|              |
| Fibonacci Heap |     n      | log n<sub>(a)</sub> |          1<sub>(a)</sub>          |         \|E\| + \|V\| log \|V\|          |

Implementations are ordered in order of difficulty of implementation. So if you know your graph ist sparse (`E = O(|V|)`) choose the Binary Heap implementation. If you know your graph is dense (`E = O(|V|<sup>2</sup>)`) choose the Array implementation. Choose the Fibonacci Heap implementation otherwise for best runtimes.

## Trees

- Binary Search Tree / Set Binary Tree
- [Binary Space Partitioning Tree](https://en.wikipedia.org/wiki/Binary_space_partitioning)
- [Spanning Tree](https://en.wikipedia.org/wiki/Spanning_tree)
- [Minimum Spanning Tree](https://en.wikipedia.org/wiki/Minimum_spanning_tree)
- Trie
- [Suffix Tree](https://en.wikipedia.org/wiki/Suffix_tree)
- Red Black Tree

### self balancing Trees

- AVL
  - Set AVL
  - Sequence AVL

## Heaps

- Binary Heap
  - use case: heap sort in place, priority queue

## Graphs

- BFS: choose if the weights are positive and bounded. We can transform a weighted graph into an unweighted one by inserting nodes until all edges have equal weight.
- DFS
- Full BFS/DFS
- Weighted Shortest Path (SSSP)
- DAG Relaxation: choose if the graph doesn't have cycles. Relax edges in topological order. A node `u` precedes `v` in the topological order, if there exists an edge from ´u´ to `v`
- Bellman-Ford
- Dijkstra: implemented as Changable Priority Queue. We run DAG Relaxation on a modified priority queue where Elements are nodes, each node has an ID and a priority (i.e. the distance to our source node `s`). The priority queue interface gets augmented with additional method `changePriority(ID, priority)`

### Single Source Shortest Path

| Name           | Graph Type |     Running Time O(?)     |    Weighted?     |
| -------------- | ---------- | :-----------------------: | :--------------: |
| BFS            | General    |      `\|V\| + \|E\|`      |        ❌        |
| DAG Relaxation | DAG        |      `\|V\| + \|E\|`      |        ✔         |
| Bellman-Ford   | General    |      `\|V\| * \|E\|`      |        ✔         |
| Dijkstra       | General    | `\|V\| log \|V\| + \|E\|` | (✔) non negative |

### All Pairs Shortest Path

- Floyd-Warshall <code>Θ(|V|<sup>3</sup>)</code>
- Johnson's algorithm: Run Bellman-Ford once and then |V| _ Dijkstra. Good for sparse graphs <code>O(|V|<sup>2</sup> log |V| + |V| _ |E|)</code>

## Consesus

- Paxos
- Raft

## Approximation Algorithms

[more...](http://www.cs.yale.edu/homes/aspnes/pinewiki/ApproximationAlgorithms.html)

## References

### Books

- [Grokking Algorithms: An illustrated guide for programmers and other curious people](https://www.manning.com/books/grokking-algorithms)
- [Introduction to Algorithms by Cormen, Leiserson, Rivest, and Stein (Third Edition, MIT Press)](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
- [Algorithms by Sedgewick and Wayne (4th Edition, Princeton)](https://algs4.cs.princeton.edu/home/)

### Courses

- [Introduction to Algorithms; MIT 2020](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-spring-2020/)
- [Design and Analysis of Algorithms; MIT 2015](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-design-and-analysis-of-algorithms-spring-2015/)

### Example Visualizations

- [Sorting and way-finding](https://clementmihailescu.github.io/Sorting-Visualizer/)
- [ALL the things](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)
