---
title: "DS - Unit-5 Questions Answered"
description: ""
summary: ""
date: 2025-01-01T16:00:52+05:30
lastmod: 2025-01-01T16:00:52+05:30
draft: false
weight: 284
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



#### Multi-way trees: Introduction, Definition, features. B-trees – Introduction, Definition and features, 

* Illustrate the properties of m-way tree with an example.
* Explain simplified B-tree with an example.
* Define and explain with example for the following: i. m-way tree   ii. B-tree   iii. 2-3 tree    iv. 2-3-4 tree

**Answer :**

i. M-way Tree : is a tree data structure where each node can have at most **m** children. It is a generalization of a binary tree where each node can have more than two children. The number **m** refers to the maximum number of children that a node can have.
- Each node in the tree can have up to m children.
- The root node may have fewer than m children, but non-root nodes must have between ⌈m/2⌉ and m children.
- The tree is balanced, meaning the depth of all leaf nodes is the same.


For a 3-way tree (a ternary tree), each node can have at most 3 children.

```
        A
     /  |  \
    B   C   D
   / \   |
  E   F  G
```

____

ii. B-tree : is a self-balancing tree data structure that maintains sorted data and allows for efficient insertion, deletion, and searching operations. It is commonly used in databases and file systems where large blocks of data need to be managed efficiently.
- All leaves are at the same level.
- The tree is balanced, and the height of the tree is logarithmic with respect to the number of elements.
- The B-tree ensures that operations like search, insert, and delete are efficient with a time complexity of \(O(\log n)\).

B-tree of order m is a tree where:
  - Each node can have up to m children.
  - Each node (except the root) must have at least ⌈m/2⌉ children.
  - Each node can store up to m-1 keys (values).

Consider a B-tree of order 3 (m = 3). Each node can hold up to 2 keys and have up to 3 children.
```
          [10, 20]
         /   |   \
       [5]  [15] [25, 30]
```

____

iii. 2-3 Tree :  is a special type of balanced search tree where every internal node can have either 2 or 3 children. It is a type of B-tree of order 3.
- Every path from the root to a leaf has the same length (the tree is balanced).
- The tree ensures logarithmic time complexity for search, insertion, and deletion operations.

In a 2-3 tree:
  - 2-node: A node that has 1 key and 2 children.
  - 3-node: A node that has 2 keys and 3 children.

```
           [10, 20]
         /     |     \
    [5]      [15]    [25, 30]
```

- The root node has 2 keys: 10 and 20, and 3 children.
- The left child is a 2-node with the key 5.
- The middle child is a 2-node with the key 15.
- The right child is a 3-node with keys 25 and 30.

____

iv. 2-3-4 Tree:  is a self-balancing tree where each node can have 2, 3, or 4 children and can store 1, 2, or 3 keys, respectively. This tree is a generalization of both the 2-tree and 3-tree and is also a type of B-tree.
- 2-node: A node with 1 key and 2 children.
- 3-node: A node with 2 keys and 3 children.
- 4-node: A node with 3 keys and 4 children.

Like 2-3 trees, the 2-3-4 tree is balanced, with all leaves at the same level.

It supports efficient insertion and deletion operations, with a time complexity of \(O(\log n)\).

The 2-3-4 tree can be converted into a B-tree of order 4, meaning it is essentially a B-tree with a maximum of 4 children per node.

```
           [10, 20, 30]
         /    |    |    \
   [5]   [15]  [25]   [35, 40]
```

- The root node contains 3 keys: 10, 20, and 30, and has 4 children.
- The leftmost child is a 2-node with the key 5.
- The second child is a 2-node with the key 15.
- The third child is a 2-node with the key 25.
- The rightmost child is a 3-node with the keys 35 and 40.

____

| Tree Type  | Number of Children per Node | Number of Keys per Node |
| ---------- | --------------------------- | ----------------------- |
| M-way Tree | Up to m                     | Varies, typically m-1   |
| B-tree     | Up to m                     | m-1                     |
| 2-3 Tree   | 2 or 3                      | 1 or 2                  |
| 2-3-4 Tree | 2, 3, or 4                  | 1, 2, or 3              |

