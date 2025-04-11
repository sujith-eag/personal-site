---
title: "OS - Unit-4 - Previous Questions"
description: ""
summary: ""
date: 2025-01-12T21:20:56+05:30
lastmod: 2025-01-12T21:20:56+05:30
draft: false
weight: 1986
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### Memory Management Concepts

#### Segmentation

- What is Segmentation? Illustrate it with a neat sketch.
- With a neat diagram, explain the concept of segmentation. What are the advantages of segmentation?
- Exemplify the process of paging and segmentation of memory.
- Paging vs Segmentation: Explain with examples and differences.

#### Paging

- Explain paging and its hardware with a neat diagram. What are the advantages of paging?
- With a neat diagram of paging hardware, explain the concept of paging. How does paging differ from segmentation? Explain with an example.
- Describe paging with the hardware diagram.
- With a neat diagram, explain paging hardware with TLB.
- With a neat diagram and example, demonstrate the working procedure of paging hardware with TLB.
- Explain with the help of a neat diagram how TLB can be used to improve Effective Access Time.

---

### Page Faults and Handling

- Under what circumstances do page faults occur? Describe the actions taken by the OS when page faults occur.
- With a neat diagram, describe the steps in handling a page fault.
- Describe the steps in handling a page fault with a neat diagram.

---

#### Fragmentation

- Distinguish between internal fragmentation and external fragmentation. How do you overcome the problem of both?
- Write short notes on the following: Fragmentation.

#### Allocation Strategies

- Distinguish between: First fit and Best fit algorithms.
- Discuss first-fit, best-fit, and worst-fit strategies of dynamic memory allocation.
- Explain the strategies for selecting the free hole.
- Give five memory partitions of 100KB, 500KB, 200KB, 300KB, and 600KB (in order). How would each of the first-fit, best-fit, and worst-fit algorithms place processes of 212KB, 417KB, 112KB, and 426KB (in order)? Which algorithm uses the memory efficiently?

---

### Addressing and Address Space

- Distinguish between: Logical vs Physical address space.
- Illustrate the facts and concepts for the following terms: Address Binding.
- What do you mean by memory protection? Elaborate on the facts of memory protection with proper justifications.
- Calculate the maximum number of pages needed if a system supports a 16-bit address line and 1KB page size.

---

### Swapping and Memory Techniques

- Write short notes on the following: Swapping process in memory.
- Illustrate the facts and concepts for the following terms: Swapping.
- Illustrate how swap space management is implemented.
- Write a note on thrashing.
- Illustrate the facts and concepts for the following terms: Dynamic Loading.

---

Page Table Structures
- Explain briefly the structures of the following Page tables:  i) Hierarchical page table  ii) Inverted page table

Protection and Access Control
- Define Access Matrix for protection and how it is implemented.

---

1. A process references 5 pages (A, B, C, D, E) in the following order: A, B, C, D, A, E, B, C, E, D. Assuming the replacement algorithms are FIFO, LRU, and Optimal, find out the number of page faults during the sequence of references, starting with an empty main memory with 3 frames.

2. Illustrate any two page-replacement algorithms for the following reference string: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5. compare the number of page faults for algorithms algorithms using three frames.

3. Given the page reference string: 1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 1, 2, 3, 6, and 3 frames, compare the number of page faults for the following page replacement algorithms: LRU, FIFO, Optimal page replacement algorithm.

4. A small computer has 4 page frames. A process makes the following list of page references: 1, 2, 3, 4, 0, 3, 2, 1, 5, 2, 3, 1, 2, 5, 0. How many page faults occur using FIFO, LRU, and Optimal page replacement algorithms?

5. Consider the following page reference string: 1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 3, 6. Find out the number of page faults, assuming 3 frames, using: FIFO, LRU, Optimal page replacement algorithm.

6. Consider the following page reference string: 1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 1, 2, 3, 6. How many page faults would occur in the case of:  FIFO, LRU, Optimal page replacement algorithms assuming three and four frames?

7. A computer has 4 page frames. A process makes the following list of page references: 1, 2, 3, 4, 6, 3, 2, 1, 5, 2, 3, 1, 2, 5, 6. How many page faults occur using: FIFO,  LRU, Optimal page replacement algorithms?  Consider that initially 3 frames are filled for FIFO, 2 frames are filled for LRU, and 1 frame is filled for Optimal page replacement.

8. Consider the reference string 7, 2, 3, 4, 3, 2, 1, 4, 5, 2, 3, 1, 8, 7, 3, 2, 4, 1, 1, 2 with 3 memory frames. Determine the page faults using: FIFO, LRU, Optimal page replacement algorithm. Consider that initially 3 frames are filled.

9. Consider the reference string 1, 2, 3, 4, 2, 2, 5, 3, 2, 1, 6, 3, 4, 5, 3, 1 with 3 memory frames. Determine the page faults using: FIFO, LRU, Optimal page replacement algorithm.

10. A small computer has 3 page frames. A process makes the following list of page references: 5, 4, 3, 2, 1, 4, 3, 5, 4, 3, 2, 1, 5. How many page faults occur using FIFO, LRU, and Optimal page replacement algorithms?

11. Consider the reference string 1, 2, 3, 4, 6, 5, 2, 5, 5, 6, 4, 1, 1, 2, 3, 4 with 4 memory frames. Determine the page fault using: FIFO, LRU, Optimal page replacement algorithm.

_____

