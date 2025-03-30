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



1. Exemplify the process of paging and segmentation of memory.
2. With a neat diagram, explain the concept of segmentation. What are the advantages of segmentation?
3. What is Segmentation? Illustrate it with a neat sketch.


4. With a neat diagram of paging hardware, explain the concept of paging. How does paging differ from segmentation? Explain with an example.
5. Explain paging and its hardware with a neat diagram. What are the advantages of paging?
6. Describe paging with the hardware diagram.
7. With a neat diagram, explain paging hardware with TLB.
8. With a neat diagram and example, demonstrate the working procedure of paging hardware with TLB.
9. Explain with the help of a neat diagram how TLB can be used to improve Effective Access Time.


10. Under what circumstances do page faults occur? Describe the actions taken by the OS when page faults occur.
11. With a neat diagram, describe the steps in handling a page fault.
12. Describe the steps in handling a page fault with a neat diagram.



13. Distinguish between: i) Logical vs physical address space  ii) Paging vs segmentation  iii) First fit and best fit algorithms

14. Discuss first-fit, best-fit, and worst-fit strategies of dynamic memory allocation.

15. Distinguish between internal fragmentation and external fragmentation. How do you overcome the problem of both internal and external fragmentation?

16. Write a note on trashing.

17. Explain briefly the structures of the following Page tables: i) Hierarchical page table ii) Inverted page table

18. Write short notes on the following: i) Swapping process in memory  ii) Fragmentation.

19. Illustrate the facts and concepts for the following terms: i) Dynamic Loading  ii) Address Binding  iii) Swapping.

20. What do you mean by memory protection? Elaborate on the facts of memory protection with proper justifications.

21. Calculate the maximum number of pages needed if a system supports a 16-bit address line and 1KB page size.

22. Define Access Matrix for protection and how it is implemented.

23. Illustrate how swap space management is implemented.

24. Explain the strategies for selecting the free hole.

25. Give five memory partitions of 100KB, 500KB, 200KB, 300KB, and 600KB (in order). How would each of the first-fit, best-fit, and worst-fit algorithms place processes of 212KB, 417KB, 112KB, and 426KB (in order)? Which algorithm uses the memory efficiently?

____



1. Illustrate any two page-replacement algorithms for the following reference string: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5.

2. Given the page reference string: 1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 1, 2, 3, 6, and 3 frames, compare the number of page faults for the following page replacement algorithms: LRU, FIFO, Optimal page replacement algorithm.

3. A process references 5 pages (A, B, C, D, E) in the following order: A, B, C, D, A, E, B, C, E, D. Assuming the replacement algorithms are FIFO, LRU, and Optimal, find out the number of page faults during the sequence of references, starting with an empty main memory with 3 frames.

4. A process references 5 pages (A, B, C, D, E) in the following order: A, B, C, D, A, E, B, C, E, D. Assuming the replacement algorithms are FIFO, LRU, and Optimal, find out the number of page faults during the sequence of references, starting with an empty main memory with 3 frames.

5. A small computer has 4 page frames. A process makes the following list of page references: 1, 2, 3, 4, 0, 3, 2, 1, 5, 2, 3, 1, 2, 5, 0. How many page faults occur using FIFO, LRU, and Optimal page replacement algorithms?

6. Consider the following page reference string: 1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 3, 6. Find out the number of page faults, assuming 3 frames, using: FIFO, LRU, Optimal page replacement algorithm.

7. Consider the following page reference string: 1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 1, 2, 3, 6. How many page faults would occur in the case of:  FIFO, LRU, Optimal page replacement algorithms assuming three and four frames?

8. A computer has 4 page frames. A process makes the following list of page references: 1, 2, 3, 4, 6, 3, 2, 1, 5, 2, 3, 1, 2, 5, 6. How many page faults occur using: FIFO,  LRU, Optimal page replacement algorithms?  Consider that initially 3 frames are filled for FIFO, 2 frames are filled for LRU, and 1 frame is filled for Optimal page replacement.

9. Consider the reference string 7, 2, 3, 4, 3, 2, 1, 4, 5, 2, 3, 1, 8, 7, 3, 2, 4, 1, 1, 2 with 3 memory frames. Determine the page faults using: FIFO, LRU, Optimal page replacement algorithm. Consider that initially 3 frames are filled.

10. Consider the reference string 1, 2, 3, 4, 2, 2, 5, 3, 2, 1, 6, 3, 4, 5, 3, 1 with 3 memory frames. Determine the page faults using: FIFO, LRU, Optimal page replacement algorithm.

11. A small computer has 3 page frames. A process makes the following list of page references: 5, 4, 3, 2, 1, 4, 3, 5, 4, 3, 2, 1, 5. How many page faults occur using FIFO, LRU, and Optimal page replacement algorithms?

12. A small computer has 3 page frames. A process makes the following list of page references: 5, 4, 3, 2, 1, 4, 3, 5, 4, 3, 2, 1, 5. How many page faults occur using FIFO, LRU, and Optimal page replacement algorithms?

13. Consider the reference string 1, 2, 3, 4, 6, 5, 2, 5, 5, 6, 4, 1, 1, 2, 3, 4 with 4 memory frames. Determine the page fault using: FIFO, LRU, Optimal page replacement algorithm.

14. Consider the reference string 1, 2, 3, 4, 6, 5, 2, 5, 5, 6, 4, 1, 1, 2, 3, 4 with 4 memory frames. Determine the page fault using: FIFO, LRU, Optimal page replacement algorithm.


_____