____

* Draw complete 2-3 and 2-3-4 trees.

* Calculate the maximum number of data entries in a:  i) 3-way tree of height 3   ii) m-way tree of height h  iii) B-Tree of order 5 with a height of h.

**Answer :**



________

#### Construction of B-trees of order 3, order 4 and order 5, Implementation, Simplified B-Trees: 2-3 tree, 2-3-4 tree.

* List the properties of B-tree. Explain the insertion operation in B-tree using essential data of your choice.
* Construct B-tree of order 4 from the following elements given as follows: `1,6,8,2,9,12,15,7,18,3,4,20.`
* Construct a B-tree of order 4 created by inserting the following data arriving in sequence: `92, 24, 6, 7, 11, 8, 22, 4, 5, 16, 19, 20, 78.`
* Draw the B-tree of order 3 created by inserting the following data arriving in sequence: `92, 24, 6, 7, 11, 8, 22, 4, 5, 16, 19, 20, 78`
* Draw a B-tree of order 5 for the following set of elements arriving in the sequence:  `76, 21, 14, 11,97, 85, 74, 63, 45, 42, 57, 20, 16, 19, 52, 30, 21`

____

* Explain the characteristics of 2-3 trees. Formulate the procedure to design a 2-3 tree for the given input:  `10, 6, 8, 5, 1, 4, 7.`

* Create a 2-3 tree of order 3 for the following data arriving in sequence. `11, 12, 8, 20, 25, 16, 12, 26, 17, 27, 52, 16, 48, 68, 3, 26, 29, 53, 95, 55.`

____

#### Graphs: Basic concepts, Terminologies: vertices, edge, cycle, loop, graph vs tree, operations: insert vertex delete vertex, insert edge, delete edge. 

* Define the following with reference to Graph and an example for each: Path, Cycle, Loop, Degree, Weighted Graph, Out-Degree and In-Degree.

**Answer :**

- Path: A sequence of vertices with edges between them.
- Cycle: A path where the first and last vertex are the same and no other vertex is repeated.
- Loop: An edge that connects a vertex to itself.
- Degree: The number of edges incident to a vertex (for undirected graphs).
- Weighted Graph: A graph where each edge has an associated weight or cost.
- Out-Degree: The number of outgoing edges from a vertex in a directed graph.
- In-Degree: The number of incoming edges to a vertex in a directed graph.

____

1. **Path**:  in a graph is a sequence of vertices such that each consecutive pair of vertices is connected by an edge. A path does not necessarily need to be a simple path, meaning that it can have repeated vertices or edges.

```
	A
   / \
  B   C
 /     \
D       E
```
A path from A to E could be A → C → E.

2. **Cycle**: is a path in which the first vertex is the same as the last vertex and no other vertex repeats. A graph that contains a cycle is called a cyclic graph; otherwise, it’s an acyclic graph.

```
	A
   / \
  B   C
 /     \
 D --- E
```

The cycle is D → E → C → A → B → D.

3. **Loop**: (or self-loop) is an edge that connects a vertex to itself. The vertex is both the start and the end point of the edge. where the edge connects A → A

4. **Degree**: of a vertex is the number of edges incident to it.
	- In-Degree: The number of incoming edges to a vertex (in directed graphs).
	- Out-Degree: The number of outgoing edges from a vertex (in directed graphs).
    - In an undirected graph, the degree is the number of edges connected to the vertex.

```
	A
   / \
  B   C
 /     \
D       E
```
- The degree of A is 2 (edges to B and C).
- The degree of B is 2 (edges to A and D).
- The degree of C is 2 (edges to A and E).

5. **Weighted Graph**: is a graph where each edge has a weight (or cost) associated with it. The weight typically represents some quantity such as distance, cost, or time, depending on the context of the graph.

