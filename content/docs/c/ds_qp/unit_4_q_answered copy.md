---
title: "DS - Unit-4 Questions Answered"
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

A Binary Search Tree (BST) is a tree data structure in which each node has at most two children, and the left child’s key is less than the parent’s key, while the right child’s key is greater than the parent’s key.

Drawbacks of BST:
1. Can become Unbalanced : If nodes are inserted in a sorted order (increasing or decreasing), the BST can become unbalanced and resemble a linked list.
2. Inefficient Search : In the worst case, searching, inserting, and deleting in a degenerate BST becomes inefficient with O(n) time complexity, where n is the number of nodes.

An AVL tree is a self-balancing binary search tree, which automatically adjusts itself to ensure that it remains balanced. It ensures that the height of the left and right subtrees of any node differ by at most 1 (i.e., the balance factor is -1, 0, or 1). An AVL tree keeps the BST properties while ensuring balance.

If the balance factor is violated (i.e., it becomes -2 or 2), the tree performs rotations to restore balance. avoiding the worst-case scenario of a skewed tree.

Optimized Search: By keeping the height of the tree logarithmic (O(log n)), the search, insertion, and deletion operations are efficient.


Inserting nodes into a Binary Search Tree in increasing order:  10, 20, 30, 40, 50, 25. The tree becomes unbalanced with all nodes skewed to the right, making it inefficient for operations. The height of the tree is O(n), which means searching for a node will take O(n) time in the worst case.

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
  10    30
```

- Insert: 40
```
	 20
	/  \
  10    30
		 \
	      40
```

- After inserting 50, the AVL tree detects an imbalance at node 30. The balance factor of 30 becomes -2, which triggers a left rotation at node 30.

After left rotation:
```
	 20
	/  \
  10    40
		/  \
	  30    50
```

- After inserting 25, the AVL tree detects an imbalance at node 20. The balance factor of 20 becomes 2, which triggers a right left rotation.

```
	 20
	/  \
  10    40
		/  \
	  30    50
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
If the balance factor is less than -1 or greater than 1, the tree is unbalanced and requires a rotation The four common cases of imbalance in AVL trees are handled using single rotations (left or right) and double rotations (left-right or right-left).

This property ensures that the tree remains balanced, meaning the height of the tree is always O(log n), where n is the number of nodes in the tree. This gives the AVL tree efficient time complexity for operations like search, insert, and delete.

---

There are four main cases of unbalanced AVL trees:

1. Left-Left (L-L) Case: Occurs when the left child of the left subtree causes the imbalance. To fix this, we perform a right rotation on the root of the subtree.
* Set the left child of the current root as the new root
* Make the right child of new root(20) as the left child of the current root (30)
* Set Current root (30) as the right child of the new root (20).

```
	  30
	 /   
   20      
  /   
10

After right rotation:

	  20
	 /  \
   10    30
```

2. Right-Right (R-R) Case: Occurs when the right child of the right subtree causes the imbalance. To fix this, we perform a left rotation on the root of the subtree.
* Set the right child of current root as new root. 
* Make the left child of the new root (20) the right child of the current root (10).
* Set the current root (10) as the left child of the new root (20).
```
  10
	\
	20
	  \
	  30
	  
After left rotation:

	  20
	 /  \
   10    30
```

3. Right-Left (R-L) Case: Occurs when the right child of the left subtree causes the imbalance. To fix this, we first perform a right rotation on the right child of the root. Then perform left rotation on the root.

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

4. Left-Right (L-R) Case: Occurs when the left child of the right subtree causes the imbalance. To fix this, we first perform a left rotation on the left child and of the root. Then perform a right rotation on the root.

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
* Discuss algorithms used in Heap construction with a suitable example: reheap up and reheap down
* Write the algorithm for Reheap UP and Reheap Down operation.
* Explain the reheap up and reheap down algorithms used in Heap construction with a suitable example.
* Define heap. Write the algorithm for reheap up and reheap down

**Answer :**

Heap Construction Algorithms:
1. Reheap Up: is used when adding a new element to the heap. The new element is initially placed at the end of the heap, and then reheapUp is used to maintain the heap property by moving the element up the tree until it reaches the correct position.

2. Reheap Down: is used when the root of the heap is removed, and the last element in the heap is moved to the root. ReheapDown is then used to maintain the heap property by moving the element down the tree until it reaches the correct position.

Both operations have O(log n) time complexity, ensuring that the heap remains efficient for priority queue operations.


Reheap Up Operation on insertion : 

* The Reheap Up (or Bubble Up) operation is used when an element is added to the heap typically inserted at the end of the tree from left t right following the complete binary tree rules.
* After the insertion, we need to ensure that the heap property is maintained by comparing the inserted element with its parent and swapping them if value it is larger (in a max-heap) or smaller (in a min-heap).
* Repeat until the element is in the correct position, or it becomes the root.

Starting with an empty heap, let’s insert the elements: `[10, 20, 30, 15, 5]`
1. Insert 10: Heap = `[10]`
2. Insert 20: Heap = `[10, 20]`
    - Compare 20 with its parent (10). Since 20 > 10, swap them.
    - Heap = `[20, 10]`
3. Insert 30: Heap = `[20, 10, 30]`
    - Compare 30 with its parent (10). Since 30 > 10, swap them.
    - Heap = `[20, 30, 10]`
    - Compare 30 with its new parent (20). Since 30 > 20, swap them.
    - Heap = `[30, 20, 10]`
4. Insert 15: Heap = `[30, 20, 10, 15]`
    - Compare 15 with its parent (20). Since 15 < 20, no need to swap.
    - Heap = `[30, 20, 10, 15]`
5. Insert 5: Heap = `[30, 20, 10, 15, 5]`
    - Compare 5 with its parent (15). Since 5 < 15, no need to swap.
    - Heap = `[30, 20, 10, 15, 5]`

Final Heap: `[30, 20, 10, 15, 5]`

____

Reheap Down (Bubble Down) Operation on deletion :

* The Reheap Down (or Bubble Down) operation is used when an element is removed from the heap (usually the root). 
* After the removal, the last element in the heap is moved to the root to maintain the CBT structure property
* To restore the heap property by comparing the new root with its children and swapping it with the larger (in a max-heap) or smaller (in a min-heap) child.
* Repeat until the heap property is in correct position or becomes a leaf node.

Starting with the heap: `[30, 20, 10, 15, 5]`, let’s remove the root (30) and perform a reheap down.
1. Remove root 30: Move 5 to the root: `[5, 20, 10, 15]`
2. Compare 5 with its children (20 and 10). The largest child is 20.
3. Swap 5 and 20: `[20, 5, 10, 15]`
4. Now, compare 5 with its new children (15). The largest child is 15.
5. Swap 5 and 15: `[20, 15, 10, 5]`
Final Heap after reheap down: `[20, 15, 10, 5]`


_____

Define Heap? Write Heap sort Algorithm and sort the below tree.
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

