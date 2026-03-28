# Development Log

## Instructions
Document your development process as you work on the assignment. Add entries showing:
- What you worked on
- Problems you encountered
- How you solved them
- Time spent

**Requirements**: Minimum 5 entries showing progression over time.

---

## Example Entry Format:

### Entry 1 - [April 1, 2026, 2:30 PM]
**What I did**: Forked the repository and set up my student ID

**Details**: 
- Created GitHub account with university email
- Forked the starter repository
- Changed student ID on line 92 to my actual ID (441234567)
- Compiled and ran the program successfully

**Challenges**: Had to install JDK first because javac wasn't recognized

**Solution**: Downloaded JDK 17 from Oracle website and set PATH variable

**Time spent**: 30 minutes

---

## Your Development Log:

Entry 1 - [March 27, 2026, 10:00 AM]
What I did: Forked the repository and set up my student ID
Details:

Created GitHub account with university email
Forked the starter repository from the professor's link
Renamed the repository to OS-Assignment1-Faisal-Aloqaily
Changed student ID on line 92 to 444050127
Ran the program for the first time and checked the output

Challenges: The program didn't run at first because VS Code couldn't find Java
Solution: Installed Java Extension Pack in VS Code and it worked after that
Time spent: 45 minutes

---

Entry 2 - [March 27, 2026, 2:00 PM]
What I did: Read and understood the starter code
Details:

Read through Process class and understood how run() works
Traced through the scheduler loop manually
Matched the code with the output to understand the flow
Read about Round-Robin scheduling in the textbook

Challenges: I didn't understand why a new Thread is created every time a process re-enters the queue
Solution: After reading more I realized a terminated thread cannot be restarted, so a new one must always be created
Time spent: 3 hours
---

Entry 3 - [March 27, 2026, 5:00 PM]
What I did: Implemented Feature 1 - Process Priority
Details:

Added priority field to Process class
Updated constructor to accept priority parameter
Added getPriority() getter method
Generated random priority (1-5) for each process in main()
Updated addProcessToQueue() to display priority in output

Challenges: Got a compile error because I forgot to update the constructor call in main()
Solution: Found the new Process(...) line in main() and added the priority argument
Time spent: 2 hours

---

Entry 4 - [March 28, 2026, 11:00 AM]
What I did: Implemented Feature 2 and Feature 3
Details:

Added contextSwitches counter and incremented it before each start()
Added creationTime and waitingTime fields to Process class
Added startWaiting() and stopWaiting() methods
Called stopWaiting() at the beginning of run()
Called startWaiting() when process is re-enqueued
Added waiting time summary printout at the end

Challenges: Feature 3 was confusing — I wasn't sure when exactly to call startWaiting() and stopWaiting()
Solution: Traced P1's journey manually on paper and figured out the exact moments to call each method
Time spent: 3 hours
---

Entry 5 - [March 28, 2026, 4:00 PM]
What I did: Final testing and documentation
Details:

Ran the full program and checked all 3 features work correctly
Verified context switches count matches the output
Checked waiting times make sense for each process
Completed ANSWERS.md and REFLECTION.md
Made sure all commits are pushed to GitHub

Challenges: Some processes showed 0ms waiting time which I thought was wrong
Solution: Realized it's correct — processes like P4 and P8 finished in their first quantum so they never waited in the queue again
Time spent: 3 hours



---

### Entry 6 - [Optional - Date and Time]
**What I did**: 

**Details**: 

**Challenges**: 

**Solution**: 

**Time spent**: 

---

## Summary

Total time spent on assignment: 4 days
Most challenging part: Feature 3 — figuring out exactly when to call startWaiting() and stopWaiting() to get accurate waiting times for each process
Most interesting learning: That a terminated thread can never be restarted — I never knew this before and it completely changed how I understood the code structure
What I would do differently next time: Start earlier and read the full code before touching anything, instead of jumping into adding features without fully understanding the existing logic first and loging with uni email first
