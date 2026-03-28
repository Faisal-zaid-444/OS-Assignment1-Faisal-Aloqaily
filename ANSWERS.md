# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:** A thread operates inside a process and shares memory with other threads, whereas a process is an independent program with its own memory. We used threads in this project since they all needed to use the same processQueue and processMap, which is made simple by threads' automated memory sharing. Additionally, starting a new thread is far less expensive and faster than starting a whole process. Sharing the queue would be extremely difficult if we employed different processes.

[Write your answer here. Consider: What is a process? What is a thread? How do they differ in terms of memory, resources, creation overhead? Why are threads more suitable for this simulation?]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:** When a process doesn't finish within its time quantum, it goes back to the end of the ready queue and waits for all other processes to take their turn first. Here is an example from my output:


[Write your answer here. Describe the specific behavior - where does the process go? When does it run again? Give an example from your actual program output showing a process that was re-queued.]

Example from my output:
▶ P1 executing quantum [4000ms]
⏸ P1 completed quantum 4000ms │ Overall progress: [████████████░░░░░░░░] 62%
   Remaining time: 2431ms
↻ P1 yields CPU for context switch

➕ P1 (Priority: 3) enters the ready queue │ Burst time: 6431ms
│ [P3 → P4 → P5 → P6 → P7 → P8 → P9 → P10 → P11 → P12 → P13 → P14 → P15 → P16 → P17 → P1]

**Explanation of example:**
[Explain what's happening in the output snippet you pasted]
the time quantum is just 4000 ms, P1 had a burst time of 6431 ms. It had 2431 ms left after running for 4000 ms, so it gave up the CPU and moved back to the back of the queue behind 15 other processes. Before it could run again, it had to wait for each of them to get a turn.
---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**

[Write your answer here. For each state, explain when P1 enters that state during the simulation. Use your understanding of the code to trace through the lifecycle.]

New: P1 enters New state when new Thread(process) is called inside addProcessToQueue() at the beginning of the simulation, before the scheduler starts.
Runnable: P1 becomes Runnable when currentThread.start() is called in the scheduler loop. At this point P1 is ready but waiting for the CPU to pick it.
Running: P1 enters Running when the JVM actually executes its run() method. In the output this is when we see ▶ P1 executing quantum [4000ms].
Waiting: P1 enters Waiting during Thread.sleep(stepTime) inside run() while showing the progress bar. Also the main thread waits for P1 during currentThread.join().
Terminated: P1 reaches Terminated when run() finishes. In the output this is when we see ✓ P1 finished execution! at remaining time 0ms. After this a new thread must be created if P1 needs to run again.

---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: Online Gaming Server

**Description**: 
Description: When multiple players are connected to the same game server, each player's actions are handled by a separate thread. For example in a multiplayer game, player movement, shooting, and chat messages all need to be processed at the same time.

**Why Round-Robin works well here**: 
Why Round-Robin works well here: Every player deserves equal response time — if one player's thread took all the CPU time, other players would experience lag. Round-Robin gives each player's thread a fair time quantum so the game feels smooth and responsive for everyone, just like how our simulation gave every process a fair turn in the queue.

### Example 2: University Registration System

**Description**: 
Description: During registration period, hundreds of students try to register for courses at the same time. Each student's request runs on a separate thread in the server.

**Why Round-Robin works well here**: 
Why Round-Robin works well here: It would be unfair if one student's request blocked everyone else. Round-Robin ensures every student gets CPU time equally so no one is stuck waiting too long. This is exactly like our simulation — even P11 which had the longest burst time (8951ms) still had to share the CPU fairly with all other processes.

---

## Summary

**Key concepts I understood through these questions:**
1. Threads share memory which makes it easy to share data like the ready queue between them
2. Round-Robin prevents any single process from monopolizing the CPU
3. Every process goes through the same thread lifecycle from New to Terminated

**Concepts I need to study more:**
1.What happens when two threads try to modify the same variable at the same time 
2. How to choose the right time quantum size for different apps
