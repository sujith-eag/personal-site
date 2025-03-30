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



### **Process Management**
1. a) Write a short note on the following with respect to processes:  
   i) Process State  
   ii) Process Control Block (PCB)  
   b) Define a process. List the different fields of a process control block.  
   c) Define a process and present its various states.  
   d) What is the critical section problem? Explain the requirements that must be satisfied by its solution.  
   e) What are the requirements for providing a solution to the critical section problem? Explain.  

---

### **CPU Scheduling**
1. a) Why is it important for the scheduler to distinguish I/O-bound programs and CPU-bound programs?  
   b) Consider the following set of processes:  

| Process | Priority | Arrival Time (ms) | Burst Time (ms) |
|---------|----------|--------------------|-----------------|
| P1      | 2        | 0                  | 10              |
| P2      | 1        | 2                  | 4               |
| P3      | 4        | 0                  | 2               |
| P4      | 1        | 5                  | 1               |
| P5      | 3        | 4                  | 6               |

   i) Draw Gantt charts for SJF and Preemptive-Priority scheduling algorithms.  
   ii) Calculate the waiting time and average waiting time for each algorithm.  
   iii) Calculate the turnaround time and average turnaround time for each algorithm.  
   iv) Which is the more efficient algorithm?  

   c) Consider the following processes:  

| Process | Arrival Time (ms) | CPU Time (ms) |
|---------|--------------------|---------------|
| P1      | 0                  | 3             |
| P2      | 2                  | 3             |
| P3      | 3                  | 5             |
| P4      | 4                  | 2             |
| P5      | 8                  | 3             |

   i) Draw the Gantt chart for the SJF algorithm.  
   ii) Calculate the average waiting and turnaround times for FCFS and Round-Robin scheduling (time slice = 1 ms).  

---

### **Scheduling Algorithms**
1. a) Assume the following jobs are executed with one processor:  

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

   b) Five batch jobs arrive simultaneously. Their estimated running times (in milliseconds) and priorities are:  

| Job | Estimated Time | Priority |
|-----|----------------|----------|
| A   | 10             | 3        |
| B   | 6              | 5        |
| C   | 2              | 2        |
| D   | 4              | 1        |
| E   | 8              | 4        |

   i) Draw Gantt charts for Round Robin (Quantum = 5 ms), Priority Scheduling, and SJF algorithms.  
   ii) Determine average waiting and turnaround times for each algorithm.  

   c) Present criteria to evaluate the best CPU scheduling algorithm.  

---

### **Synchronization**
1. a) Write the code snippets for hardware-based lock instructions `TestAndSet()` and `Swap()`.  
   b) Describe the N-process solution to the critical section problem using `test()` and `set()` atomic instructions.  
   c) What is a semaphore? Discuss the Dining Philosophers problem.  
   d) Provide the solution for the Dining Philosophers problem using semaphores.  

---

### **Multiprocessing**
1. a) Describe the differences between symmetric and asymmetric multiprocessing.  
   b) What are the advantages and disadvantages of multiprocessor systems?  
   c) Explain processor affinity. How is it useful in multiprocessor scheduling?  
   d) Discuss load balancing and symmetric multithreading in multiprocessor scheduling.  

---

### **Interprocess Communication (IPC)**
1. a) Explain IPC using message passing with an example.  
   b) Define the following terms:  
      i) Dispatcher  
      ii) Short-term scheduler  
      iii) Context switching  
      iv) CPU-bound processes  
      v) I/O-bound processes  
      vi) Device queue  

---
____
___

# Raw Questions


**3.**  
a) Write a short note on the following with respect to processes:  
i) Process State  
ii) Process Control Block (PCB)  
b) Why is it important for the scheduler to distinguish I/O-bound programs and CPU-bound programs?  
c) Write the code snippet for hardware-based lock instructions `TestAndSet()` and `Swap()`.

**4.**  
a) Explain IPC using message passing with an example.  
b) Consider the following set of processes:

