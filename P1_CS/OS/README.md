# OS

- [Difference between process and thread](#Difference-between-process-and-thread)
- [Multi-thread](#Multi-thread)
  - strength and weakness
  - Multi-thread vs Multi-process
- [Scheduler](#Scheduler)
  - Long-term scheduler
  - Short-term scheduler
  - Mid-term scheduler
- [CPU scheduler](#cpu-scheduler)
  - FCFS
  - SJF
  - SRTF
  - Priority scheduling
  - RR
- [Difference between synchronous and asynchronous](#Difference-between-synchronous-and-asynchronous)
- [Process Synchronization](#Process-Synchronization)
  - Critical Section
  - solution
    - Lock
    - Semaphores
    - monitor
- [Memory management strategy](#memory-management-strategy)
  - Memory management background
  - Paging
  - Segmentation
- [Virtual Memory](#Virtual-Memory)
  - background
  - What virtual memory does
  - Demand Paging
  - Page replacement algorithm
- [Locality of cache](#Locality-of-cache)
  - Locality
  - Caching line
- [Interview Questions for OS](#Interview-Questions-for-OS)
  - [Linux](#Linux)
  - [Windows](#Windows)

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

</br>

---

## Difference between process and thread

### Process

A process is a running program that can be loaded into memory from disk and allocated to the CPU. Address space, files, and memory are allocated from the operating system, and these are collectively called processes. Specifically, a process contains a process stack with temporary data such as function parameters, return address and local variables, and a data section that contains global variables. Processes also contain heaps, which are memory dynamically allocated during process execution.

#### Process Control Block (PCB)

The PCB is the data structure of the operating system that stores important information about a specific process. The operating system creates a unique PCB at the same time as the process creation to manage the process. Even though a process is assigned a CPU to process a task, if a process switch occurs, the work in progress must be saved and the CPU returned. At this time, all the work progress is saved in the PCB. And when the CPU is allocated again, the contents stored in the PCB are fetched and the work is performed again from the point where it was previously terminated.

_Information stored on the PCB_

- Process ID (Process ID, PID): Process identification number
- Process status: saves the status of new, ready, running, waiting, terminated, etc.
- Program counter: the address of the next instruction the process will execute
- CPU register
- CPU scheduling information: process priority, pointer to schedule queue, etc.
- Memory management information: Contains information such as page table or segment table
- I/O status information: I/O devices allocated to the process and a list of open files
- Accounting information: CPU time used, time limit, account number, etc.

</br>

### Thread

A thread is the execution unit of a process. Multiple execution flows running within a process can share an address space or resource within a process.
A thread consists of a thread ID, a program counter, a set of registers, and a stack. It shares operating system resources such as code, data sections, and open files and signals with other threads in the same process.
Multithreading is called multithreading that divides one process into multiple execution units to share resources and minimizes the redundancy of resource creation and management to improve performance. In this case, each thread has its own stack and PC register values ​​because each thread must perform an independent task.

#### Why the stack is allocated independently for each thread

Since the stack is a memory space used to store arguments passed when calling a function, address values ​​to be returned, and variables declared within the function, the fact that the stack memory space is independent means that independent function calls are possible. Will be added. Therefore, an independent stack is allocated as the minimum condition for adding an independent execution flow according to the thread definition.

#### Why PC Registers are allocated independently for each thread

The PC value indicates how far the thread has executed the instruction. The thread is allocated a CPU and is preempted again by the scheduler. Therefore, it is necessary to remember to which part the command was executed without being executed continuously. Therefore, the PC registers are allocated independently.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

</br>

---

## Multi-thread

### Advantages of multi-threading

When a task that was simultaneously processed using a process is implemented as a thread, memory space and system resource consumption are reduced. Even when communication between threads is required, data can be exchanged using a space of a global variable or a heap area, which is a dynamically allocated space, instead of using a separate resource. Therefore, the communication method between threads is much simpler than the communication method between processes. Even a thread's context switch is faster because it doesn't need to free cache memory unlike a process context switch. Therefore, the throughtput of the system is improved, the resource consumption is reduced, and the response time of the program is naturally shortened. Because of this advantage, tasks that can be done by multiple processes are performed by dividing them into threads in one process.

</br>

### The problem of multi-threading

When programming based on multi-process, there is no shared resource between processes, so there is no simultaneous access to the same resource, but when programming based on multi-threading, you need to be careful about this. Because different threads share data and heap areas, one thread can access variables or data structures used by other threads to read or modify incorrect values.

Therefore, synchronization is necessary in a multi-threaded environment. It controls the order of work processing and access to shared resources through synchronization. However, there is a high possibility that this will cause a bottleneck and degrade performance. Therefore, it is necessary to reduce the bottleneck caused by excessive locking.

</br>

### Multi-thread vs Multi-process

Multi-thread has the advantage of taking up less memory space and quicker context switching than multi-process, but it has a synchronization problem with the fact that if one thread is terminated due to an error, all threads can be terminated. On the other hand, the multi-process method has the advantage that even if one process dies, it does not affect other processes and runs normally, but has a disadvantage in that it takes up more memory space and CPU time than multi-threads. Both of these are the same in that they perform multiple tasks at the same time, but they are classified according to the system to be applied. Therefore, it is necessary to select and apply an appropriate operation method according to the characteristics of the target system.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

</br>

---

## Scheduler

\_There are three types of queues for scheduling processes.

- Job Queue: Set of all processes in the current system
- Ready Queue: The set of processes currently in memory and waiting to be executed by grabbing the CPU.
- Device Queue: A set of processes waiting for device I/O work

There are largely **three types** of schedulers that put processes in and out of each queue.

### Long-term scheduler or job scheduler

The memory is limited, but when many processes load into memory at once, they are temporarily stored in large memory (usually disk). It plays a role of determining which of the processes stored in this pool will allocate memory and send it to the ready queue.

- Responsible for scheduling between memory and disk.
- Allocate memory (and various resources) to process
- degree of Multiprogramming control
  (Control the number of running processes)
- Process status
  new -> ready(in memory)

\_cf) Even if there are too many programs in memory or too little, performance is not good. For reference, there is no long-term scheduler in the time sharing system. It just goes into memory and becomes ready.

</br>

### Short-term scheduler or CPU scheduler

- Responsible for scheduling between CPU and memory.
- Determine which process to run among the processes existing in the Ready Queue.
- Allocate CPU to process (scheduler dispatch)
- Process status
  - ready -> running -> waiting -> ready

</br>

### Medium-term scheduler or Swapper

- Swapping the whole process from memory to disk to make space
- Deallocate memory from process
- degree of Multiprogramming control
- Scheduler to control the simultaneous loading of too many programs in memory on the current system.
- Process status
  - ready -> suspended

#### Process state - suspended

Suspended(stopped): Refers to a state in which execution of a process has been stopped for external reasons and has been dropped from memory. All processes are swapped out to disk. The blocked state is a state waiting for other I/O operations, so it can return itself to the ready state, but this state cannot be returned by itself because it is suspended for external reasons.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

</br>

---

## CPU scheduler

_Scheduling targets are processes in the Ready Queue._

### First Come First Served (FCFS)

#### Characteristic

- The method of serving customers who came first, that is, in the order they came first.
- Non-Preemptive scheduling
  Once you catch the CPU, it does not return the CPU until the CPU burst is complete. Scheduling occurs only when the allocated CPU is returned.

#### Problem

- convoy effect
  A process with a long time required arrives first, reducing efficiency.

</br>

### SJF(Shortest-Job-First)

#### Characteristic

- Pre-allocation to processes with short CPU burst time even if other processes arrive first
- Non-Preemptive scheduling

#### problem

- starvation
  Pursuing efficiency is paramount, but certain processes should not be overly discriminated against. This scheduling prefers jobs with extremely low CPU usage. So a process with a long usage time can hardly ever be allocated a CPU.

</br>

### Shortest Remaining time First (SRT)

#### Characteristic

- Whenever a new process arrives, a new scheduling is performed.
- Preemptive scheduling
  When a new process arrives with a CPU burst time shorter than the remaining burst time of the currently running process, the CPU is taken away.

#### problem

- starvation
- The CPU burst time cannot be measured because the scheduling is re-scheduled every time a new process arrives.

</br>

### Priority Scheduling

#### Characteristic

- This is the scheduling that allocates CPU to the process with the highest priority. The priority is expressed as an integer, and the smaller number has the higher priority.
- Preemptive scheduling method
  When a higher priority process arrives, it stops running processes and preempts the CPU.
- Non-Preemptive Scheduling Method
  When a higher priority process arrives, it is placed in the head of the Ready Queue.

#### problem

- starvation
- Indefinite blocking
  A state in which the CPU waits indefinitely for a process that is ready to run but cannot use the CPU.

#### solution

- aging
  No matter how low-priority processes are, if you wait a long time, increase the priority.

</br>

### Round Robin

#### Characteristic

- Modern CPU scheduling
- Each process has the same amount of time quantum.
- After the allotted time, the process is preempted and goes back to the end of the ready queue and queues again.
- `RR` is efficient when processes with random CPU usage time are mixed.
- The reason `RR` is possible is because it can save the context of the process.

#### Advantages

- `Response time` is faster.
  If n processes are in the ready queue and the allocation time is q (time quantum), each process gets 1/n of the CPU time in units of q. That is, no process waits more than (n-1)q time units.
- The time the process waits increases as much as it uses the CPU.
  It's fair scheduling.

#### Note

If the set `time quantum` becomes too large, it becomes the same as `FCFS`.
Also, if it is too small, it is ideal for the purpose of the scheduling algorithm, but the overhead occurs due to frequent context switches.
Therefore, it is important to set the appropriate `time quantum`.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

</br>

---

## Difference between synchronous and asynchronous

### Easy explanation by analogy

Suppose you have three tasks to do: laundry, washing dishes, and cleaning. If you do these things synchronously, you do the laundry, wash the dishes, and clean.
If you do things asynchronously, ask the laundry company to do the laundry. Have the dishwashing agency wash the dishes. Have a cleaning agent do the cleaning. It is not known which of the three will be completed first. The company that has finished working has decided to let me know, so I can do other work. In this case, it means asynchronous when the task is processed by a background thread.

### Sync vs Async

In general, the difference between synchronous and asynchronous is that when a method is executed and a return value is expected `at the same time`, it is expressed as **synchronous**, and if not, it is expressed as **asynchronous**. Simultaneous means that when executed, it is `blocking' until the value is returned. In the case of asynchronous, the expected value is not immediately returned because it is not `blocking` and is put on the event queue or the task is delegated to a background thread and the next code is executed.

#### Reference

- https://blog.miguelgrinberg.com/post/sync-vs-async-python-what-is-the-difference

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

</br>

---

## process synchronization

### Critical Section

As shown in the problem of multi-threading, the area of ​​code that executes tasks that simultaneously access the same resource (e.g. using shared variables, using the same file, etc.) is called a critical section.

### Critical Section Problem

It is to design a protocol that processes can use with the Critical Section.

#### Requirements (Basic conditions for resolution)

- Mutual Exclusion
  If process P1 is running in a critical section, other processes cannot run in their critical section.
- Progress
  Only processes that do not have a process running in the critical section and do not have separate actions can participate as candidates for entering the critical section.
- Bounded Waiting
  Until P1 is accepted after applying for entry into the critical section, there must be a limit on the number of times other processes enter the critical section.

### solution

### Lock

- As a hardware-based solution, in order to prevent access to shared resources at the same time, the process entering the critical section acquires a lock and releases the lock when exiting the critical section so that it cannot be accessed simultaneously.

#### Limit

- It cannot be applied in terms of time efficiency in a multiprocessor environment.

### Semaphores

- Synchronization tool to solve critical section problem in software

#### Kinds

OS distinguishes between Counting/Binary semaphores

- Counting semaphore
  It is used for access control to **resources with the available number**, and the semaphore is initialized with the **resource number** available.
  The semaphore decreases when resources are used, and the semaphore increases when released.

- Binary semaphore
  Also called MUTEX, it was created after the acronym of Mutual Exclusion.
  As the name suggests, only values ​​between 0 and 1 are possible, and is used to solve the critical section problem between multiple processes.

#### Disadvantages

- Busy Waiting
  In the early version of Semaphore, called spin lock, a process that had to enter a critical section had to repeatedly execute the entry code and wasted CPU time. This is called Busy Waiting, and it is inefficient unless there is a special situation.
  In general, Semaphore attempts to enter the critical section, but blocks the failed process, and then wakes up again when there is a seat in the critical section. In this case, the problem of wasting time due to busy waiting is solved.

#### Deadlock

- The semaphore has a Ready Queue, two or more processes are waiting indefinitely for entry to the Critical Section, and the process running in the Critical Section refers to a situation in which the process waiting for entry can only exit.

### Monitor

- As a design structure of a high-level language, it is an abstract data form that makes the developer's code mutually exclusive.
- Processes both acquiring a key to access shared resources and releasing after using the resource. (The semaphore requires direct key release and shared resource access processing.)

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

---

## memory management strategy

### Memory management background

Each **process** has its own memory space, and there is a limit to accessing the memory space of the operating system or other processes. However, only the **operating system** is not restricted by access to the operating system memory area and the user memory area.

**Swapping**: A technique used for memory management. In the standard swapping method, in a multi-programming environment with scheduling such as round-robin, the memory of the process whose CPU allocation time has expired can be exported to an auxiliary storage device (e.g. hard disk) and the memory of another process can be loaded.

> This process is called **swap** (**swap**). The process of loading into the main memory (RAM) is called **swap-in**, and the process of exporting to the auxiliary memory is called **swap-out**. Because swap requires a large disk transfer time, swapping starts when memory space is insufficient now.

**Fragmentation** (**Fragmentation**): As processes are repeatedly loaded and removed from memory, small unusable free spaces increase between the memory gaps occupied by processes, which is **fragmentation. ** to be. Fragmentation is divided into two types.

| `Process A` | free | `Process B` | free | `Process C` | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; free &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | `Process D` |
| ----------- | ---- | ----------- | ---- | ----------- | :--------------------------------------------------------------------------------------: | ----------- |

- External fragmentation: The portion of the memory space that becomes unusable. If all the remaining spaces in the physical memory (RAM) are added together, it can be seen that the parts that become sufficient space are **distributed.**
- Internal Fragmentation: The remaining part of the memory space used by the process. For example, if there is 10,000B of free space for partitioning memory and Process A uses 9,998B, there is a difference of 2B, and this phenomenon is called internal fragmentation.

Compression: This is a methodology to secure free space by driving the spaces used by the process to one side to eliminate external fragmentation, but the work efficiency is not good. (The above memory status can have the effect of changing as shown in the figure below through compression)

| `Process A` | `Process B` | `Process C` | `Process D` | &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; free &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; |
| ----------- | ----------- | ----------- | :---------: | ------------------------------------------------------------------------------------------------------------------ |

### Paging

This is a memory management method that removes the restriction that the memory space used by one process must be contiguous.
As a methodology developed to solve external fragmentation and compression, physical memory is divided into fixed size called Frame, and logical memory (occupied by process) is divided into fixed sized blocks called pages. Page to enter)

By using the paging technique, when the logical memory is stored in the physical memory, it does not need to be continuously stored, and it is appropriately disposed in the remaining frames of the physical memory, thereby solving external fragmentation.

The space used by one process is divided into several pages and managed (in logical memory), and individual pages are mapped and stored in frames in physical memory **regardless of order**.

- Disadvantages: The proportion of internal fragmentation problems increases. For example, if the page size is 1,024B, and **Process A** requires 3,172B of memory, a total of 4 page frames are required because 100B remains after 3 page frames (1,024 \* 3 = 3,072). Consequently, an internal fragmentation problem occurs in which a free space of 924B (1,024-100) remains in the fourth page frame.

### Segmentation

As in paging, logical and physical memory are not divided into blocks of the same size, but into segments, which are logical units of different sizes.
User specifies with two addresses (segment number + displacement)
The segment table stores the reference (segment's starting physical address) and limit (segment length) of each segment.

- Disadvantages: If segments of different sizes are repeatedly loaded and removed from memory, the free space may be divided into a large number of small pieces and become unusable (external fragmentation).

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

---

## Virtual memory

In order to realize multiple programming, many processes must be placed in memory at the same time. Virtual memory is a technique that enables execution even if the entire process is not in memory, and has the main advantage that the program can be larger than the physical memory.

### Virtual memory development background

**All of the code to be executed has to exist in physical memory**, and programs larger than the memory capacity cannot be executed. Performance issues arise.
Also, since you can check the memory occupied by code that is used only occasionally, you can see that the entire program does not need to be loaded into memory unnecessarily.

#### If only part of the program can be loaded into memory...

- You are not limited by the physical memory size.
- You can run more programs at the same time. Accordingly, `response time` is maintained, and `CPU utilization` and `processing rate` increase.
- Since the I/O required for `swap` is reduced, programs run faster.

### What Virtual Memory Does

Virtual memory can be organized as a separate concept of the actual physical memory and the user's logical memory. This makes it possible to provide any number of large `virtual address spaces` to the programmer with small memory.

#### Virtual address space

- It is a space that implements the logical appearance of a process stored in memory in virtual memory.
  By providing the memory space required by the process in the virtual memory, physical memory can be saved by not loading the memory space that is not currently directly needed in the physical memory.
- For example, suppose a program is executed and 100KB of logical memory is required.
  However, if the sum of the memory space required until execution is 40KB (Heap area, Stack area, code, data), then only 40KB is stored in the physical memory, and the remaining 60KB can be understood as being requested from the physical memory when necessary.

| `Stack` | &nbsp;&nbsp;&nbsp; free (60KB) &nbsp;&nbsp;&nbsp;&nbsp; | `Heap` | `Data` | `Code` |
| ------- | ------------------------------------------------------- | :----: | ------ | ------ |

#### Page sharing between processes

Virtual memory is...

- Allows `system library' to be shared among multiple processes. Each process recognizes that it uses a `shared library`in its own virtual address space, but the`physical memory pages` containing the library are shared by all processes.
- Enables processes to share memory, and processes can communicate via shared memory.
  Again, each process perceives as its own address space, but the actual physical memory is shared.
- It enables pages to be shared during process creation through `fork()`.

### Demand Paging

Instead of loading the entire program from disk into physical memory at the beginning of program execution, a strategy that loads only what is initially needed is called'request paging', and is widely used in virtual memory systems. And virtual memory is usually managed as `pages`.
In virtual memory using demand paging, pages are loaded as needed during execution. **Pages that have never been accessed are not loaded into physical memory.**

Individual pages in the process are managed by `pager`. The pager reads only the pages actually needed to execute the process into memory, thus reducing the waste of time and memory waste of getting pages that will not be used.\*\*

#### Page fault trap

### page replacement

As mentioned in `request paging`, all items are not loaded into the physical memory when the program is executed, so if a `page fault' occurs in the process of requesting a page required for the operation of the process, the desired page is It is taken from the auxiliary storage device. However, if all of the physical memory is in use, a page replacement must be done (or there is a way for the operating system to kill the process forcibly).

#### Basic method

This is the flow of memory replacement when all of the physical memory is in use.

1. Locate the required page on disk
2. Find the blank page frame.
   1. Choose the page to be victimized through the `page replacement algorithm`.
   2. Write the page to be sacrificed to disk and modify the related page table.
3. A new page is read into the frame in the newly emptied page table, and the frame table is modified.
4. Restart user process

#### page replacement algorithm

##### FIFO page replacement

As the simplest page replacement algorithm, it has a flow of first-in first-out (FIFO). In other words, it goes out first at the time of page replacement in the order of the pages first entered into the physical memory.

- Advantages

  - Easy to understand and easy to program.

- Disadvantages
  - Old pages may not always contain unnecessary information (initial variables, etc.)
  - By replacing the pages that are actively used from the beginning, it may cause the side effect of increasing the page absent rate.
  - `Belady's Contradiction`: There is a contradiction in which more page faults occur because the number of page frames that can store pages can be increased.

##### Optimal Page Replacement

After confirming the `Belady's contradiction`, the search for the optimal replacement algorithm was proceeded, and the page failure rate was lower than that of all algorithms, and `Belady's contradiction` did not occur. The key to this algorithm is to'find and replace pages that will not be used for the longest in the future'.
It is mainly used for comparative research purposes.

- Advantages

  - It guarantees the lowest page failure rate among algorithms.

- Disadvantages
  - There is a difficulty in implementation. This is because there is no way to know in advance the plan of memory references for all processes.

##### LRU Page Replacement

`LRU: Least-Recently-Used`
As an approximation algorithm of the optimal algorithm, the page that has not been used for the longest is selected and replaced.

- Characteristic
  - In general, it is better than the `FIFO algorithm` and less than the `OPT algorithm`.

##### LFU Page Replacement

`LFU: Least Frequently Used`
This is how to replace the page with the least number of references. It is an algorithm created under the assumption that a page that is actively used will have a large number of references.

- Characteristic
  - If a process uses a specific page intensively or uses other functions, it may stay in memory even if it is no longer used, which may lead to a point in which the initial assumptions are broken.
  - It is not used well because it does not approximate the optimal (OPT) page replacement properly.

##### MFU Page Replacement

`MFU: Most Frequently Used`
It is based on the assumption that the page with the lowest reference count was recently loaded into memory and will continue to be used in the future.

- Characteristic
  - It is not used well because it does not approximate optimal (OPT) page replacement properly.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)

---

## Locality of cache

### Cache locality principle

The cache memory is a general-purpose memory to reduce bottlenecks caused by a speed difference between a fast device and a slow device. To play this role, it is necessary to be able to predict to some extent what data the CPU will want. This is because the performance of the cache depends on how much useful information the CPU will refer to later in the small cache memory.

At this time, in order to maximize the `hit rate`, the data `principle of locality` is used. As a prerequisite for locality, the program is based on the characteristic that all codes or data are not accessed evenly. In other words,'Locality' refers to a characteristic of intensively referencing a specific part at a moment, rather than uniformly accessing information in the memory device.

This data locality is typically divided into Temporal Locality and Spatial Locality.

- Time locality: The content of the address that was recently referenced is a characteristic that will be referenced again soon.
- Spatial locality: The characteristic that the contents of the address adjacent to the address referenced by most real programs are re-referenced

</br>

### Caching line

As mentioned, a cache is a place where frequently used data is stored close to the processor. However, no matter how close the cache is, it will take a long time if you have to traverse all the data because you don't know where the data you are looking for is stored. In other words, if the target data is stored in the cache, the cache becomes meaningful only if it can be accessed and printed immediately.

Therefore, when data is stored in the cache, it is stored in a `bundle` using a specific data structure, which is called **caching line**. Because the process uses data in various addresses, the addresses of frequently used data are also scattered. Therefore, it is necessary to attach a tag in which the memory address of the data is recorded on the data stored in the cache. These tags are called caching lines, and when they are fetched from memory, they are fetched based on the caching line.
There are three representative types.

1.  Full Associative
2.  Set Associative
3.  Direct Map

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)



## Interview Questions for OS

### Linux

* [10 Job Interview Questions for Linux System Administrators from Linux.com](https://www.linuxfoundation.org/blog/2015/07/10-job-interview-questions-for-linux-system-administrators/)
* [10 Useful Random Linux Interview Questions and Answers](http://www.tecmint.com/useful-random-linux-interview-questions-and-answers/)
* [11 Basic Linux Interview Questions and Answers](http://www.tecmint.com/basic-linux-interview-questions-and-answers/)
* [11 Essential Linux Interview Questions from Toptal](http://www.toptal.com/linux/interview-questions)
* [Some basic Linux questions from ComputerNetworkingNotes.com](http://computernetworkingnotes.com/rhce-interview-questions/linux-interview-questions-answers.html)
* [Top 30 Linux System Admin Interview Questions & Answers](http://www.linuxtechi.com/experience-linux-admin-interview-questions/)
* [Top 50 Linux Interview Questions from Career Guru](http://career.guru99.com/top-50-linux-interview-questions/)
* [Linux System Administrator/DevOps Interview Questions](https://github.com/chassing/linux-sysadmin-interview-questions)
* [278 Test Questions and Answers for \*nix System Administrators](https://github.com/trimstray/test-your-sysadmin-skills)
* [Linux Interview Questions - Quick Refresher](https://www.techbeamers.com/essential-linux-questions-answers/)

### Windows

* [Top 10 Interview Questions for Windows Administrators](http://www.brentozar.com/archive/2009/07/top-10-interview-questions-for-windows-sysadmins/)
* [Top 22 Windows Server Interview Questions from Career Guru](http://career.guru99.com/top-22-windows-server-interview-questions/)
* [Windows Admin Interview Questions & Answers](http://www.01world.in/p/windows.html)


</br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#OS)
---

</br>

_OS.end_
