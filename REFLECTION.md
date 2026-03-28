# Reflection Questions

## Instructions
Answer the following questions about your learning experience. Each answer should be **at least 5-7 sentences** and show your understanding.

---

## Question 1: What did you learn about multithreading?

**Your Answer:** I had no idea what threads were or how they operated prior to this project. I discovered that a thread is formed using new Thread(process) and only begins to execute when you call start() after working with the code. The fact that a thread cannot be restarted once it has finished surprised me the most. For this reason, addProcessToQueue() always creates a new thread each time a process re-enters the queue. I also discovered that we can imitate CPU execution time and Thread by using Thread.sleep().Before proceeding to the next process, join() compels the main thread to wait for the current one to complete. The entire scheduler would fail without join() because the processes would execute out of sequence.

[Write your answer here. Discuss specific concepts like thread creation, thread states, how threads execute concurrently, what surprised you, etc.]

---

## Question 2: What was the most challenging part of this assignment?

**Your Answer:** Implementing Feature 3—tracking the waiting time—was the hardest part for me. I had to determine precisely when to start and end the timer because the identical Process object is reused every cycle. I didn't realize that waiting time should only be recorded when the process is in the queue and not while it is operating, thus at first I wasn't sure where to execute startWaiting() and stopWaiting(). The process object is always present, but it is only "waiting" at certain times, which made this unclear.

[Describe the specific challenge. Was it understanding the code? Implementing a feature? Using Git? Explain what made it difficult and how it relates to the course concepts.]

---

## Question 3: How did you overcome the challenges you faced?

**Your Answer:** Tracing through the code by hand and going step-by-step through one procedure (P1) was what really helped me. I created a straightforward timeline that shows when P1 joins the queue, begins operating, returns to the queue, and so on. This demonstrated that startWaiting() should be called immediately before addProcessToQueue() when the process is re-enqueued, and stopWaiting() should be called at the start of run() when the process begins to execute. In order to test that the waiting times made sense, I also ran the code several times and examined the results. Processes that completed in a single round, such as P4, displayed 0 ms waiting, indicating that the logic was sound.

[Describe your problem-solving approach. Did you read documentation? Ask for help? Debug systematically? What resources did you use? What strategies worked?]

---

## Question 4: How can you apply multithreading concepts in real-world applications?

**Your Answer:** a web browser such as Chrome. Because each tab operates on its own thread when you open multiple tabs, one tab may crash or load slowly without impacting the others. HungerStation, a meal delivery service, is another example. Each order is managed by a different thread when multiple users make orders simultaneously, saving customers from having to wait for another customer's order to be processed before theirs.Every process in the ready queue is a customer, and the time quantum guarantees that no customer has to wait too long. The application waits for each order to be confirmed before proceeding to the next phase, just as Thread.join() causes the scheduler to wait for the current process to complete its quantum.

[Give specific examples from real applications you use (web browsers, games, mobile apps, etc.). Explain why threads are useful in those scenarios. Connect to what you learned in this assignment.]

---

## Additional Reflections (Optional)

### What would you like to learn more about?

[Any topics related to threading, concurrency, or operating systems that you're curious about?]

---

### How confident do you feel about multithreading concepts now?

[Rate yourself and explain: Beginner / Intermediate / Confident]

[Explain your rating - what do you understand well? What needs more practice?]

I consider myself to be a Beginner. I had no idea how Java threads operated before this assignment, but now I know the fundamentals, such as using new Thread() to create threads, start() to start them, and join() to wait for them. I also understand the lifecycle of a thread and the reason it cannot be restarted once it is finished. Thread synchronization, such as what occurs when two threads attempt to change the same variable at the same time, is something I still need to work on. To fully understand the idea, I believe I need to work on more examples.
---

### Feedback on the assignment

This assignment was really helpful to me since it made the connection between theory from the lectures and real running code. It was much simpler to see how programs vie for CPU time when you saw the Round-Robin algorithm operating in real time with the colored output. Feature 3 was the most difficult aspect of the task, although it was still manageable. In order to make it easier for beginners to fully understand the code structure before making changes, I suggest that a smaller starting example be given before diving into the complete exercise.

[Any comments about the assignment? Was it helpful? Too easy/hard? Suggestions for improvement?]
