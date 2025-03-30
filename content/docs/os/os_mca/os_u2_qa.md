---
title: "OS - Unit-2 - Answered"
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



A **program** is a passive entity. It is essentially a file that contains a list of instructions (e.g., an executable file) along with associated resources.

A **program becomes a process** when it is loaded into memory. A process is an active instance of a program, with its own execution context.

Internally, every process is represented by several components:

- **Text Section:** Contains the executable code of the program.
- **Data Section:** Stores global and static variables.
- **Process Stack:** Stores temporary data such as:
    - Function parameters
    - Return addresses
    - Local variables
- **Heap Section:** Dynamically allocated memory during runtime that grows and shrinks as the program executes.

#### **Structure of a Process in Memory:**

{{< figure src="images/os/3_01_Process_Memory.jpg" alt="3.01 A Process in Memory" caption="3.01 A Process in Memory" >}}

---

While multiple processes can be associated with the same program, each process is considered a separate execution sequence. For instance:

- Different users running distinct copies of the same program, or
- A single user running multiple instances of a program, like a web browser.

In these cases, each process is independent, even though their text sections (program code) may be identical. The **data**, **heap**, and **stack** sections will differ for each process.

Modern computer systems enable multiple programs to be loaded and executed concurrently. This requires tighter control and better compartmentalization of resources, leading to the concept of a **process**, which is a program in execution.

---

### **Process State**

As a process runs, it transitions through various **states** depending on its current activity. A process can be in one of the following states:

- **New:** The process is in the process of being created.
- **Running:** The process is actively executing instructions.
- **Waiting:** The process is waiting for some event, such as I/O completion or signal reception.
- **Ready:** The process is ready to be assigned to the CPU.
- **Terminated:** The process has completed its execution.

{{< figure src="images/os/3_02_ProcessState.jpg" alt="3.02 States Of Process" caption="3.02 States Of Process" >}}

**Note:**

- Only one process can be in the **running** state on the CPU at any given moment.
- Multiple processes can be in the **ready** or **waiting** states at the same time.

---

### **Process Control Block (PCB)**

Every process in an operating system is represented by a **Process Control Block (PCB)**, also known as a **Task Control Block**.

{{< figure src="images/os/3_03_PCB.jpg" alt="3.03 Process Control Block" caption="3.03 Process Control Block" >}}

The PCB holds important information related to a process:

- **Process State:** The current state of the process (e.g., Running, Waiting, Ready).
- **Program Counter:** The address of the next instruction to be executed in the process.
- **CPU Registers:** All registers that the process uses (e.g., general-purpose registers, stack pointers).
- **CPU Scheduling Information:** Includes process priority, pointers to scheduling queues, and other scheduling parameters.
- **Memory Management Information:** Includes base and limit registers, page tables, or segment tables, depending on the memory system.
- **Accounting Information:** Tracks CPU and real time usage, time limits, account numbers, and job or process identifiers.
- **I/O Status Information:** Lists I/O devices allocated to the process and any open files.

When an interrupt occurs, the program counter and other state information must be saved to allow the process to resume execution correctly once the interrupt is handled.

{{< figure src="images/os/3_04_ProcessSwitch.jpg" alt="3.04 Process Switching" caption="3.04 Process Switching" >}}

---

### **Process Scheduling**

The goal of **multiprogramming** is to ensure that the CPU is always being utilized, thereby maximizing **CPU utilization**. The objective of **time-sharing systems** is to switch the CPU between processes rapidly enough that users can interact with each program while it runs.

The **Process Scheduler** selects an available process from the set of processes waiting for execution on the CPU whenever one process must wait, improving system efficiency.

When there are more processes than available CPU time, some processes will have to wait until the CPU becomes free again.

---

#### **Scheduling Queues**

- **Job Queue:**  
    Processes enter the **job queue** when they are submitted for execution. This queue contains all processes in the system.
    