```
	A
   / \
 5/   \3
  B---C
	 2
```

The weight of the edge from A to B is 5, the weight from A to C is 3, and the weight from C to B is 2.

6. **Out-Degree**: of a vertex in a directed graph is the number of edges leaving the vertex. This only applies to directed graphs, where edges have a direction.
```
   A → B → C
		↑
		D
```

- The out-degree of A is 1 (since it has one outgoing edge to B).
- The out-degree of B is 2 (since it has outgoing edges to C and D).
- The out-degree of C is 0 (no outgoing edges).

7. **In-Degree**: of a vertex in a directed graph is the number of edges entering the vertex. This only applies to directed graphs, where edges have a direction.
```
   A → B → C
		↑
		D
```

- The in-degree of A is 0 (no incoming edges).
- The in-degree of B is 1 (one incoming edge from A).
- The in-degree of C is 1 (one incoming edge from B).
- The in-degree of D is 1 (one incoming edge from B).


____
##### Discuss the steps to add and delete a vertex in the graph with suitable examples.





____

#### Graph traversals: Breadth-First- Search (BFS) Traversal, Depth-First- Search (DFS) Traversal, 

* Write an algorithm for Breadth-first Traversal.
* Discuss Breadth-first traversal of a graph with suitable example and algorithm

**Answer :**

Breadth-First Search (BFS) is an algorithm for traversing or searching tree or graph data structures. BFS starts at the root node (or any arbitrary node in the case of a graph) and explores all the neighboring nodes at the present depth level before moving on to nodes at the next depth level. BFS uses a **queue** to keep track of the nodes to be explored.

BFS is an essential graph traversal algorithm that explores nodes layer by layer, ensuring that all nodes at the current depth level are processed before moving on to the next level. 

It is widely used for applications like finding the shortest path in unweighted graphs, web crawling, and social network analysis.


1. Start with the starting node: We enqueue the starting node and mark it as visited.
2. Process each node: We dequeue a node, print or store it, and then enqueue all of its unvisited neighbors.
3. Repeat until all nodes are visited: The algorithm processes nodes level by level. First, it processes all nodes at the current level, then moves on to the next level, and so on.

____

Steps for BFS:
1. Initialization:
    - Mark all vertices as not visited.
    - Create an empty queue.
    - Enqueue the starting vertex (root node) into the queue.
    - Mark the starting vertex as visited.

2. BFS:    
    - While the queue is not empty:
        - Dequeue a vertex from the queue.
        - Visit and process that vertex (usually print or store the result).
        - Enqueue all unvisited adjacent vertices of the dequeued vertex.
        - Mark those adjacent vertices as visited.

___

Let's consider the following graph represented using an adjacency list:

```
    A
   / \
  B   C
 / \   \
D   E   F
```

Adjacency List representation:
```
A: [B, C]
B: [A, D, E]
C: [A, F]
D: [B]
E: [B]
F: [C]
```


BFS Graph Traversal (Step-by-step Example)
1. Start at A → Visit A → Enqueue B, C.
2. Move to B → Visit B → Enqueue D, E.
3. Move to C → Visit C → Enqueue F.
4. Move to D → Visit D (no new nodes to enqueue).
5. Move to E → Visit E (no new nodes to enqueue).
6. Move to F → Visit F (no new nodes to enqueue).
7. All nodes are visited, so the traversal ends.

BFS Output (Order of Visit):
```
A B C D E F
```

____

BFS Traversal Process (Starting from A):

1. Start at node A:
    - Mark A as visited and enqueue it.
    - Queue: `[A]`

2. Dequeue A and process it:    
    - A's neighbors are B and C.
    - Mark B and C as visited and enqueue them.
    - Queue: `[B, C]`

3. Dequeue B and process it:    
    - B's neighbors are A, D, and E.
    - A is already visited, so enqueue D and E.
    - Queue: `[C, D, E]`

4. Dequeue C and process it:    
    - C's neighbors are A and F.
    - A is already visited, so enqueue F.
    - Queue: `[D, E, F]`

