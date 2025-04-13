---
title: "DS - Unit-4 Q_Answered"
description: ""
summary: ""
date: 2025-01-01T16:00:52+05:30
lastmod: 2025-01-01T16:00:52+05:30
draft: false
weight: 282
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


#### Advanced concepts in Trees: AVL Search Trees: Need for AVL Search Trees, Definition, Balancing Trees (L-L Rotation, R-R Rotation, L-R Double Rotation, R-L Double Rotation)-, 

* How to overcome the drawbacks of Binary Search Tree (BST) using AVL tree? Illustrate with an example.

**Answer :**

A Binary Search Tree (BST) is a tree data structure in which each node has at most two children, and the key in the left subtree is less than the node’s key, while the key in the right subtree key is greater.

Drawbacks of BST:
* **BST can become Unbalanced** : If nodes are inserted in a sorted order (increasing or decreasing), the BST can become unbalanced and degenerate into a linear structure resembling a linked list.
* **Inefficient Operations** : In the worst case scenario, time complexity for search, insert, and deletion becomes O(n) due to unbalanced structure, where n is the number of nodes.

#### AVL Tree

An AVL tree is a self-balancing binary search tree, which automatically adjusts itself to ensure that it remains balanced. 

Characteristics of AVL trees:
* **Balance factor** : It ensures that the height of left and right subtrees of any node differ by at most 1 (i.e., the balance factor is -1, 0, or 1). An AVL tree keeps the BST properties while ensuring balance.

* If the balance factor is violated (i.e., it becomes -2 or 2), the tree performs rotations to restore balance. avoiding the worst-case scenario of a skewed tree.

* **Optimized Search** : Operations such as search, insertion, and deletion maintain a time complexity of **O(log n)** due to the balanced structure.


**Inserting nodes into a Binary Search Tree in increasing order:**

For the given sequence : 10, 20, 30, 40, 50, 25.  The tree becomes unbalanced with all nodes skewed to the right, making it inefficient for operations. The height of the tree is O(n), which means searching for a node will take O(n) time in the worst case.

```
          10
            \
            20
              \
              30
             /  \
            25  40
                  \
                  50
```

___

Inserting Same Nodes into an AVL Tree

- Insert: 10
```
   10
```

- Insert: 20
```
   10
     \
     20
```

- After inserting 30, the AVL tree detects an imbalance at node 10. The balance factor of 10 becomes -2, which triggers a left rotation at node 10 to restore balance.

After left rotation:
```
     20
    /  \
  10   30
```

- Insert: 40
```
     20
    /  \
  10   30
            \
            40
```

- After inserting 50, the AVL tree detects an imbalance at node 30. The balance factor of 30 becomes -2, which triggers a left rotation at node 30.

After left rotation:
```
     20
    /  \
  10   40
        /  \
      30   50
```

- After inserting 25, the AVL tree detects an imbalance at node 20. The balance factor of 20 becomes 2, which triggers a right left rotation.

```
     20
    /  \
  10   40
        /  \
      30   50
     /
   25
```

After right left rotation:
```
       30
      /  \
    20    40
   /  \     \
 10   25    50

```
Now, the tree is balanced, and the height of the tree is O(log n), ensuring that operations like search, insert, and delete will be efficient.

____

#### Discuss AVL tree and Write code to create AVL tree.

* How you balance an unbalanced AVL trees in the following cases: i. Left of Left(L-L)     ii. Right of Right(R-R) iii. Right of Left(R-L)    iv. Left of Right(L-R) Explain with suitable examples.
* Explain the Rotate Left and Double Rotation Left algorithms used for AVL tree balancing with a suitable example.
* Write algorithms to RotateRight and RotateLeft in an AVL tree.
* Explain the following AVL Tree balancing procedures giving suitable examples: Double Rotation Right and Double Rotation Left.
* Explain the Rotate right and Double Rotation Right algorithms used for AVL Tree balancing with a suitable example

**Answer :**

An AVL Tree is a self-balancing binary search tree (BST) where the height difference (or balance factor) between the left and right subtrees of any node is at most 1 by using rotations. 

`Balance Factor = Height of Left Subtree - Height of Right Subtree`.
For a node to be balanced, its balance factor should be in the range of -1 to +1.

If the balance factor becomes less than -1 or greater than 1 due to an insertion or deletion, the tree becomes unbalanced and must be rebalanced using rotations.

