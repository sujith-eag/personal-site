---
title: "OS - Unit-3 - Previous Questions"
description: ""
summary: ""
date: 2025-01-12T21:20:56+05:30
lastmod: 2025-01-12T21:20:56+05:30
draft: false
weight: 1983
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



### Deadlock Basics & Conditions

- What is a deadlock? What are the four necessary conditions for a deadlock to occur?
- Define a deadlock. Describe the necessary and sufficient conditions for a deadlock to occur in a system.
- What are the necessary conditions to form a deadlock? Explain.
- What are the necessary conditions to form a deadlock? Differentiate between deadlock prevention and deadlock avoidance.

### Deadlock Prevention, Avoidance, Detection and Handling

- What are the different ways a deadlock can be handled? How can deadlocks be prevented?
- Explain the deadlock prevention algorithms.
- What are the different ways a deadlock can be handled? Discuss different ways of recovering from deadlocks.
- What do you mean by deadlock? How do you recover the system from deadlock?
- What is deadlock detection and recovery? Discuss different mechanisms to achieve the same.
- Write the deadlock detection algorithms.
- Propose methods to recover the system from a deadlock situation.
- Discuss different ways of recovering from deadlocks.

### Resource Allocation Graph (RAG) and System State

- Discuss the Resource Allocation Graph.
- Demonstrate how to identify deadlocks using the Resource Allocation Graph.
- Narrate the different components of the Resource Allocation Graph. How do you analyze RAG with respect to safe state and unsafe state?
- Deadlock exists if a cycle exists. Yes or No? Justify your answer with a suitable example.
- Present the definitions for the following terms:  
  i) Safe state  
  ii) Aborted state  
  iii) Claim edge  
  iv) Cycle state

### System Models and Analysis

- Elaborate the facts with the system model to acquire required resources.
- Let a system have P1, P2, P3, P4 processes and r1 and r2 resources. Both resources have 2 instances. The set E is given by:  
`E = {<P1 -> r1>, <r1 -> P2>, <r1 -> P3>, <P3 -> r2>, <r2 -> P4>, <r2 -> P1>}`
  Does the system lead to a deadlock?
- In a real computer system, neither the resources available nor the demands of processes for resources remain consistent over long periods. If deadlock is controlled by the Banker’s algorithm, analyze whether the following changes can be made safely, and under what circumstances:  
  i) Increase Available (new resources added)  
  ii) Decrease Available (resource permanently removed)  
  iii) Increase Max for one process (the process may need more resources)  
  iv) Decrease Max for one process (the process needs fewer resources)  
  v) Increase the number of processes  
  vi) Decrease the number of processes

### Classic Problems Involving Deadlocks

- Explain the Readers-Writers Problem with code snippets and explain how deadlock is avoided.
- Explain the Dining Philosophers Problem with code snippets and explain how the deadlock situation is avoided.

____

### Problems on Page Allocation

Consider a system with five processes P_0 through P_4 and three resource types ( A ), ( B ), and ( C ). Resource type ( A ) has 10 instances, ( B ) has 5 instances, and  C  has 8 instances. Suppose at time ( t_0 ), the following snapshot of the system has been taken:

| Processes | Allocation A | Allocation B | Allocation C | Max A | Max B | Max C | Available A | Available B | Available C |
| --------- | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----------- | ----------- | ----------- |
| P0        | 0            | 1            | 2            | 7     | 5     | 3     | 3           | 3           | 2           |
| P1        | 2            | 0            | 0            | 3     | 2     | 2     | -           | -           | -           |
| P2        | 3            | 0            | 1            | 9     | 0     | 2     | -           | -           | -           |
| P3        | 2            | 1            | 1            | 2     | 2     | 2     | -           | -           | -           |
| P4        | 0            | 0            | 2            | 4     | 3     | 3     | -           | -           | -           |

