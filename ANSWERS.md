# Lab 07 Analysis Questions

1. Compare the results with time quantum 3 and time quantum 5. Which quantum gave better average waiting time? Why?

Both came out to 6.67ms for me which surprised me. The averages are the same but the individual waits are different. With quantum 5 P3 has to wait a lot longer since P1 takes a bigger chunk first. So I guess they balance out with these burst times.

2. What would happen if the time quantum was 1ms? Would the system be more or less efficient?

It would feel really responsive but be less efficient. Every switch costs time and with a 1ms quantum you'd be switching constantly. So a lot of CPU time goes to switching instead of actual work.

3. What would happen if the time quantum was 20ms (larger than any process burst time)? How would Round Robin behave then?

It would just turn into FCFS. No process ever runs out its quantum so each one runs to the end before the next one starts. P1 runs 0-7, P2 runs 7-11, P3 runs 11-13.

4. In the simulation with quantum 3, how many context switches occurred? Count each time a process was removed from the queue.

6 total. I traced it:
- P1 at time 0
- P2 at time 3
- P3 at time 6 (done at 8)
- P1 at time 8
- P2 at time 11 (done at 12)
- P1 at time 12 (done at 13)

5. Why does Round Robin prevent the convoy effect that occurs in FCFS scheduling?

Because no process can hog the CPU. After one quantum it gets kicked to the back of the line. So short jobs don't get stuck waiting forever behind a long one like they do in FCFS.
