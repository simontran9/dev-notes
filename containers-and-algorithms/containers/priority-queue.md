# Priority queue

## Operations

| **Operation**     | **Description**                                                                  |
| ----------------- | -------------------------------------------------------------------------------- |
| `top()`           | Returns the element with the top priority without removing it.                   |
| `add(element: E)` | Adds an element to the priority queue.                                           |
| `remove_top()`    | Removes and returns the element with the highest priority in the priority queue. |

## Binary heap

### Definition

A binary heap is a binary tree with the following two properties:
1. Complete property: All the levels of a heap are completely filled, except (possibly) for the last level. The filled items in the last level are left-justified.
2. Heap-order property: For any node $i$, the key of the key of parent of $i$ is larger than or equal to key of $i$ if it's a max heap, and the key of parent of $i$ is less than or equal to key of $i$ if it's a min heap.

### Storing heaps

Heaps are usually stored in dynamic arrays, where:
- the root node is at index $0$
- the left child of node $i$ is node $2i + 1$
- the right child of node $i$ is node $2i + 2$
- the parent of node $i$ is node $\lfloor \frac{i - 1}{2} \rfloor$

![[Pasted image 20250222075606.png]]
### Time complexity

| **Operation** | **Time complexity**    |
| ------------- | ---------------------- |
| Build heap    | Worst-case $O(n)$      |
| Lookup        | Worst-case $O(1)$      |
| Insertion     | Worst-case $O(\log n)$ |
| Deletion      | Worst-case $O(\log n)$ |

### Node sifting mechanisms

**Sift up**
For some node, we repeatedly "sift" the node "up" if the node's key is less than its parent's key (min-heap) or if the node's key is greater than its parent's key (max-heap) by swapping positions with its parent.

**Sift down**
For some node, we repeatedly "sift" the node "down" when its key is greater than one of its children's key by swapping it with the smallest children (min-heap) or when its key is less than one of its children's key by swapping it with the largest children (max-heap).

### Building a heap from initial elements

To build a heap from initial elements of a list in $O(n)$ worst case time, we build in a bottom-up manner as follows:
1. Copy over all elements in the original list into the backing dynamic array
2. Beginning at the parent of the last element in the dynamic array, and repeatedly call sift down

### Search

Typically, binary heaps are used as containers for priority queues, so a lookup will usually be for the topmost element in the heap, so we simply return the element at index $1$. However, for any other elements, we have to perform a linear search.

### Insertion

1.  Add an element as the rightmost leaf of the heap (i.e. the last element in the backing array).
2. Sift up the node containing the element to correct its position within the tree.

### Deletion

1. Set the root node's key to be the same key of the last node in the heap.
2. Remove the last node in the heap now that we've placed its key in the root node.