5. Dequeue D and process it:    
    - D's neighbor is B, which is already visited.
    - Queue: `[E, F]`

6. Dequeue E and process it:    
    - E's neighbor is B, which is already visited.
    - Queue: `[F]`

7. Dequeue F and process it:    
    - F's neighbor is C, which is already visited.
    - Queue: `[]` (empty, traversal complete)


### **BFS Pseudocode**

```python
BFS(graph, start):
    # Create a queue to store the nodes
    queue = []
    
    # Create a set to track visited nodes
    visited = set()
    
    # Enqueue the start node and mark it as visited
    queue.append(start)
    visited.add(start)
    
    while queue:
        # Dequeue a vertex from the queue
        node = queue.pop(0)
        
        # Process the current node (here, we print it)
        print(node, end=" ")
        
        # Enqueue all unvisited adjacent nodes of the current node
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```


____

### Depth First Traversal 

* Write the algorithm for depth first traversal of a graph. Explain the process of traversal with suitable graph data structure.
* Discuss Depth-first traversal of a Graph with an example.
* Explain Depth-first traversal of a graph with the help of an algorithm. Give the Depth-first traversal for the following graph starting from vertex 12.
```
5      12
	   |
	23
   |
25		3

5 connects 12 and 25
3 connects 12 and 25
23 connects 12 and 25
```

* Explain Depth-first traversal of a graph with the help of an algorithm. Give the Depth-first traversal for the following graph starting from vertex A.
```
Graph of hexagonal and sqaure shape
```

**Answer :**

The Depth First Search (DFS) is an algorithm for traversing or searching tree or graph data structures. Starting from a root node, the algorithm explores as far as possible along each branch before backtracking  and exploring alternate paths. It uses a stack (or recursion) to remember the nodes to visit next.

DFS is a useful algorithm for exploring all nodes of a graph, often used in scenarios like searching, topological sorting, and pathfinding.


General algorithm for Depth First Traversal of a graph:
1. Initialization:
    - Mark all vertices as not visited.
    - Create a stack (or use recursion).
2. DFS (starting from a vertex):
    - Push the starting vertex onto the stack.
    - While the stack is not empty:
        - Pop the top vertex from the stack.
        - If the vertex has not been visited, mark it as visited and print it (or store the result).
        - Push all its unvisited adjacent vertices onto the stack.

Process of Traversal with a simple undirected graph:

```
    A
   / \
  B   C
 / \
D   E
```

The adjacency list representation of the graph is:

```
A: [B, C]
B: [A, D, E]
C: [A]
D: [B]
E: [B]
```

Let’s say we are performing a DFS traversal starting at **A** on the graph above:
1. Start at A → Visit A → Push B, C.
2. Move to B → Visit B → Push D, E.
3. Move to D → Visit D (No neighbors left).
4. Backtrack to B → Move to E → Visit E (No neighbors left).
5. Backtrack to A → Move to C → Visit C (No neighbors left).
6. All nodes are visited, so the traversal ends.

_____

1. Starting at A:
    - Visit A and mark it as visited.
    - Push A’s neighbors (B and C) onto the stack.

2. Move to B (since it was pushed first):    
    - Visit B and mark it as visited.
    - Push B’s neighbors (A, D, E) onto the stack. 
    - A is already visited, so only push D and E.

3. Move to D (since it was pushed after B’s neighbors):
    - Visit D and mark it as visited.
    - D has no unvisited neighbors, so we backtrack.

4. Move to E
    - Visit E and mark it as visited.
    - E has no unvisited neighbors, so we backtrack.

5. Backtrack to A and move to C:    
    - Visit C and mark it as visited.
    - C has no unvisited neighbors.

6. DFS completes as all nodes are visited.    

- Output: `A B D E C`



