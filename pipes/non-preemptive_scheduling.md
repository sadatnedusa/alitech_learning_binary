**Non-preemptive scheduling** is a type of CPU scheduling technique in which, once a process has been given the CPU, it continues to execute until it **completes** or **voluntarily yields** the CPU (such as when waiting for input/output operations). In this approach, the operating system does **not forcibly interrupt** or switch a running process to another one.

### Key Characteristics of Non-Preemptive Scheduling:
1. **No Process Interruption**:
   - Once a process starts execution, it cannot be interrupted by the operating system. The CPU is not reallocated to another process unless the current process finishes or goes into a waiting state (e.g., waiting for I/O).

2. **Simple Implementation**:
   - Since there is no need to frequently switch between processes, non-preemptive scheduling is simpler to implement compared to preemptive scheduling, which requires saving and restoring process states.

3. **Lower Overhead**:
   - Non-preemptive scheduling incurs less **context-switching overhead** because there are fewer switches between processes. This can be efficient for tasks where minimizing CPU overhead is important.

4. **Risk of Process Starvation**:
   - Long-running processes can monopolize the CPU, leading to poor responsiveness for other processes, especially if higher-priority or time-sensitive tasks are waiting in the queue.

5. **Limited Responsiveness**:
   - Non-preemptive scheduling is less suited for interactive or real-time systems where processes may need immediate attention. Lower-priority processes might wait a long time if a higher-priority process holds the CPU.

### How Non-Preemptive Scheduling Works:
1. **Process Arrival**:
   - When a process arrives in the ready queue, it is selected by the CPU scheduler based on a specific scheduling algorithm (e.g., First Come First Serve, Shortest Job First).
   
2. **Execution Until Completion or Blocked State**:
   - Once a process starts executing, it continues until one of two things happens:
     - The process **completes**.
     - The process enters a **blocked state** (e.g., waiting for I/O or other resources).
   
3. **CPU Reallocation**:
   - Only when the running process completes or blocks does the scheduler select another process to run. The OS does not forcefully take control of the CPU from the running process.

### Examples of Non-Preemptive Scheduling Algorithms:

1. **First Come First Serve (FCFS)**:
   - In this scheduling method, the CPU is allocated to processes in the order in which they arrive. Once a process is running, it will execute until completion.
   - Example: Imagine three processes A, B, and C arriving in that order. They will be executed one after the other, with A completing before B, and B completing before C, regardless of their burst time.
  
2. **Shortest Job First (SJF)**:
   - In this algorithm, the process with the **shortest CPU burst** time is selected to run first. Since it is non-preemptive, once a process starts executing, it will complete without interruption, even if a shorter process arrives later.
   - Example: If Process A has a burst time of 5 units, B has 3 units, and C has 2 units, the scheduler will first run the shortest one (C), followed by B, and then A.
  
3. **Priority Scheduling (Non-Preemptive)**:
   - In this algorithm, the CPU is assigned to the process with the **highest priority** (numerically lowest number in most systems). Once a process starts running, it continues until it either finishes or blocks. New processes with higher priority do not interrupt the currently running process.
   - Example: If Process A has priority 3, B has priority 1, and C has priority 2, Process B will be executed first, then Process C, and finally Process A.

### Advantages of Non-Preemptive Scheduling:
1. **Simple and Predictable**:
   - Non-preemptive scheduling is simple to implement and easier to reason about since processes always run to completion once they start.
   
2. **Less Overhead**:
   - Since processes are not interrupted, there is no need to save and restore the state frequently, which reduces **context-switching overhead**.

3. **Good for Batch Processing**:
   - It works well for **batch processing systems** where processes don’t need frequent interactions with the user or other processes. Long-running processes can complete without interruptions.

### Disadvantages of Non-Preemptive Scheduling:
1. **Poor Responsiveness**:
   - Non-preemptive scheduling is not suitable for interactive or real-time systems, as lower-priority processes or tasks might have to wait a long time before being executed.
   
2. **CPU Starvation**:
   - If a long-running process is scheduled, other processes may be starved of CPU time, leading to poor performance for other tasks.

3. **No Immediate Response for Higher Priority Tasks**:
   - Higher-priority processes that arrive while a lower-priority process is running will have to wait until the current process completes, which can cause delays in handling urgent tasks.

### Example Scenario of Non-Preemptive Scheduling:

Imagine three processes A, B, and C arrive at the same time, with burst times as follows:

| Process | Burst Time |
|---------|------------|
| A       | 5          |
| B       | 2          |
| C       | 8          |

If the system uses the **First Come First Serve (FCFS)** non-preemptive scheduling:

1. **Process A** starts first and runs for its entire burst time (5 units). 
2. After A finishes, **Process B** starts and runs for 2 units.
3. Finally, **Process C** starts and runs for 8 units.

Even if a shorter process or a more urgent process arrives after the current process starts, the OS will **not preempt** the running process, which can lead to inefficiency.

### Comparison to Preemptive Scheduling:
| **Aspect**                 | **Non-Preemptive Scheduling**                | **Preemptive Scheduling**                  |
|----------------------------|----------------------------------------------|--------------------------------------------|
| **Process Interruption**    | No interruption once the process starts.     | Processes can be interrupted and switched. |
| **Responsiveness**          | Low, since processes run to completion.      | High, because the OS can quickly switch to more urgent processes. |
| **Context Switching**       | Minimal, since there are fewer switches.     | Higher, due to frequent context switching. |
| **Overhead**                | Low, as no process states need to be saved.  | Higher, due to context switching overhead. |
| **Use Cases**               | Suitable for batch systems.                  | Suitable for interactive and real-time systems. |

---

### Points to Ponder:
**Non-preemptive scheduling** is a simpler and more predictable scheduling method, where processes are allowed to run until completion without being interrupted by the operating system.
This can be efficient for batch processing systems or environments where process interruptions are not needed. 
However, it lacks the flexibility and responsiveness required for real-time and interactive systems, where preemptive scheduling is generally preferred for better user experience and task management.
