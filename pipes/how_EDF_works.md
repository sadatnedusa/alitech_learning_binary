# How EDF works

- **Earliest Deadline First (EDF)** is a **dynamic scheduling algorithm** used primarily in **real-time systems** where tasks are assigned deadlines.
- In EDF, the task with the **earliest deadline** is always given the highest priority for CPU execution.
- The idea is that the task which is closest to its deadline is the most urgent and should be executed first to avoid missing the deadline.

### Key Concepts of EDF Scheduling:

1. **Dynamic Priority**: 
   - EDF is a dynamic scheduling algorithm, meaning that the priority of tasks can change during the system's execution. As new tasks arrive or existing tasks approach their deadlines, their priorities are re-evaluated.
   
2. **Earliest Deadline Priority**: 
   - The task with the **earliest absolute deadline** is given the highest priority. This means that as soon as a new task with an earlier deadline than the currently running task arrives, the system will preempt the current task and switch to the new one.

3. **Preemptive or Non-preemptive**: 
   - EDF can be implemented as either **preemptive** or **non-preemptive**. In a **preemptive system**, the current running task can be interrupted if a new task with an earlier deadline arrives. In a **non-preemptive system**, once a task starts executing, it will complete before the CPU is reassigned to another task.

4. **Real-time Guarantee**: 
   - If tasks are **schedulable** under EDF (i.e., there’s enough CPU time to complete all tasks before their deadlines), EDF guarantees that all tasks will meet their deadlines. This is an important feature for **hard real-time systems** where missing a deadline can lead to system failure.

### How EDF Scheduling Works:

#### Basic EDF Algorithm Steps:

1. **Task Arrival**:
   - Tasks are added to a queue, and each task has an associated **deadline** (i.e., a time by which the task must finish execution).
   
2. **Task Scheduling**:
   - The CPU always selects the task with the **earliest deadline** to execute. The deadlines are compared, and the task with the closest deadline is given the CPU.

3. **Task Execution**:
   - The selected task executes until it either completes or gets preempted by a newly arrived task with an earlier deadline.
   
4. **Preemption (in Preemptive EDF)**:
   - If a new task arrives while the CPU is executing a task, and this new task has an earlier deadline than the running task, the current task is preempted, and the new task takes over the CPU.

5. **Completion**:
   - Once a task completes, it is removed from the system. The scheduler then looks for the next task with the earliest deadline.

#### Example of EDF Scheduling:

Consider the following tasks with deadlines and burst times (execution times):

| Task | Burst Time | Deadline |
|------|------------|----------|
| A    | 2 units    | 5 units  |
| B    | 1 unit     | 3 units  |
| C    | 4 units    | 6 units  |

- At **time 0**, all tasks arrive.
- **Task B** has the earliest deadline (3 units), so it is scheduled first.
- After 1 unit of time, **Task B** completes, and now **Task A** has the earliest deadline (5 units), so it is scheduled next.
- After 2 units of time, **Task A** completes, and finally, **Task C** is scheduled and completes after 4 units.

The execution order will be: **B → A → C**.

### Key Points of EDF:

1. **Dynamic Scheduling**:
   - Unlike static scheduling algorithms like **Rate Monotonic Scheduling (RMS)**, EDF dynamically adjusts task priorities based on their deadlines, making it more flexible for handling real-time workloads.

2. **Utilization Efficiency**:
   - EDF is **optimal** for **uniprocessor systems** in the sense that if a set of tasks is **feasible** (i.e., can be completed within their deadlines), EDF will find a valid schedule that ensures all tasks meet their deadlines. In fact, EDF can achieve **100% CPU utilization** if tasks are scheduled appropriately.

3. **Preemption Cost**:
   - In preemptive systems, there is a cost associated with preempting tasks (due to context switching). Frequent preemptions can introduce **overhead** that might affect overall system performance, particularly in systems with many tasks.

4. **Overload Handling**:
   - In situations where the system is **overloaded** (i.e., not all tasks can meet their deadlines due to excessive CPU demand), EDF does not handle task deadlines gracefully. In overload conditions, EDF can lead to **deadline misses**, and in some cases, the most critical tasks might miss their deadlines.

### Advantages of EDF:

1. **Optimal for Uniprocessor Systems**:
   - EDF is optimal for scheduling in uniprocessor systems, meaning that if a feasible schedule exists, EDF will ensure all tasks meet their deadlines.

2. **Dynamic Adjustment**:
   - EDF dynamically changes the priority based on task deadlines, making it more flexible than static priority algorithms.

3. **Maximizes CPU Utilization**:
   - Under EDF, CPU utilization can reach up to **100%** for schedulable task sets, maximizing resource usage.

4. **Simple Deadline-Based Scheduling**:
   - EDF works purely based on deadlines, which makes it straightforward to determine which task should run next.

### Disadvantages of EDF:

1. **High Preemption Overhead**:
   - In preemptive EDF, if many tasks arrive with close deadlines, frequent preemptions can occur, leading to high overhead from context switching.

2. **Poor Performance in Overloaded Systems**:
   - In overloaded systems where not all tasks can meet their deadlines, EDF may miss multiple deadlines unpredictably, which can be problematic for critical real-time tasks.

3. **Complexity in Multiprocessor Systems**:
   - EDF is optimal for uniprocessor systems, but it can be challenging to implement efficiently in **multiprocessor systems** due to the need for global coordination between processors.

### Example of Preemptive EDF Scheduling:

Let’s say we have three tasks with the following deadlines and burst times:

| Task | Burst Time | Deadline |
|------|------------|----------|
| A    | 4 units    | 7 units  |
| B    | 2 units    | 4 units  |
| C    | 1 unit     | 2 units  |

1. At **time 0**, all three tasks arrive.
2. **Task C** has the earliest deadline (2 units), so it starts executing.
3. After **1 unit** of execution
