# OS161-Priority-Based-CPU-Scheduler

This is a in-place modification of Harvard's OS161 CPU Scheduler to convert it to use priority based queues for responsive task scheduling. This completely replaces the round-robin scheduling algorithm with priorities assigned by thread behavior.

Threads begin at normal priority and are shifted up or down based on their usage of their alloted CPU time. I.e. if a thread enters sleeping or idling while it is alloted time on a core, it is shifted to a lower priorty. Conversely, if a thread spends all of the alloted time executing on said core, it is assumed to be a CPU-bound process, and its priority rises to high.

In doing so, processes that utilize the full CPU time are granted more chances to perform CPU-bound operations, instead of loading processes that trend towards blocking execution for I/O or other sleep inducing behaviors.

This is by no means a perfect solution, but rather a demonstration of possible performance gains through leveraging a CPU scheduler that is aware of process behavior.
