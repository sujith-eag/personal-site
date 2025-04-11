---
title: "OS - Unit-3 - Q_Answered"
description: ""
summary: ""
date: 2025-01-12T21:20:56+05:30
lastmod: 2025-01-12T21:20:56+05:30
draft: false
weight: 1985
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


##### Define a deadlock. Describe the necessary and sufficient conditions for a deadlock to occur in a system.

* What is a deadlock? Explain the Readers Writers Problem with code snippets and explain how deadlock is avoided in the scenario.

**Answer :**

Deadlock is a situation where a set of processes are blocked because each process is holding a resource and waiting for another resource that is held by another process in the set. This leads to a cycle of dependencies where no process can proceed.

A deadlock occurs when the following four conditions are met simultaneously:

1. Mutual Exclusion: At least one resource must be held in a non-shareable mode.
2. Hold and Wait: A process must be holding at least one resource and waiting to acquire additional resources held by other processes.
3. No Preemption: Resources cannot be preempted (taken away) from processes; they must be released voluntarily.
4. Circular Wait: A set of processes must exist such that each process in the set is waiting for a resource that is held by another process in the set, forming a circular chain of dependencies.

Readers-Writers Problem:
The Readers-Writers Problem is a classic synchronization problem in which a shared resource (such as a database) must be accessed by multiple processes. In this problem, two types of processes are involved:

- Readers: Processes that only read from the resource and do not modify it.
- Writers: Processes that modify the resource.

The challenge is to allow concurrent access to the shared resource by multiple readers, while ensuring that only one writer can access the resource at a time and that no reader can access the resource while a writer is writing.

Code Snippet for the Readers-Writers Problem:

```c

```

How Deadlock is Avoided in the Readers-Writers Problem:

In this solution, deadlock is avoided through proper synchronization mechanisms:
- Semaphores are used to ensure that the writers are blocked when there are active readers, and readers are blocked when a writer is writing. This prevents circular waits (the fourth condition of deadlock).
- The readCount variable ensures that writers are blocked as long as at least one reader is accessing the resource. The first reader blocks writers and the last reader releases the writer lock, preventing a circular wait between readers and writers.
- The mutex is used to protect the critical section where `readCount` is incremented or decremented, ensuring that race conditions do not occur when updating the reader count.

Thus, by carefully managing the resources (through the use of semaphores), the system ensures that deadlock does not occur, even though there are multiple processes interacting with shared resources.


___

##### What are the different ways a deadlock can be handled? How can deadlocks be prevented?

* Explain the deadlock prevention algorithms.
* What is deadlock detection and recovery? Discuss different mechanisms to achieve the same.
* What are the different ways a deadlock can be handled? Discuss different ways of recovering from deadlocks.
* Differentiate between deadlock prevention and deadlock avoidance.

**Answer :**

Deadlocks can be handled in several ways in operating systems. The three primary approaches are deadlock prevention, deadlock avoidance, and deadlock detection and recovery. Let’s go through each approach and how deadlocks can be prevented.

- Deadlock Prevention: Proactively avoids deadlock by eliminating one of the four necessary conditions.
- Deadlock Avoidance: Dynamically allocates resources but ensures the system always stays in a safe state.
- Deadlock Detection and Recovery: Allows deadlock to occur but detects and recovers from it using various algorithms.

#### 1. Deadlock Prevention

Deadlock prevention aims to prevent the occurrence of one or more of the necessary conditions for a deadlock. The four conditions for a deadlock (mutual exclusion, hold and wait, no preemption, and circular wait) must be violated to ensure that deadlock cannot occur. 

- Mutual Exclusion: This condition states that at least one resource must be held in a non-shareable mode. In many cases, mutual exclusion cannot be eliminated for certain resources (e.g., printers, disk drives). However, some resources can be shared, so deadlock can be prevented by ensuring that the resource can be shared among processes (e.g., read-only resources like files).

- Hold and Wait: To prevent this condition, we can require that a process must request all the resources it needs at once. If a process cannot obtain all the resources it needs, it releases the ones it already has and tries again later. This approach avoids a process holding resources while waiting for others.

- No Preemption: To prevent the no preemption condition, a system can be designed so that if a process holding a resource is preempted (interrupted), the resources are taken away from the process and allocated to other processes. This ensures that a process cannot hold onto a resource while waiting for another one.

- Circular Wait: To avoid circular wait, we impose a total order on all resource types. Processes can request resources in a specific order, and if a process requests a resource that it cannot obtain, it releases the resources it holds and retries. This ensures that a cycle in the resource allocation graph cannot form.


#### 2. Deadlock Avoidance

Deadlock avoidance allows the system to allocate resources dynamically but in a way that ensures that deadlock is always avoided. This requires the system to have more information about the resource needs of processes ahead of time. One common approach to deadlock avoidance is the Banker’s Algorithm.

