# Tree and graph

## Type of trees

### tree vs binary tree vs binary search tree

* For binary search tree, all the nodes on the left subtree are smaller than the parent, and all the nodes on the right are larger

![binary search tree](http://cramster-image.s3.amazonaws.com/definitions/computerscience-5-img-1.png )

## Tree traversal
[From wiki](https://en.wikipedia.org/wiki/Tree_traversal)

### 1. In-order traversal
```
inorder(node)
  if (node = null)
    return
    
  inorder(node.left)
  visit(node)
  inorder(node.right)
```
### 2. Pre-order traversal

```
preorder(node)
  if (node = null)
    return
  visit(node)
  preorder(node.left)
  preorder(node.right)
```
### 3. Post-order traversal

```
postorder(node)
  if (node = null)
    return
  postorder(node.left)
  postorder(node.right)
  visit(node)
```

Exercise:
* [binary-tree-inorder-traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

### The use of 3 ways:

The traversal strategy the programmer selects depends on the specific needs of the algorithm being designed. The goal is speed, so pick the strategy that brings you the nodes you require the fastest.

1. If you know you need to explore the roots before inspecting any leaves, you pick pre-order because you will encounter all the roots before all of the leaves.
2. If you know you need to explore all the leaves before any nodes, you select post-order because you don't waste any time inspecting roots in search for leaves.
3. If you know that the tree has an inherent sequence in the nodes, and you want to flatten the tree back into its original sequence, than an in-order traversal should be used. The tree would be flattened in the same way it was created. A pre-order or post-order traversal might not unwind the tree back into the sequence which was used to create it.

## Heap and Priority Queue
[Binary Heap](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Binary%20Heaps/heaps.html)

### Binary Heap
A binary heap is a complete binary tree which satisfies the heap ordering property. The ordering can be one of two types:

* the min-heap property: the value of each node is greater than or equal to the value of its parent, with the minimum-value element at the root.
* the max-heap property: the value of each node is less than or equal to the value of its parent, with the maximum-value element at the root.
 
#### Time complexity

Operation | Time Complexity
---|---
find-min | Θ(1)
delete-min | Θ(log n)
insert | O(log n)
decrease-key | Θ(log n)
merge | Θ(n)


### Priority Queue
Priority queues are useful for any application that involves processing elements based on some priority. It supports two major operations insert(object) and deleteMin(). The elements of a priority queue must be comparable to each other, either through the Comparable or Comparator interfaces.

### heap in python 
Heap can be used by 
```
import heapq
```
Here are methods inside this module

* heapq.heappush(heap,item) : 
Push the value item onto the heap, maintaining the heap invariant.

* heapq.heappop(heap):
Pop and return the smallest item from the heap, maintaining the heap invariant. If the heap is empty, IndexError is raised. To access the smallest item without popping it, use heap[0].

* heapq.heapify(x):
Transform list x into a heap, in-place, in linear time.
* heapq.nlargest(n, iterable[, key]):
Return a list with the n largest elements from the dataset defined by iterable. key, if provided, specifies a function of one argument that is used to extract a comparison key from each element in the iterable: key=str.lower Equivalent to: sorted(iterable, key=key, reverse=True)[:n]

Note that Heap elements can be tuples. This is useful for assigning comparison values (such as task priorities) alongside the main record being tracked:

```
>>> h = []
>>> heappush(h, (5, 'write code'))
>>> heappush(h, (7, 'release product'))
>>> heappush(h, (1, 'write spec'))
>>> heappush(h, (3, 'create tests'))
>>> heappop(h)
(1, 'write spec')
```
the first elements of tuples with be heapified
## Graph search

### BFS


```
BFS(G, s)
For each vertex u exept s
    Do Color[u] = WHITE
        Distance[u] = MAX
        Parent[u] = NIL
Color[s] = GRAY
Distance[s] = 0
Parent[s] = NIL
Enqueue(Q, s)
While Q not empty
    Do u = Dequeue(Q)
        For each v is the neighbor of u
            Do if Color[v] == WHITE
                Color[v] = GRAY
                Distance[v] = Distance[u] + 1
                Parent[v] = u
                Enqueue(Q, v)
            Color[u] = BLACK”
```
### DFS

```
DFS(G)
For each vertex v in G
    Do Color[v] = WHITE
    Parent[v] = NIL
For each vertex v in G
    DFS_Visit(v)

DFS_Visit(u)
Color[u] = GRAY
For each v is the neighbor of u
    If Color[v] == WHITE
        Parent[v] = u
        DFS_Visit(v)
Color[u] = BLACK
```