|Process|Priority|Arrival Time (ms)|Burst Time (ms)|
|---|---|---|---|
|P1|2|0|10|
|P2|1|2|4|
|P3|4|0|2|
|P4|1|5|1|
|P5|3|4|6|

The lowest number in priority indicates the highest priority of the process.

i) Draw Gantt charts that illustrate the execution of these processes using SJF and Preemptive-Priority scheduling algorithms.  
ii) What is the waiting time of each process and the average waiting time for each scheduling algorithm?  
iii) What is the turnaround time of each process and the average TAT for each scheduling algorithm?  
Which is the more efficient algorithm among these?



**3.**  
a) Define a process. List the different fields of a process control block.  
b) Consider the following processes:

| Process | Arrival Time (ms) | CPU Time (ms) |
|---------|--------------------|---------------|
| P1      | 0                  | 3             |
| P2      | 2                  | 3             |
| P3      | 3                  | 5             |
| P4      | 4                  | 2             |
| P5      | 8                  | 3             |

   i) Draw the Gantt chart for the SJF algorithm.  
   ii) Calculate the average waiting time and average turnaround time for FCFS and Round-Robin scheduling (time slice = 1 ms).  

c) What are the requirements for providing a solution to the critical section problem? Explain.

**4.**  
a) Assume you have the following jobs to execute with one processor, arriving in the listed order:

| Process | Burst Time |
|---------|------------|
| P0      | 80         |
| P1      | 20         |
| P2      | 10         |
| P3      | 20         |
| P4      | 50         |

   i) Draw a Gantt chart illustrating the execution of these processes using FCFS scheduling.  
   ii) What is the turnaround time for process P3?  
   iii) What is the average waiting time for the processes?  

b) What is processor affinity? How is it useful in multiprocessor scheduling?  
c) Describe the N-process solution to the critical section problem using `test()` and `set()` atomic instructions. Explain how the algorithm satisfies all requirements of the critical section.



**3.**  
a) Consider the following set of processes, with the length of the CPU burst given in milliseconds. The processes arrived in the order P1, P2, P3, P4, P5, all at time 0:  

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

b) Explain processor affinity.  

**4.**  
a) Describe the differences between symmetric and asymmetric multiprocessing. What are the advantages and disadvantages of multiprocessor systems?  
b) Provide the solution for the Dining Philosophers problem using semaphores.  



**3.**  
a) Five batch jobs (A through E) arrive at a computer center almost simultaneously. Their estimated running times (in milliseconds) and priorities (with 5 being the highest priority) are as follows:  

| Job | Estimated Time | Priority |
|-----|----------------|----------|
| A   | 10             | 3        |
| B   | 6              | 5        |
| C   | 2              | 2        |
| D   | 4              | 1        |
| E   | 8              | 4        |

For each of the following scheduling algorithms, draw the Gantt chart and determine the average waiting time and average turnaround time:  
   i) Round Robin with priority basis (Quantum = 5 milliseconds)  
   ii) Priority Scheduling  
   iii) Shortest Job First (SJF)  

b) Present the various criteria to be considered when evaluating the best CPU scheduling algorithm.  
c) Discuss load balancing and symmetric multithreading with respect to multiprocessor scheduling.  

**4.**  
a) Define the following terms:  
   i) Dispatcher  
   ii) Short-term scheduler  
   iii) Context switching  
   iv) CPU-bound processes  
   v) I/O-bound processes  
   vi) Device queue  

b) What is the critical section problem? Explain the requirements that must be satisfied by its solution.  
c) What is a semaphore? Discuss the Dining Philosophers problem.  



**3.**  
a) Consider the following set of processes, with the length of the CPU burst given in milliseconds. The processes arrived in the order P1, P2, P3, P4, P5, all at time 0:  

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

b) Explain processor affinity.  

**4.**  
a) Describe the differences between symmetric and asymmetric multiprocessing. What are the advantages and disadvantages of multiprocessor systems?  
b) Provide the solution for the Dining Philosophers problem using semaphores.  

_____