- Banker’s Algorithm: This algorithm checks whether a resource allocation would result in a safe state. It does this by simulating the allocation and determining if there is a sequence of processes that can execute without resulting in deadlock. If the allocation would result in a deadlock, the system denies the request. It is like a "safety check" before allocating resources to ensure no circular wait is possible.

- Safe State vs Unsafe State: A state is said to be safe if there exists at least one sequence of processes that can be executed without causing a deadlock. If no such sequence exists, the state is unsafe, and deadlock could occur.

#### 3. Deadlock Detection and Recovery

In deadlock detection and recovery, the system allows deadlocks to occur but has mechanisms in place to detect them and recover from them when they do occur. This involves:

- Deadlock Detection: The system must periodically check for the presence of deadlocks using algorithms such as the Resource Allocation Graph (RAG) or Wait-for Graph. If a cycle is detected in the graph, a deadlock exists.

- Deadlock Recovery: Once a deadlock is detected, the system must take action to recover. There are several strategies for recovery:
    - Process Termination: One way to recover is to kill one or more processes involved in the deadlock. This can be done by either aborting a process or rolling back the process to some safe state.
    - Resource Preemption: Another way to recover from a deadlock is by preempting resources from the processes involved in the deadlock and reallocating them. The preempted process may be restarted later.

___

##### Discuss the Resource Allocation Graph.

* Narrate the different components of the Resource Allocation Graph. How do you analyze RAG with respect to safe state and unsafe state?
* Demonstrate how to identify deadlocks using the Resource Allocation Graph.
* Demonstrate how to identify deadlocks using the Resource Allocation Graph.
* Deadlock exists if a cycle exists. Yes or No? Justify your answer with a suitable example.

**Answer :**

The Resource Allocation Graph (RAG) is a directed graph used to model the allocation and request of resources in a system to detect deadlocks. In this graph:
- Processes are represented by nodes (circles).
- Resources are represented by nodes (squares or rectangles).
- Request Edge: An edge from a process to a resource signifies a request for that resource by the process. If process Pi is requesting resource Rj, we draw a directed edge from Pi to Rj (denoted as Pi → Rj).
- Assignment Edge: An edge from a resource to a process indicates that the resource has been allocated to the process. If process Pi has been allocated resource Rj, we draw a directed edge from Rj to Pi (denoted as Rj → Pi).    

Deadlock Detection in RAG:
- If there is a cycle in the graph, it indicates that each process is holding a resource and waiting for another resource held by another process creating a circular wait, this cycle can indicate a potential deadlock.
- A cycle in the Resource Allocation Graph can be used to detect deadlocks.
- If no cycle is present in the graph, the system is considered to be deadlock-free.


Processes: P1, P2    Resources: R1, R2

Allocation and Request:
- P1 holds R1 and requests R2.
- P2 holds R2 and requests R1.

The Resource Allocation Graph will look like this:
```
P1 → R2 → P2 → R1 → P1
```

In this case, we have a cycle (P1 → R2 → P2 → R1 → P1), indicating a deadlock.

____

Consider the following resource allocation system:
- Processes: P1, P2, P3
- Resources: R1, R2, R3
- Allocations:
    - P1 holds R1, requests R2.
    - P2 holds R2, requests R3.
    - P3 holds R3, requests R1.

The Resource Allocation Graph will look like this:
```
P1 → R2 → P2 → R3 → P3 → R1 → P1
```

This graph contains a cycle: P1 → R2 → P2 → R3 → P3 → R1 → P1, indicating a circular wait.

In this case, the cycle represents a deadlock, as no process can proceed because they are all waiting for resources held by other processes in the cycle, and no resources are available to break the cycle.


Circular wait, which is one of the necessary conditions for a deadlock to occur. Deadlock exists if a cycle exists, but it is also dependent on the availability of resources to break the cycle and allow processes to complete.

The existence of a cycle is necessary but not sufficient for deadlock:
- A cycle in the RAG does not always guarantee deadlock if resources can be preempted or if processes can be aborted. Deadlock requires that a process cannot make progress, i.e., it must be waiting indefinitely for a resource that is never released.
- Therefore, if there are available resources to break the cycle, the system can avoid deadlock.

___

23. Explain the dining philosophers problem with code snippets and explain how the deadlock situation is avoided in the problem.

24. Elaborate the facts with the system model to acquire required resources.

25. Present the definitions for the following terms:    
- i) Safe state
- ii) Aborted state
- iii) Claim edge
- iv) Cycle state

16. Let a system have P1, P2, P3, P4 processes and r1 and r2 resources. Both resources have 2 instances. The set E is given by:  `E = {<P1 -> r1>, <r1 -> P2>, <r1 -> P3>, <P3 -> r2>, <r2 -> P4>, <r2 -> P1> }` Does the system lead to a deadlock?


_____