- **Ready Queue:**  
    Processes in main memory that are ready to execute are placed in the **ready queue**.
    
- **Device Queue:**  
    If a process requests I/O (e.g., disk access) and the device is busy, it enters the **device queue** for that specific I/O device. Each device has its own queue.


{{< figure  src="images/os/3_06_QueueingDiagram.jpg"  alt="3.06 Queueing Diagram Representing Process Scheduling"  caption="3.06 Queueing Diagram Representing Process Scheduling" >}}


**CPU-I/O Cycle**: Process execution alternates between CPU bursts and I/O waits until the program terminates.

- **I/O-bound programs**: These programs tend to have short CPU bursts and frequent I/O operations.
- **CPU-bound programs**: These have long CPU bursts and minimal I/O operations.


___

#### **Schedulers**

1. **Long-Term Scheduler (Job Scheduler):**
    - Selects processes from a pool and loads them into memory for execution, controlling the **degree of multiprogramming** (the number of processes in memory).
    
1. **Short-Term Scheduler (CPU Scheduler):**    
    - When the CPU is idle, it selects a process from the **ready queue** and allocates CPU time to it. This ensures that CPU time is used efficiently.

2. **Medium-Term Scheduling:**
	- In multiprogramming systems, sometimes it’s beneficial to remove processes from main memory (swapping them to disk) to reduce the level of multiprogramming and manage system resources.

Swapping allows processes to be later reintroduced into memory and continue execution from where they left off, helping balance memory load and system performance.

{{< figure  src="images/os/3_07_QueuingDiagram2.jpg"  alt="3.07 Medium Term Scheduling in Queueing Diagram"  caption="3.07 Medium Term Scheduling in Queueing Diagram" >}}


---

#### **Context Switching**

A **context switch** occurs when the operating system switches from one process to another. The current process’s state (including CPU registers and other information in the PCB) is saved, and the state of the next process is loaded.

Context switching happens frequently as the CPU alternates between tasks.

- **Overhead:** Context switches add overhead because the system must spend time saving and loading process states, which does not directly contribute to task execution.
    
- **Speed Variation:** The time taken for a context switch can vary depending on system factors, such as memory speed and the number of registers involved.
    

---

#### **Dispatcher**

The **dispatcher** is responsible for transferring control of the CPU to the process selected by the short-term scheduler. The dispatcher performs operations like context switching, switching to user mode, and jumping to the correct program location.

**Dispatch Latency** is the time taken to perform a context switch and start executing a new process. This latency is crucial for optimizing process scheduling efficiency.

---

### **CPU Scheduling**

CPU scheduling happens in the following situations:

1. **Running → Waiting:** A process requests I/O or another resource.
2. **Running → Ready:** An interrupt occurs, causing the process to return to the ready state.
3. **Waiting → Ready:** The process finishes its I/O and is ready to execute again.
4. **Process Termination:** The process completes its execution.

- **Nonpreemptive Scheduling:** Once a process is running, it holds the CPU until it terminates or blocks (e.g., for I/O).

- **Preemptive Scheduling:** The OS can interrupt a running process to allocate CPU time to another process, allowing higher-priority processes to execute. This can lead to race conditions if multiple processes share data.


---

#### **Scheduling Criteria**

To compare different scheduling algorithms, the following criteria are considered:

- **CPU Utilization:** The goal is to maximize CPU usage (e.g., from 40% to 90%).
- **Throughput:** The number of processes completed per unit of time, indicating system efficiency.
- **Turnaround Time:** The total time from process submission to completion, including waiting times.
- **Waiting Time:** The amount of time a process spends waiting in the ready queue.
- **Response Time:** The time from process submission to the first response from the system.

Optimization goals:

- **Maximize** CPU utilization and throughput.
- **Minimize** turnaround time, waiting time, and response time.

---

### **Scheduling Algorithms**

CPU scheduling involves determining which process from the ready queue should be allocated CPU time.

