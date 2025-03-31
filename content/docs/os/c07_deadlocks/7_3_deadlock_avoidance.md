---
title: "OS 7.03 - Deadlock Avoidance"
description: ""
summary: ""
date: 2025-01-12T21:27:49+05:30
lastmod: 2025-01-12T21:27:49+05:30
draft: false
weight: 2042
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

### Deadlock Avoidance

Deadlock avoidance requires that the operating system be given additional information about how resources are to be requested during a processes lifetime. 

With this knowledge of the complete sequence of requests and releases for each thread, the system can decide for each request whether or not the thread should wait in order to avoid a possible future deadlock.

To decide whether the current request can be satisﬁed or must be delayed, the system must consider the resources currently available, the resources currently allocated to each process, and the future requests and releases of each process.


The simplest and most useful model requires that each thread declare the maximum number of resources of each type that it may need.

The resource-allocation state is defined by the number of available and allocated resources and the maximum demands of the threads.


#### 1. Safe State

A state is safe if the system can allocate resources to each thread (up to its maximum) in some order and still avoid a deadlock. 
A system is in a safe state only if there exists a safe sequence.
If no such sequence exists, then the system state is said to be unsafe.

A sequence of threads <T1 , T2 , ..., Tn > is a safe sequence for the current allocation state if, for each Ti , the resource requests that Ti can still make can be satisfied by the currently available resources plus the resources held by all Tj , with j < i.
if the resources that Ti needs are not immediately available, then Ti can wait
until all Tj have finished. When they have finished, Ti can obtain all of its needed resources.


A deadlocked state is an unsafe state. Not all unsafe states are deadlocks, however an unsafe state may lead to a deadlock.


Whenever a thread requests a resource that is currently available, the system
must decide whether the resource can be allocated immediately or the thread
must wait. The request is granted only if the allocation leaves the system in a
safe state.
In this scheme, if a thread requests a resource that is currently available, it
may still have to wait. Thus, resource utilization may be lower than it would
otherwise be.


#### 2. Resource Allocation Graph Algorithm

In addition to the request and assignment edges in RAG, a new type of edge, called a claim edge is used for deadlock avoidance.

A claim edge Ti → Rj indicates that thread Ti may request resource Rj at some time in the future. This edge resembles a request edge in direction but is represented in the graph by a dashed line. 

When thread Ti requests resource Rj , the claim edge Ti → Rj is converted to a request edge. 
When a resource Rj is released by Ti , the assignment edge Rj → Ti is reconverted to a claim edge Ti → Rj .

Now suppose that thread Ti requests resource Rj . The request can be
granted only if converting the request edge Ti → Rj to an assignment edge
Rj → Ti does not result in the formation of a cycle in the resource-allocation
graph by using a cycle-detection algorithm. 

If no cycle exists, then the allocation of the resource will leave the system
in a safe state. If a cycle is found, then the allocation will put the system in
an unsafe state. In that case, thread Ti will have to wait for its requests to be
satisfied.

(An algorithm for detecting a cycle in this graph requires an order of n2 operations, where n is the number of threads in the system.)

{{< figure  src="images/os/7_07_DeadlockAvoidance-min.jpg"  alt="."  caption="." >}}



Suppose that T2 requests R2 . Although R2 is currently free, we cannot allocate it to T2 , since this action will create a cycle in the graph. A cycle, as mentioned, indicates that the system is in an unsafe state. If T1 requests R2 , and T2 requests R1 , then a deadlock will occur.


{{< figure  src="images/os/7_08_UnsafeState-min.jpg"  alt="."  caption="." >}}


The resource-allocation-graph algorithm is not applicable to a resource-
allocation system with multiple instances of each resource type.

#### 3. Banker's Algorithm


When a new thread enters the system, it must declare the maximum num-
ber of instances of each resource type that it may need. This number may not
exceed the total number of resources in the system. When a user requests a
set of resources, the system must determine whether the allocation of these
resources will leave the system in a safe state. If it will, the resources are allo-
cated; otherwise, the thread must wait until some other thread releases enough
resources.