There are four common cases of AVL tree imbalance:
- Left-Left (L-L)
- Right-Right (R-R)
- Left-Right (L-R)
- Right-Left (R-L)

These imbalances in AVL trees are handled using single rotations (left or right) and double rotations (left-right or right-left).

This property ensures that the tree remains balanced, meaning the height of the tree is always O(log n), where n is the number of nodes in the tree. This gives the AVL tree efficient time complexity for operations like search, insert, and delete.

---

**Left-Left (L-L) Case:**

Occurs when a node is inserted into the **left subtree of the left child** of an unbalanced node. (Left child of the left subtree causes the imbalance. 

To fix this, a single right rotation is performed on the root of the subtree.
* Set the left child of the current root as the new root
* Make the right child of new root(20) as the left child of the current root (30)
* Set Current root (30) as the right child of the new root (20).

```
      30
     /   
   20      
  /   
10

After right rotation to node 30:

      20
     /  \
   10    30
```


**Right-Right (R-R) Case** :  

Occurs when a node is inserted into the **right subtree of the right child** of an unbalanced node. (Right child of the right subtree causes the imbalance).

To fix this, we perform a single left rotation on the root of the subtree.
* Set the right child of current root as new root. 
* Make the left child of the new root (20) the right child of the current root (10).
* Set the current root (10) as the left child of the new root (20).
```
    10
      \
      20
        \
        30

After left rotation at node 10:

      20
     /  \
   10    30
```


**Right-Left (R-L) Case** : 

Occurs when a node is inserted into the **left subtree of the right child** of an unbalanced node.

To fix this, we perform a double rotation(Right-Left)
* Right rotation on the right child of the root. 
* Left rotation on the unbalanced root.

```
      10
        \
         30
        /
      20

Right Rotation on 30:

      10
        \
        20
          \
          30

Left rotation on 10:

      20
     /  \
   10    30
```


**Left-Right (L-R) Case** : 

Occurs when a node is inserted into the **right subtree of the left child** of an unbalanced node.

To fix this, we perform a double rotation(Left-Right)
* Left rotation on the left child of the root. 
* Right rotation on the unbalanced root.

```
      30
     /
   10
     \
     20

Left Rotation on 10:

      30
     /
   20
   /
 10

Right Rotation on 30:

      20
     /  \
   10    30
```


_____

#### AVL tree Operations: Insertion, Deletion. 

* Show the AVL tree that results after each of the integer keys  `9, 27, 50, 15, 2, 21, 36` are inserted, in that order, into an initially empty AVL tree.  Clearly show the tree that results after each insertion, and make clear any rotations that must be performed.

* Construct AVL tree for the following data:  `21,26,30,9,4,14,28,18,15,10,2,3,7`

* Construct the AVL tree mentioning the balance factor from the following data  `13, 5, 1, 7, 8, 98, 67, 26, 33, 12, 6, 7, 8.`

* Define AVL tree. Construct the AVL tree mentioning the balance factor from the following data: `14, 6, 1, 7, 8, 99, 68, 26, 33, 12, 6, 7, 8.`

* Construct an AVL tree utilizing the given dataset. Display the balance factors in the resultant tree. Data: `17, 28, 9, 13, 35, 42, 65, 50, 73` After insertion of 20 and 45, update the AVL tree.

* Create an AVL tree using the following data .Show the balance factors in the resulting tree. `24,45, 28, 12,23, 32,14,67`.  Insert 48 and 52 into the tree created.

* Create an AVL tree using the following data. Show the balance factors in the resulting tree. `14 23 7 10 33 56 80 66 70` Insert 44 and 50 into the tree created.


_____

#### Heaps – Definition, Heap Maintenance operations: insertion and deletion. Rheapup, Rheapdown algorithms and heap implementation, Applications.

* What are the applications of Heap? Write the algorithm for Reheap UP and Reheap Down operation.
* Discuss algorithms used in Heap construction with a suitable example: i) reheap up    ii) reheap down
* Explain the algorithms to perform following operations with an example: i) Max heap construction ii) Max heap deletion.
* Explain the reheap up and reheap down algorithms used in Heap construction with a suitable example.

**Answer :**

A heap is a special tree-based data structure that satisfies the heap property.

In a max-heap, every parent node is greater than or equal to its children; in a min-heap, every parent node is less than or equal to its children. 