#### **First-Come, First-Served Scheduling (FCFS)**

The **FCFS** scheduling algorithm allocates CPU to processes in the order they arrive, using a **FIFO queue**. The process at the front of the queue gets the CPU, and when it completes, it is removed.

##### **Drawbacks of FCFS**

1. **Monopolization of CPU:** A CPU-bound process consumes the CPU while I/O-bound processes, which could proceed with little CPU time, wait. This leads to inefficient use of I/O devices.
    
2. **Transition and Idle CPU:** Once a CPU-bound process finishes its burst, it moves to the I/O queue, causing idle periods for the CPU while I/O-bound processes complete their tasks.
    
3. **Convoy Effect:** A long CPU-bound process delays smaller, I/O-bound processes, causing inefficient use of resources.
    

---

#### **Shortest Job First Scheduling**

The **Shortest Job First (SJF)** scheduling algorithm assigns the CPU to the process with the shortest CPU burst.  
If two processes have the same burst, **FCFS** is used to break the tie.

- **Nonpreemptive SJF:** The process that starts executing runs until it completes, even if another process arrives with a shorter burst.
    
- **Preemptive SJF:** If a process arrives with a shorter CPU burst than the currently running process, the CPU is preempted and allocated to the new process. This is also known as **Shortest-Remaining-Time-First (SRTF)** scheduling.
    

---

#### **Priority Scheduling**

The **Priority Scheduling** algorithm allocates CPU time based on process priority. The process with the highest priority gets the CPU.  
If two processes have the same priority, **FCFS** is used.

- **Preemptive Priority Scheduling:** A higher-priority process preempts a lower-priority process that is already running.
    
- **Nonpreemptive Priority Scheduling:** A higher-priority process waits until the current process completes or blocks before it executes.


##### **Major Issues:**

**Indefinite Blocking (Starvation):** Low-priority processes may never get to execute because higher-priority processes continuously preempt them.

**Aging** is used to solve starvation by gradually increasing the priority of long-waiting processes, ensuring that they eventually get executed.

---

#### **Round Robin Scheduling**

The **Round-Robin (RR)** scheduling algorithm is a variant of **FCFS**, but with preemption.

- **Time Quantum (or Time Slice):** A small time unit (typically between 10 to 100 milliseconds) allocated to each process.
- **Preemption:** No process is allowed to monopolize the CPU for more than 1 time quantum.

1. The **Ready Queue** functions as a circular queue.
2. The CPU scheduler allocates the CPU to each process for a time quantum.
3. After the time quantum ends, the process is preempted and placed back at the end of the ready queue.

This approach prevents any single process from monopolizing the CPU, allowing for better time-sharing.

---

### **Process Synchronization**

**Process synchronization** involves ensuring that cooperating processes maintain data consistency when accessing shared resources. This is crucial for maintaining the integrity of shared data.

##### **Problems from Concurrent Execution**

A **race condition** occurs when multiple processes or threads concurrently access and modify shared data, leading to inconsistent or incorrect results, depending on the timing of the operations.

#### **Critical Section Problem**

In a system with **n processes** ({P0, P1, ..., Pn-1}), each process has a **critical section**—a segment of code where the process manipulates shared resources. The challenge is ensuring that **no two processes** execute their critical sections simultaneously.

The critical-section problem requires that each process requests permission to enter its critical section, usually in the **entry section** of its code. After executing the critical section, the process enters the **exit section**, followed by the **remainder section**.

##### **Requirements for a Solution:**

A valid solution to the critical-section problem must satisfy:

1. **Mutual Exclusion:** If one process is in its critical section, no other process can enter its critical section at the same time.
2. **Progress:** If no process is in its critical section and multiple processes are waiting, one of the waiting processes must be allowed to enter the critical section.
3. **Bounded Waiting:** There must be a limit on how many times other processes are allowed to enter their critical sections before a waiting process is granted access.


____

