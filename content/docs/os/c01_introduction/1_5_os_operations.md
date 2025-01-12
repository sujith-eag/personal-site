---
title: "OS 1.05 - OS Operations"
description: ""
summary: ""
date: 2025-01-12T21:21:19+05:30
lastmod: 2025-01-12T21:21:19+05:30
draft: false
weight: 2001
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


**Interrupts, System Calls, and Modes of Operation**

## **Interrupt-Driven Systems**

Modern Operating Systems are **interrupt-driven**, meaning they rely on **interrupts** to perform tasks. If there are no I/O devices to service or no user requests, the OS remains idle, waiting for events to occur.

### **Interrupts**
An **interrupt** is a signal to the processor indicating that an event has occurred, prompting the OS to take specific actions.      
A **trap** (or **exception**) is a software-generated interrupt triggered by errors (e.g., division by zero, invalid memory access) or by a user program requesting an operating system service.

### **Interrupt Service Routine**
For each type of interrupt, the OS contains specific code that determines the appropriate action. The OS uses an **Interrupt Service Routine (ISR)** to handle interrupts when they occur.

Since both the OS and users share the hardware and software resources, any error in a user program should only affect that particular program, not the entire system. However, issues such as infinite loops or erroneous programs modifying data from other programs can cause system-wide problems.

> **Note:** A properly designed OS ensures that a faulty or malicious program does not negatively affect other running programs or the OS itself.

___

### **Interrupt vs. Trap**

> **Question:** What is the difference between a **trap** and an **interrupt**?
> 
> Both **traps** and **interrupts** are mechanisms that allow the operating system to take control of the processor, but they are triggered in different ways and serve different purposes:       
> 
> A **trap** is a software-generated interrupt, typically triggered by a user program requesting a service or due to errors, while **interrupts** can be caused by external events, such as hardware I/O requests.
> 
> While **interrupts** are typically hardware-driven and serve external events, **traps** are software-driven, usually related to program errors or service requests. Both mechanisms transfer control to the OS, but **privileged instructions** are used to prevent unauthorized programs from interfering with critical system operations.


1. **Interrupt**:
   - **Cause**: Interrupts are typically **hardware-driven** events that occur asynchronously. These can be triggered by external hardware devices (such as I/O devices) that need the processor's attention (e.g., when input/output operations are completed, or a timer has expired).
   - **Function**: Interrupts notify the processor that it must temporarily stop executing the current instructions to handle an external event. After the interrupt is serviced, the processor resumes its previous task.
   - **Example**: A keyboard press, network packet arrival, or disk I/O completion.

2. **Trap (or Exception)**:
   - **Cause**: A **trap** (or **exception**) is **software-generated** and occurs synchronously. It is usually caused by an event that arises during program execution, such as an error or a system call (where a program requests an OS service).
   - **Function**: Traps are triggered by **program execution** and can indicate issues like errors or a specific request for operating system services. They often signal that a process needs special handling from the OS (e.g., an invalid memory access or division by zero).
   - **Example**: A program attempting to divide by zero or access invalid memory.

**Interrupts**: These are managed by the OS, which often includes **privileged instructions** for interrupt handling (e.g., enabling or disabling interrupts). Interrupts are generally not allowed to be triggered by user programs directly.
  
**Traps**: User programs can trigger a trap (e.g., by making a system call), but they cannot directly trigger interrupts. The OS provides specific instructions to handle these, and **privileged instructions** are restricted to the kernel to prevent misuse by user applications.


| Feature          | **Interrupt**                                                        | **Trap (Exception)**                                                                          |
| ---------------- | -------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **Trigger**      | Hardware event (asynchronous)                                        | Software event (synchronous)                                                                  |
| **Cause**        | External devices (I/O, timer, etc.)                                  | Program errors or system calls (e.g., divide by zero, invalid memory access)                  |
| **Control Flow** | Control is transferred to the OS immediately to handle the event     | Control is transferred to the OS by the program itself (typically via a system call or error) |
| **Handling**     | Typically involves service routines for external hardware management | Involves error handling or system service routines                                            |


---

## **1.5.1 Dual-Mode and Multi-Mode Operation**

### **User Mode vs Kernel Mode**

To protect the OS from errant user programs and vice versa, the OS operates in two main modes: **User Mode** and **Kernel Mode** (also called **system mode**, **privileged mode**, or **supervisor mode**).

- **User Mode (1)**: The mode in which user applications run.
- **Kernel Mode (0)**: The privileged mode in which the OS operates and can execute sensitive instructions.

