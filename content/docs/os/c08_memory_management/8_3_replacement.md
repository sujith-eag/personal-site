---
title: "OS 8.02 - Virtual Memory, Page Replacement"
description: ""
summary: ""
date: 2025-01-12T21:27:49+05:30
lastmod: 2025-01-12T21:27:49+05:30
draft: false
weight: 2047
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


Virtual memory is a technique that allows the execution of processes that
are not completely in memory. One major advantage of this scheme is that programs can be larger than physical memory. 

Virtual memory abstracts main memory into an extremely large, uniform array of storage, separating logical memory as viewed by the programmer from physical memory.  

This separation allows an extremely large virtual memory to be provided for programmers when only a smaller physical memory is available, frees programmers from the concerns of memory-storage limitations. 

Virtual memory also allows processes to share files and libraries, and to implement shared memory. In addition, it provides an efficient mechanism for process creation.

Virtual memory allows one process to create a region of memory that it can
share with another process. Processes sharing this region consider it part
of their virtual address space, yet the actual physical pages of memory are
shared,

___

The virtual address space of a process refers to the logical (or virtual) view
of how a process is stored in memory. this view is that a process begins at a certain logical address—say, address 0—and exists in contiguous memory.

physical memory is organized in page frames and that the physical page
frames assigned to a process may not be contiguous

____

The ability to execute a program that is only partially in memory would
confer many benefits:
• A program would no longer be constrained by the amount of physical
memory that is available. Users would be able to write programs for an
extremely large virtual address space, simplifying the programming task.
• Because each program could take less physical memory, more programs
could be run at the same time, with a corresponding increase in CPU utilization and throughput but with no increase in response time or turnaround
time.
• Less I/O would be needed to load or swap portions of programs into
memory, so each program would run faster.

____


### Demand Paging

Usual way of getting an executable program from to secondary memory, we may not initially need the entire program in memory to run the program,.

A Strategy is to load pages only as they are needed. This technique is known as demand paging and is commonly used in virtual memory systems.

With demand-paged virtual memory, pages are loaded only when they are demanded during program execution. Pages that are never accessed are thus never loaded into physical memory. A demand-paging system is similar to a paging system with swapping.


while a process is executing, some pages will be in memory, and some will be in secondary storage. Thus, we need some form of hardware support to distinguish between the two. The valid–invalid bit scheme can be used for this purpose.

when the bit is set to “valid,” the associated page is both legal and in memory. If the bit is set to “invalid,” the page either is not valid (that
is, not in the logical address space of the process) or is valid but is currently in secondary storage.

{{< figure  src="images/os/8_15_ValidBits-min.jpg"  alt="."  caption="." >}}



The page-table entry for a page that is brought into memory is set as usual, but the page-table entry for a page that is not currently in memory is simply marked invalid.

{{< figure  src="images/os/9_05_PageTable-min.jpg"  alt="."  caption="." >}}

Access to a page marked invalid causes a page fault. 
The paging hardware, in translating the address through the page table, will notice that the invalid bit is set, causing a trap to the operating system. This trap is the result of the operating system’s failure to bring the desired page into memory.



The procedure for handling this page fault is: 
1. We check an internal table (usually kept with the process control block) for this process to determine whether the reference was a valid or an invalid memory access.
2. If the reference was invalid, we terminate the process. If it was valid but we have not yet brought in that page, we now page it in.
3. We find a free frame (by taking one from the free-frame list).
4. We schedule a secondary storage operation to read the desired page into the newly allocated frame.
5. When the storage read is complete, we modify the internal table kept with the process and the page table to indicate that the page is now in memory.
6. We restart the instruction that was interrupted by the trap. The process can now access the page as though it had always been in memory.

{{< figure  src="images/os/9_06_PageFaultSteps-min.jpg"  alt="."  caption="." >}}

The hardware to support demand paging is the same as the hardware for
paging and swapping:

• Page table. This table has the ability to mark an entry invalid through a
valid –invalid bit or a special value of protection bits.
• Secondary memory. This memory holds those pages that are not present
in main memory. The secondary memory is usually a high-speed disk or
NVM device. It is known as the swap device, and the section of storage
used for this purpose is known as swap space.

