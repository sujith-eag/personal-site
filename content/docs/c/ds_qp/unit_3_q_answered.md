---
title: "DS - Unit-3 Q_Answered"
description: ""
summary: ""
date: 2025-01-01T16:00:52+05:30
lastmod: 2025-01-01T16:00:52+05:30
draft: false
weight: 280
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



##### Trees: Importance of Trees, Basic Tree Concepts and Terminologies: node, path, degree, internal nodes, height and subtree. 
##### Binary Tree: Binary Trees, Binary Tree Representations, Representing Lists as Binary trees, Minimum nodes, Maximum nodes, Nearly complete binary tree


* Give the properties of binary trees that distinguish them from general trees.
* Explain how to change a general tree into a binary tree with an example.


____

Explain the Level of a tree with example. In a Binary Tree what is the maximum number of nodes that can be found in level 12.

With a suitable examples, define the following:
i) Binary tree
ii) Degree of a node
iii) Level of a binary tree
iv) Complete binary tree
v) Nearly complete binary tree.
vi) Height of a tree
vii) Binary Search Tree.
viii) Expression Tree



_____

#### Tree Traversals Depth First Traversal (Preorder, Inorder and Postorder), Breadth First Traversal, 


* Write the algorithm for Binary Tree Inorder, Preorder and Postorder traversal.




____

Find the following in the tree given:
i. Balance factor of the tree.
ii. Show the depth first traversal (preorder, inorder and postorder) of the tree.
iii. Show the breadth first traversal of the tree.

```
                           10
                        /      \
                      8         11
                    /              \
                  2                 14
                /   \              /    \
              1      6            13    16
                    / 
	               4   
                 / \
                3   5
```

Traverse the given tree using Inorder and Postorder traversals.
```
                        A
                    /       \
                  B           C
               /    \       /    \
             D       E    F      G
               \               /   \
	            H             I     J
```

Find the following in the tree given: 
```
                        125
                    /        \
                  15          50
                /   \       /     \
              10     22   35      70
            /  \   /  \  /  \    /    \
           4   12 18  24 31  44 66    90
```
i) Balance factor of the tree.
ii) Show the depth first traversal (preorder, inorder and postorder) of the tree.
iii. Show the breadth first traversal of the tree.


Find the following in the tree given:
```
                           A
                         /   \
                        B     F
                       /       \
                      C         G
                    /   \      / | \
                   D     E    H  I  J
			                     |
		                         K

```
i) Balance factor of the tree.  
ii) Show the depth first traversal (preorder, inorder and postorder) of the tree.  
iii) Show the breadth first traversal of the tree.

____


Generate Binary Tree looking into the following tree traversals:
Preorder: ABDGCEHIF
Inorder: DGBAHEICF

**Answer :**

Steps to construct the binary tree:
1. Preorder traversal: The first node in preorder is always the root of the tree. The root will be A.

2. Inorder traversal: In the inorder traversal, all nodes to the left of the root node A (in the inorder sequence) will form the left subtree, and all nodes to the right will form the right subtree.    
    Inorder sequence: DGBAHEICF . The root A is at index 3 in the inorder sequence, so:
	- Left subtree nodes: DGB
	- Right subtree nodes: HEICF
3. Now, we need to continue recursively for both left and right subtrees.

Left subtree of A: 
- From the preorder traversal, after A, the next nodes for the left subtree are B, D, and G.
- Inorder for left subtree: From the inorder traversal, the nodes corresponding to the left subtree are DGB.
    - Root of the left subtree is B (from preorder), so:
        - Left subtree of B: D
        - Right subtree of B: G


Right Subtree of A:
- Preorder for right subtree: From the preorder traversal, after A and its left subtree, the next nodes for the right subtree are C, E, H, I, F.
- Inorder for right subtree: From the inorder traversal, the nodes corresponding to the right subtree are HEICF.
    - Root of the right subtree is C (from preorder), so:
        - Left subtree of C: E and H
        - Right subtree of C: I and F

```
                           A
                        /     \
                      B        C
                    /   \     /   \
                   D     G   E     F
                          /        /
                         H         I
                                    \
                                     K
```


____

Generate binary trees looking into the following tree traversals.
i. Inorder: E A C K F H D B G    Preorder: F A E K C D H G B

ii. Inorder : 2 6 7 1 4 8 3 5 9     Postorder: 7 6 2 8 4 9 5 3 1