```python
DFS(graph, start):
    # Initialize visited set
    visited = set()
    
    # Helper function for DFS using stack
    def dfs_util(v):
        # Mark the current node as visited
        visited.add(v)
        print(v, end=" ")  # Or store the result
        
        # Recur for all the vertices adjacent to this vertex
        for neighbor in graph[v]:
            if neighbor not in visited:
                dfs_util(neighbor)
                
    # Call DFS from the starting vertex
    dfs_util(start)
```

Alternatively, DFS can be implemented iteratively using a stack:
```python
DFS(graph, start):
    # Initialize visited set
    visited = set()
    
    # Stack for DFS
    stack = [start]
    
    while stack:
        # Pop the top element from the stack
        node = stack.pop()
        
        # If the node has not been visited, mark it as visited
        if node not in visited:
            visited.add(node)
            print(node, end=" ")  # Or store the result
        
        # Push all unvisited neighbors of the node onto the stack
        for neighbor in reversed(graph[node]):  # Reverse to visit in correct order
            if neighbor not in visited:
                stack.append(neighbor)
```

____

#### Storage structures (Adjacency Matrix and Adjacency List), graph algorithms.

* Explain how Graph can be represented using a Adjacency Matrix and Adjacency List with suitable example.
* Describe the graph storage structures adjacency matrix and adjacency list with example. Give the comparisons between them.
* Differentiate the following graph storage structures using suitable example. i) Adjacency Matrix ii) Adjacency List.
* Explain the two common structures used to store graphs with examples.
* Describe the two types of graph storage structures with suitable examples.
* Explain different graph storage structure with example.

**Answer :**

A graph can be represented using various data structures, the two most common being the Adjacency Matrix and the Adjacency List. 

Adjacency Matrix Representation : is a 2D array of size n×n, where n is the number of nodes in the graph. The matrix entry `matrix[i][j]` is:
- **1** (or the weight of the edge) if there is an edge from node `i` to node `j`.
- **0** if there is no edge from node `i` to node `j`.

Consider a simple undirected graph with 4 nodes:
```
    1 -- 2
    |    |
    3 -- 4
```

The adjacency matrix for this graph would look like this:
```
    1   2   3   4
1   0   1   1   0
2   1   0   0   1
3   1   0   0   1
4   0   1   1   0
```


Adjacency List Representation : is an array of lists. Each index represents a node, and the list at each index contains the nodes that are connected to that node.

For the same graph, the adjacency list would look like this:
```
1: [2, 3]
2: [1, 4]
3: [1, 4]
4: [2, 3]
```


Adjacency Matrix :
- Space Complexity: `O(n^2)` where n is the number of nodes (this can be inefficient for sparse graphs). Suitable for dense graphs where most of the possible edges exist.
- Advantages: Fast edge lookup: O(1). Simple to implement.
- Disadvantages: Inefficient space usage for sparse graphs. Difficult to iterate through all edges.

Adjacency List :
- Space Complexity : O(n + e), where n is the number of nodes and e is the number of edges (more space-efficient for sparse graphs). Suitable for sparse graphs where few edges exist relative to the number of nodes.
- Advantages: More space-efficient for sparse graphs. Efficient traversal of all edges.
- Disadvantages: Edge lookup is slower than the adjacency matrix: O(n)O(n) in the worst case.


____

Adjacency Matrix : A graph with 5 nodes, where most of the nodes are connected, such as a fully connected network.

```
    1   2   3   4   5
1   0   1   1   1   1
2   1   0   1   1   1
3   1   1   0   1   1
4   1   1   1   0   1
5   1   1   1   1   0
```

Adjacency List : A graph with 5 nodes, where only a few nodes are connected:
```
1: [2, 3]
2: [1, 4]
3: [1, 5]
4: [2]
5: [3]
```

____

For a graph with 3 nodes:
```
   1 --- 2
    \   /
     \ /
      3
```

Adjacency Matrix:
```
    1   2   3
1   0   1   1
2   1   0   1
3   1   1   0
```

Adjacency List :
```
1: [2, 3]
2: [1, 3]
3: [1, 2]
```

___

