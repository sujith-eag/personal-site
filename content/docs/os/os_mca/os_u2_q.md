---
title: "OS - Unit-2 - Previous Questions"
description: ""
summary: ""
date: 2025-01-12T21:20:56+05:30
lastmod: 2025-01-12T21:20:56+05:30
draft: false
weight: 1982
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



### Process Basics

- Define a process. List the different fields of a Process Control Block (PCB).

- What is a Process Control Block (PCB)? Explain its contents.

- Write a short note on the following with respect to processes:   i) Process State   ii) Process Control Block (PCB)

- Define a process and present its various states.

- Explain the different states of a process with a neat diagram.

- Explain how a system process is created and terminated.


### Scheduling and Execution

- Explain the various process schedulers.

- Describe the role and functioning of context switching.

- Define the following terms:  
	i) Dispatcher  
	ii) Short-term scheduler  
	iii) Context switching  
	iv) CPU-bound processes  
	v) I/O-bound processes  
	vi) Device queue

### Critical Section Problem

- What is the critical section problem? Explain the requirements that must be satisfied by its solution.

- What are the requirements for providing a solution to the critical section problem? Explain.

---

## Synchronization

- Write the code snippets for hardware-based lock instructions `TestAndSet()` and `Swap()`.

- Describe the N-process solution to the critical section problem using `test()` and `set()` atomic instructions.

- What is a semaphore? Discuss the Dining Philosophers problem.

- Provide the solution for the Dining Philosophers problem using semaphores.

---

## Multiprocessing

- Describe the differences between symmetric and asymmetric multiprocessing.

- What are the advantages and disadvantages of multiprocessor systems?

- Explain processor affinity. How is it useful in multiprocessor scheduling?

- Discuss load balancing and symmetric multithreading in multiprocessor scheduling.

---

## Interprocess Communication (IPC)

- What is IPC? Explain the two models of IPC.

- Explain IPC using message passing with an example.

- What is interprocess communication? Elaborate on the reasons for providing an environment that allows process cooperation.

- Elaborate on the benefits of interprocess communication. List the differences between direct communication and indirect communication.

- Is cooperation among processes necessary? Justify.

---

### CPU Scheduling Problems

1. Why is it important for the scheduler to distinguish I/O-bound programs and CPU-bound programs?  

2. Present various criteria to evaluate the best CPU scheduling algorithm.

3. Consider the following set of processes:  

| Process | Priority | Arrival Time (ms) | Burst Time (ms) |
| ------- | -------- | ----------------- | --------------- |
| P1      | 2        | 0                 | 10              |
| P2      | 1        | 2                 | 4               |
| P3      | 4        | 0                 | 2               |
| P4      | 1        | 5                 | 1               |
| P5      | 3        | 4                 | 6               |
The lowest number in priority indicates the highest priority of the process.

   i) Draw Gantt charts for SJF and Preemptive-Priority scheduling algorithms.  
   ii) Calculate the waiting time and average waiting time for each algorithm.  
   iii) Calculate the turnaround time and average turnaround time for each algorithm.  
   iv) Which is the more efficient algorithm?

___

3. Consider the following processes:  

| Process | Arrival Time (ms) | CPU Time (ms) |
|---------|--------------------|---------------|
| P1      | 0                  | 3             |
| P2      | 2                  | 3             |
| P3      | 3                  | 5             |
| P4      | 4                  | 2             |
| P5      | 8                  | 3             |

   i) Draw the Gantt chart for the SJF algorithm.  
   ii) Calculate the average waiting and turnaround times for FCFS and Round-Robin scheduling (time slice = 1 ms).  

____

4. Consider the following set of processes, with the length of the CPU burst given in milliseconds. The processes arrived in the order P1, P2, P3, P4, P5, all at time 0:  

| Process | Burst Time | Priority |
|---------|------------|----------|
| P1      | 8          | 4        |
| P2      | 2          | 1        |
| P3      | 2          | 3        |
| P4      | 3          | 3        |
| P5      | 5          | 2        |

i) Draw Gantt charts for the following scheduling algorithms:  
   - First-Come-First-Serve (FCFS)  
   - Non-Preemptive Priority Scheduling  
   - Round Robin (Time Quantum = 1 ms)  

ii) Calculate the waiting time of each process for each scheduling algorithm. Also, find the average waiting time for each algorithm.  
iii) Calculate the turnaround time of each process for each scheduling algorithm. Also, find the average turnaround time for each algorithm.

___

5. Assume the following jobs are executed with one processor:  

| Process | Burst Time |
|---------|------------|
| P0      | 80         |
| P1      | 20         |
| P2      | 10         |
| P3      | 20         |
| P4      | 50         |

   i) Draw a Gantt chart for FCFS scheduling.  
   ii) Calculate the turnaround time for process P3.  
   iii) Determine the average waiting time.  

___

6. Five batch jobs arrive simultaneously. Their estimated running times (in milliseconds) and priorities (with 5 being the highest priority) are as follows:  

| Job | Estimated Time | Priority |
|-----|----------------|----------|
| A   | 10             | 3        |
| B   | 6              | 5        |
| C   | 2              | 2        |
| D   | 4              | 1        |
| E   | 8              | 4        |

   i) Draw Gantt charts for Round Robin (Quantum = 5 ms), Priority Scheduling, and SJF algorithms.  
   ii) Determine average waiting and turnaround times for each algorithm.  

---