Answer the following questions using Banker’s Algorithm:
i) What will be the content of the Need matrix?
ii) If a request from process \( P_2 \) arrives for (2, 0, 1), can it be granted?

____

Considering a system with five processes P0 through P4 and three resources types A, B, C. Resource type A has 10 instances, B has 5 instances and type C has 9 instances. Suppose at time t0 following snapshot of the system has been taken:

| Processes | Allocation A | Allocation B | Allocation C | Max A | Max B | Max C | Available A | Available B | Available C |
| --------- | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----------- | ----------- | ----------- |
| P0        | 0            | 1            | 2            | 7     | 5     | 3     | 3           | 3           | 2           |
| P1        | 2            | 0            | 0            | 3     | 2     | 2     | -           | -           | -           |
| P2        | 3            | 0            | 2            | 9     | 0     | 2     | -           | -           | -           |
| P3        | 2            | 1            | 1            | 2     | 2     | 2     | -           | -           | -           |
| P4        | 0            | 0            | 2            | 4     | 3     | 3     | -           | -           | -           |

Answer the following questions using Banker’s algorithm:
i) What will be the content of the Need matrix?
ii) If a request from process P1 arrives for (1 0 2), can it be granted?

___

Consider the following snapshot of a system:

| Processes | Maximum R0 | Maximum R1 | Maximum R2 | Allocation R0 | Allocation R1 | Allocation R2 | Available R0 | Available R1 | Available R2 |
| --------- | ---------- | ---------- | ---------- | ------------- | ------------- | ------------- | ------------ | ------------ | ------------ |
| P0        | 4          | 1          | 2          | 1             | 0             | 2             | 2            | 2            | 0            |
| P1        | 1          | 5          | 1          | 0             | 3             | 1             | -            | -            | -            |
| P2        | 1          | 2          | 3          | 1             | 0             | 2             | -            | -            | -            |

Answer the following questions using Banker's Algorithm:
i) Is the system in a safe state?
ii) Will the system be able to satisfy a request by process P0 for one unit of resource type R1?
iii) Will the system be able to satisfy a request by process P1 for one unit of resource type R0?

___

Consider the following system state, there are three resources and three processes

| Processes | Maximum R1 | Maximum R2 | Maximum R3 | Allocation R1 | Allocation R2 | Allocation R3 | Available R1 | Available R2 | Available R3 |
| --------- | ---------- | ---------- | ---------- | ------------- | ------------- | ------------- | ------------ | ------------ | ------------ |
| P1        | 2          | 1          | 2          | 1             | 0             | 1             | 2            | 1            | 2            |
| P2        | 3          | 2          | 4          | 0             | 0             | 1             | -            | -            | -            |
| P3        | 4          | 2          | 1          | 1             | 1             | 1             | -            | -            | -            |

Answer following questions using Bankers algorithm.
i) Is the system in a safe state?
ii) Consider each of the following requests and say if it can be
granted. i. P3 requests 1 0 0 ii. P1 requests 0 1 0
iii) P2 requests 2 0 0 iv. P2 requests 1 0 1.

___

Consider the following snapshot of a system.

| Processes | Allocation A | Allocation B | Allocation C | Max A | Max B | Max C | Available A | Available B | Available C |
| --------- | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----------- | ----------- | ----------- |
| P0        | 0            | 1            | 0            | 7     | 5     | 3     | 3           | 3           | 2           |
| P1        | 2            | 0            | 0            | 3     | 2     | 2     | -           | -           | -           |
| P2        | 3            | 0            | 2            | 9     | 0     | 2     | -           | -           | -           |
| P3        | 2            | 1            | 1            | 2     | 2     | 2     | -           | -           | -           |
| P4        | 0            | 0            | 2            | 4     | 3     | 3     | -           | -           | -           |


Consider the a system with 5 processes P0 through P4 and 3 resource types A,B,C. Resource type A has 10 instances, B has 5 instances and C has 7 instances.
Answer the following questions using the Banker’s algorithm.
i) Find the content of the Need matrix?
ii) Judge the system is in Safe state?