___


### Page Replacement

Deciding how much memory to allocate to I/O and how much to program pages is a significant challenge.


When Memory is over allocated. While a process is executing, a page fault occurs. The operating system determines where the desired page is residing on secondary storage but then finds that there are no free frames on the free-frame list; all memory is in use.

Most operating systems now combine swapping pages with page replacement.


modify the
page-fault service routine to include page replacement:
1. Find the location of the desired page on secondary storage.
2. Find a free frame:
a. If there is a free frame, use it.
b. If there is no free frame, use a page-replacement algorithm to select a victim frame.
c. Write the victim frame to secondary storage (if necessary); change
the page and frame tables accordingly.
3. Read the desired page into the newly freed frame; change the page and frame tables.
4. Continue the process from where the page fault occurred.



if no frames are free, two page transfers (one for the page-out and one for the page-in) are required. This situation effectively doubles the page-fault service time and increases the effective access time accordingly.

Page replacement is basic to demand paging. It completes the separation
between logical memory and physical memory.



We must solve two major problems to implement demand paging: we must
develop a frame-allocation algorithm and a page-replacement algorithm. That is, if we have multiple processes in memory, we must decide how many frames to allocate to each process; and when page replacement is required, we must select the frames that are to be replaced


#### FIFO Page Replacement

The simplest page-replacement algorithm is a first-in, first-out (FIFO) algorithm. A FIFO replacement algorithm associates with each page the time when that page was brought into memory. When a page must be replaced, the oldest page is chosen.

{{< figure  src="images/os/9_12_FIFO_PageReplacement-min.jpg"  alt="."  caption="." >}}

#### Optimal Page Replacement

Replace the page that will not be used for the longest period of time. Use of this page-replacement algorithm guarantees the lowest possible page-
fault rate for a fixed number of frames.

{{< figure  src="images/os/9_14_OptimalPageReplacement-min.jpg"  alt="."  caption="." >}}

Unfortunately, the optimal page-replacement algorithm is difficult to implement, because it requires future knowledge of the reference string.
As a result, the optimal algorithm is used mainly for comparison
studies.


#### LRU Page Replacement

FIFO algorithm uses the time when a page was brought into memory, whereas the OPT algorithm uses the time when a page is to be used. 

If we use the recent past as an approximation of the near future, then we can replace the page that has - not been used for the longest period of time. This approach is the least recently used (LRU) algorithm.

When a page must be replaced, LRU chooses the page that has not been used for the longest period of time.
This strategy as the optimal page-replacement algorithm looking backward in time, rather than forward.

{{< figure  src="images/os/9_15_LRU_PageReplacement-min.jpg"  alt="."  caption="." >}}

The LRU policy is often used as a page-replacement algorithm and is considered to be good.

____

## Thrashing

if a process does not have “enough” frames—that is, it does not have the minimum number of frames it needs to support pages in the working set. The process will quickly page-fault. At this point, it must replace some page. However, since all its pages are in active use, it must replace a page that will be needed again right away. Consequently, it quickly faults again, and again, and again, replacing pages that it must bring back in immediately.

This high paging activity is called thrashing. A process is thrashing if it
is spending more time paging than executing. As you might expect, thrashing results in severe performance problems.

____

## Unit Summary

Virtual memory abstracts physical memory into an extremely large uni-
form array of storage.
• The benefits of virtual memory include the following: (1) a program can be
larger than physical memory, (2) a program does not need to be entirely in
memory, (3) processes can share memory, and (4) processes can be created
more efficiently.
• Demand paging is a technique whereby pages are loaded only when they
are demanded during program execution. Pages that are never demanded
are thus never loaded into memory.
• A page fault occurs when a page that is currently not in memory is
accessed. The page must be brought from the backing store into an avail-
able page frame in memory.

• When available memory runs low, a page-replacement algorithm
selects an existing page in memory to replace with a new page. Page-
replacement algorithms include FIFO, optimal, and LRU. Pure LRU
algorithms are impractical to implement, and most systems instead use
LRU-approximation algorithms.
• Global page-replacement algorithms select a page from any process in the
system for replacement, while local page-replacement algorithms select a
page from the faulting process.


____