Several data structures must be maintained to implement the banker’s algorithm. 
n is the number of threads in the system and m is the number of resource types :

Available. A vector of length m indicates the number of available resources
of each type. If `Available[j]` equals k, then k instances of resource type Rj
are available.

Max : An n × m matrix defines the maximum demand of each thread. If `Max[i][j]` equals k, then thread Ti may request at most k instances of resource type Rj .


Allocation. An n × m matrix defines the number of resources of each type
currently allocated to each thread. If `Allocation[i][j]` equals k, then thread
Ti is currently allocated k instances of resource type Rj .

Need. An `n × m` matrix indicates the remaining resource need of each
thread. If `Need[i][j]` equals k, then thread Ti may need k more instances of
resource type Rj to complete its task. 

`Need[i][j] = Max[i][j]− Allocation[i][j]`.


Resource-Request Algorithm for determining whether requests can be safely granted:      

1. If `Requesti ≤ Needi` , go to step 2. Otherwise, raise an error condition, since the thread has exceeded its maximum claim.
2. If `Requesti ≤ Available`, go to step 3. Otherwise, `Ti` must wait, since the resources are not available.
3. Have the system pretend to have allocated the requested resources to thread `Ti` by modifying the state as follows:

`Available = Available–Requesti`   (remove from available)
`Allocationi = Allocationi + Requesti`  (add it to allocation)
`Needi = Needi –Requesti`  (remaining need is reduced)

If the resulting resource-allocation state is safe, the transaction is completed, and thread `Ti` is allocated its resources. However, if the new state is unsafe, then `Ti` must wait for `Requesti` , and the old resource-allocation state is restored.

____

> Problems on Banker's algorithm


| Process | Allocation (A, B, C) | Max (A, B, C) | Available (A, B, C) |
| ------- | -------------------- | ------------- | ------------------- |
| T0      | 0, 1, 0              | 7, 5, 3       | 3, 3, 2             |
| T1      | 2, 0, 0              | 3, 2, 2       |                     |
| T2      | 3, 0, 2              | 9, 0, 2       |                     |
| T3      | 2, 1, 1              | 2, 2, 2       |                     |
| T4      | 0, 0, 2              | 4, 3, 3       |                     |

Need Matrix

| Task | A   | B   | C   |
| ---- | --- | --- | --- |
| T0   | 7   | 4   | 3   |
| T1   | 1   | 2   | 2   |
| T2   | 6   | 0   | 0   |
| T3   | 0   | 1   | 1   |
| T4   | 4   | 3   | 1   |

We claim that the system is currently in a safe state. The sequence <T1 , T3 , T4 , T2 , T0 > satisfies the safety criteria. 

Suppose T1 requests (1,0,2), we first check that `Request1 ≤ Available` which is `(1,0,2) ≤ (3,3,2)` which is true.

We then pretend that this request has been fulfilled, and we arrive at the following new state of need and allocation:


| Process | Allocation (A, B, C) | Need (A, B, C) | Available (A, B, C) |
| ------- | -------------------- | -------------- | ------------------- |
| T0      | 0, 1, 0              | 7, 4, 3        | 2, 3, 0             |
| T1      | 3, 0, 2              | 0, 2, 0        |                     |
| T2      | 3, 0, 2              | 6, 0, 0        |                     |
| T3      | 2, 1, 1              | 0, 1, 1        |                     |
| T4      | 0, 0, 2              | 4, 3, 1        |                     |
we execute our safety algorithm and find that the sequence <T1 , T3 , T4 , T0 , T2 > satisfies the safety requirement. Hence, we can immediately grant the request of thread T1 .


When the system is in this state, a request for (3,3,0) by T4 cannot be granted, since the resources are not available.

A request for (0,2,0) by T0 cannot be granted, even though the resources are available, since the resulting state is unsafe with no safe sequence.


_____