i. Preorder: ABDGCEHIF;     Inorder: DGBAHEICF

ii. Postorder: IEJFCGKLHDBA;    Inorder: EICFJBGDKHLA


____

### Construction of Expression Tree.


* Define expression tree. Write the procedure to construct the expression tree from an infix expression.

* Give the algorithms for pre-order and post-order tree traversals. Represent the following expression using binary tree and write the pre-order and Post-order traversals for the tree generated.  

* `A + ( B - C ) * D $ ( E * F )`
* `( a / ( b + c )) + (((d / e) - f) * g)`     
* `( A + B * C ) $ ( ( D + E ) * F )`     
* `( M / ( N + O )) + ((( P / Q ) - R ) * S)`
* `( A + B * C ) $ (( D + E ) * F)`
* `( 5 + 6 * 7 ) $ ( ( 5 + 6 ) * 7 ))`





_____

#### Binary Search Tree: Binary Search Trees – Basic Concepts, Operations (Insertion, Deletion, Find the smallest node, Find the largest node, and Find a requested node), Applications, 


* Write an algorithm to insert and delete an element in a Binary Search Tree.

* Explain algorithm to delete a node from the Binary Search Tree (BST) with an appropriate example.

* Write an algorithm to delete a node from the Binary Search Tree (BST). Explain with an appropriate example.

* Write algorithms to perform the following operations on a BST: i. Search for a requested node  ii. Add a new node.

* Write the algorithms for the following operations in Binary Search Tree (BST). i) Smallest node in a BST ii) Add node to BST iii) Search an item in a BST

* Write algorithms to find Smallest node and largest node in a Binary Search Tree.

* Write C function to find the maximum element in BST.




_____


What is Binary Search Tree? List the applications of Binary Search Tree. Create a binary search tree using the following data entered as a sequential set:
`14, 15, 12, 23, 5, 7, 7, 10, 33, 80, 66` Also perform inorder and preorder traversal for the created tree.


Construct the Binary search for the following set of numbers `14, 17, 11, 7, 53, 4, 13, 12, 8, 60, 19, 16`.  Perform inorder, preorder and postorder traversals of the obtained tree.


Construct the Binary Search Tree (BST) from the following elements  `D A T A S T R U C T U R E A N D A L G O R I T H M S` also write the in-order, pre-order and post-order traversals for the BST generated.


Construct the Binary Search Tree (BST) from the following elements: `D A T A S T R U C T U R E S U S I N G C` also write the in-order, pre-order and post-order traversals for the BST generated.



____

### Threaded Binary Trees.

With suitable example, illustrate Threaded Binary tree.

Explain threaded binary trees and their representation with a neat diagram. Also develop function to do the inorder traversal of a threaded binary tree.

What area threaded tree and its advantage?

Define and give an example for Threaded Binary tree.

Write short note on: Threaded Binary Tree.

Define Threaded Binary Tree and show its representation.

**Answer :**

A Threaded Binary Tree is a binary tree in which null pointers (those pointing to child nodes that do not exist) are replaced by threads. 

In a normal binary tree, each node has two pointers: left and right for each child. If a node does not have a left or right child, those pointers are set to NULL.

In a threaded binary tree, we replace these NULL pointers with threads:
- A left thread is used to point to the inorder predecessor (the node that would come before it in an inorder traversal).
- A right thread is used to point to the inorder successor (the node that would come after it in an inorder traversal).

This modification allows us to traverse the tree in inorder without needing a stack or recursion, simply by following the left and right threads.


There are two types of threaded binary trees:
1. **Single Threaded Binary Tree**: In this type, only one set of threads is used (either left or right). The **left thread** points to the inorder predecessor, or the **right thread** points to the inorder successor.

2. **Double Threaded Binary Tree**: In this type, both the **left** and **right** pointers are used for threading. The **left thread** points to the inorder predecessor, and the **right thread** points to the inorder successor.

```
        10
       /  \
      5    15
     / \     \
    3   7    20
```

(Proper Diagram needed)

____

To perform the **inorder traversal** of a threaded binary tree, we need to follow the **threads** instead of using recursion or a stack. Here’s how it works:

1. Start from the **leftmost node**.
2. Visit the node.
3. If the node has a right thread, move to the inorder successor using the right thread.
4. If the node has no right child, move to its parent (using the thread in the left pointer if it exists).
5. Repeat the process until all nodes are visited.

____