___

Assume that there are 5 processes, P0 through P4, and 4 types of resources. At time T0, the system state is as follows:

| Processes | Allocation A | Allocation B | Allocation C | Max A | Max B | Max C | Available A | Available B | Available C |
| --------- | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----------- | ----------- | ----------- |
| P0        | 5            | 2            | 3            | 3     | 1     | 2     | 1           | 2           | 2           |
| P1        | 4            | 6            | 2            | 3     | 4     | 1     | -           | -           | -           |
| P2        | 2            | 1            | 7            | 0     | 0     | 5     | -           | -           | -           |
| P3        | 6            | 3            | 1            | 5     | 1     | 0     | -           | -           | -           |
| P4        | 3            | 5            | 1            | 1     | 4     | 0     | -           | -           | -           |

Answer the following questions:
i) Construct the need matrix.
ii) Is the system in a safe state? If yes, what is the safe sequence?
iii) If a request for process p2 arrives for (1, 2, 0) can it be granted immediately.

____

Consider the following Snapshot of the system:

| Processes | Allocation A | Allocation B | Allocation C | Allocation D | Max A | Max B | Max C | Max D | Available A | Available B | Available C | Available D |
| --------- | ------------ | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----- | ----------- | ----------- | ----------- | ----------- |
| P0        | 0            | 1            | 2            | 0            | 1     | 5     | 2     | 0     | 1           | 2           | 1           | 5           |
| P1        | 1            | 0            | 0            | 1            | 7     | 5     | 3     | 0     | -           | -           | -           | -           |
| P2        | 1            | 3            | 5            | 2            | 3     | 4     | 2     | 3     | -           | -           | -           | -           |
| P3        | 0            | 1            | 4            | 0            | 6     | 5     | 6     | 5     | -           | -           | -           | -           |
| P4        | 0            | 1            | 4            | 6            | 5     | 6     | 5     | 6     | -           | -           | -           | -           |

Answer following questions using Bankers algorithm.
i) Is the system in a safe state?
ii) Can a request for (0, 4, 2, 0) by P1 be granted immediately?   Give reason.

___

For the following snapshot find the safe sequence using Banker’s algorithm. The number of resource units are R1, R2, R3 which are 7, 7, 10 respectively.

| Process | Allocated A | Allocated B | Allocated C | Max A | Max B | Max C |
| ------- | ----------- | ----------- | ----------- | ----- | ----- | ----- |
| P1      | 2           | 2           | 3           | 3     | 6     | 8     |
| P2      | 2           | 0           | 3           | 4     | 3     | 3     |
| P3      | 1           | 2           | 4           | 3     | 4     | 4     |

___

Consider the Snapshot of the system:

| Process | Allocation A | Allocation B | Allocation C | Allocation D | Max A | Max B | Max C | Max D | Available A | Available B | Available C | Available D |
| ------- | ------------ | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----- | ----------- | ----------- | ----------- | ----------- |
| P0      | 0            | 0            | 1            | 2            | 0     | 0     | 1     | 2     | 1           | 5           | 2           | 0           |
| P1      | 1            | 0            | 0            | 0            | 1     | 7     | 5     | 0     | -           | -           | -           | -           |
| P2      | 1            | 3            | 5            | 4            | 2     | 3     | 5     | 6     | -           | -           | -           | -           |
| P3      | 0            | 6            | 3            | 2            | 0     | 6     | 5     | 2     | -           | -           | -           | -           |
| P4      | 0            | 0            | 1            | 4            | 0     | 6     | 5     | 6     | -           | -           | -           | -           |


Answer the following questions using the banker’s algorithm:
(i)What is the content of the matrix Need?
(ii)Is the system in a safe state?
If a request from a process P1 arrives for (0, 4, 2, 0), can the request be granted immediately?

___