##### Common Applications of Heap:

* **Priority Queues** – Efficient for accessing the highest or lowest priority element.

* **Heap Sort** – comparison-based, in-place sorting algorithm that uses a binary heap to sort elements.

* **Dijkstra’s Algorithm** – For finding the shortest path in graphs.

* **Job Scheduling Systems** – For scheduling jobs/tasks based on priority.

* **Median Maintenance in data streams** – Heaps are used in real-time to keep track of medians of dynamic stream of numbers.

* **Data Stream Management** – For maintaining top-k elements in a stream of data efficiently. (Trending hashtags, top-scoring users in games, real-time recommendation systems)

___

Heap Construction Algorithms **Reheap Up** and **Reheap Down** operations maintain the heap structure:
- Reheap Up restores the heap property after insertion.
- Reheap Down restores the heap property after deletion.

Both operations ensure that a heap maintains O(log n) time complexity, making heaps suitable for efficient implementations of priority queues, heap sort, and graph algorithms like Dijkstra’s algorithm.

___

**Reheap Up** : is used when adding a new element to the heap. 
* The new element is inserted at the end of the heap to maintain CBT structure.
* Compare the inserted element with its parent.
* if the element is greater (in max-heap), swap with its parent.
* Repeat until the heap property is restored or the element reaches the root.
* reheapUp is used to maintain the heap property by moving the element up the tree until it reaches the correct position.

Starting with an empty heap, let’s insert the elements: `[10, 20, 30, 15, 5]`

Insert 10: Heap = `[10]`

Insert 20: Heap = `[10, 20]`
- Compare 20 with its parent (10). Since 20 > 10, swap them.
- Heap = `[20, 10]`

Insert 30: Heap = `[20, 10, 30]`
- Compare 30 with its parent (10). Since 30 > 10, swap them.
- Heap = `[20, 30, 10]`
- Compare 30 with its new parent (20). Since 30 > 20, swap them.
- Heap = `[30, 20, 10]`

Insert 15: Heap = `[30, 20, 10, 15]`
- Compare 15 with its parent (20). Since 15 < 20, no need to swap.
- Heap = `[30, 20, 10, 15]`

Insert 5: Heap = `[30, 20, 10, 15, 5]`
- Compare 5 with its parent (15). Since 5 < 15, no need to swap.
- Heap = `[30, 20, 10, 15, 5]`

Final Heap: `[30, 20, 10, 15, 5]`

______

**Reheap Down** : is used when the root of the heap is removed. 
* Replace the root with the last element
* Compare the new root with its children
* Swap If the root is smaller than the larger child (in max-heap)
* Repeat until the heap property is restored

Starting with the heap: `[30, 20, 10, 15, 5]`, let’s remove the root (30) and perform a reheap down.

Remove root 30: Move 5 to the root: `[5, 20, 10, 15]`
* Compare 5 with its children (20 and 10). The largest child is 20.
* Swap 5 and 20: `[20, 5, 10, 15]`
* Now, compare 5 with its new children (15). The largest child is 15.
* Swap 5 and 15: `[20, 15, 10, 5]`

Final Heap after reheap down: `[20, 15, 10, 5]`

ReheapDown is then used to maintain the heap property by moving the element down the tree until it reaches the correct position.

____

* Define Heap? Write Heap sort Algorithm and sort the below tree.
```
                    27
                  /    \
                14      35
               /  \    /  \
             10   19  31   42
```

**Answer :**



____

* Show construction of a heap from the following data  `30, 4, 12, 9, 19, 50, 65, 60, 20, 17`. Insert 75 into the Heap and reheapify.

* Show construction of a heap from the following data read from the keyboard: `42, 23, 74, 11, 65, 58, 94`. Insert 36 into the heap and reheapify

* Show the construction of max-heap to sort the following numbers by mentioning the steps clearly: `82, 90, 10, 12, 15, 77, 55, 23` . Delete 90 from the heap and heapify.

* Show construction of a heap from the following data read from the keyboard: `20, 35, 9, 26, 49, 78, 2`. Insert 46 into the heap and reheapify

* Show construction of a heap from the following data read from the keyboard: `21, 37, 10, 26, 50, 76, 5` Insert 45 into the heap and reheapify.

* Construction the heap tree from the following data : `32, 8, 21, 18, 39, 55, 75, 80, 40, 99.` Design an algorithm for the same.



___