A **mode bit** is added to the CPU to indicate the current mode of operation. This dual-mode operation helps protect the OS by restricting certain instructions, called **privileged instructions**, to **Kernel Mode**. These privileged instructions may include tasks like I/O control, interrupt management, and timer management.

> **Examples of privileged instructions**:  
> - Switching between modes (User to Kernel or Kernel to User)
> - I/O control
> - Timer management
> - Interrupt management

[image for transition from user mode to kernel mode]


---

### **Multi-Mode Operation**

Some CPU's support more than two modes of operation.      
For example, systems supporting **virtualization** may have a mode for the **Virtual Machine Manager (VMM)** that has more privileges than user programs to create virtual machines and to change the state of CPU but fewer privileges than the Kernel.

> **Note:** CPU's like the Intel 64 family support **privilege levels** for virtualization, but they do not have a separate mode specifically for virtualization.


---

#### **Mode Transition and Control Flow**

At system startup, the hardware begins in **Kernel Mode**. As the OS loads, it switches to **User Mode** to run applications. The OS switches back to **Kernel Mode** when responding to system calls, interrupts, or traps. Before passing the control to a user program, the system always switches to user mode.

1. **Boot time**: The system starts in **Kernel Mode**.
2. **User applications**: When the OS loads user applications, it switches to **User Mode**.
3. **System Call/Interrupt/Trap**: When a user application requests OS services or an error occurs, the system switches to **Kernel Mode** to process the request or handle the issue.
4. **Return to User Mode**: Once the OS has completed the task, it returns to **User Mode** to resume the user application.

---

## **System Calls**

A **System Call** is a mechanism that allows a user program to request services from the OS to perform tasks on the user program's behalf, typically involving privileged operations that are otherwise restricted.

System calls are usually implemented as **traps** that transfer control to a specific location in the **interrupt vector**.

##### Execution of a system call

- When a system call is executed, it is treated by the hardware as a **software interrupt**.
- The **interrupt vector** passes control to a **service routine** in the OS, and the system switches to **Kernel Mode**. (The **system-call service routine** is a part of the operating system. )
- The kernel examines the interrupting instruction to determine what system call has occurred.
- A parameter indicates what type of service the user program is requesting.
- The OS then verifies the system call parameters to be legal.
- Executes the requested task, and returns control to the user program.


>[!control passing] Control Flow of a System call
> * Interrupt / Trap
> * Interrupt Vector
> * OS
> * Service routine (System-call service routine in OS)
> * Kernel


> **Example in MIPS**: A specific `syscall` instruction is used to invoke a system call.

---

### **Preventing Illegal Execution**

Once hardware protection is in place, it detects errors that violate modes. 

When the system is in **Kernel Mode**, it can detect errors that violate the operating modes, such as illegal instruction execution or unauthorized memory access. These errors are handled by the OS:

- If a user program attempts to execute an illegal instruction or access unauthorized memory which is not in the user's address space, the hardware **traps** to the OS.
- The OS handles the error, typically terminating the program abnormally and providing an error message.
- The system may also generate a **memory dump** for debugging purposes, which is saved to a file for analysis.

> **Note**: The absence of hardware-supported dual-mode operation can lead to serious issues. For instance, **MS-DOS**, which was designed for the Intel 8088 without a mode bit, allowed user programs to overwrite the OS and access hardware directly, resulting in potential system crashes.

---

### **1.5.2 Timer**

A **Timer** is a critical component in the OS to maintain control over execution. It can interrupt the system after a fixed or variable period, preventing user programs from running indefinitely.

- A **fixed-rate clock** and a **counter** are used to implement a variable timer.
- The OS initializes the counter, and each time the clock ticks, the counter is decremented. When the counter reaches zero, an interrupt occurs.
- Timer interrupts ensure that a program does not run too long or gets stuck in an infinite loop and never return control to OS.

#### **Timer Usage Example**
- A program with a 7-minute limit could have its timer initialized to **420** (7 minutes in seconds).
- Each second, the counter decrements by 1, and control returns to the user program as long as the counter is positive.
- If the counter reaches zero, the OS terminates the program for exceeding its time limit.

> **Example Timer Configuration**:  
> A 10-bit counter with a 1-millisecond clock allows for interrupts at intervals ranging from 1 millisecond to 1,024 milliseconds (1 second).

Before transferring control to a user program, the OS ensures that the timer is set. If the timer interrupts, control is passed to the OS, which can either treat the interrupt as an error or extend the program's time.

Instructions that modify the content of the timer are privileged.


---
