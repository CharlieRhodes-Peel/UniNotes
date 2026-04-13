This just covers the lecture going over the coursework, hopefully I can refactor things put here. But for now they have no place to go, so they are going here

# Admin Stuff
Is due **19th March**

# Notes:
- Program should be statically linked (pass ```-static``` to gcc)

# Why are we doing this?
Looking at ways to make things "better"; such as looking at the [[Instruction]]s-per-second, [[Instruction]]s-per-cycle, how the [[ISA]] plays into all of it, etc...

# Methods of Simulation
The list below goes down in granularity, so the bottom is the most low level method of simulation

- Thinking about it
- [[ISA]] level thinking
- Event-driven      - *Gem 5 is somewhere between here*
- Transaction-level - *and here*
- Gate level 
- Profiling
- ...

# What types of Q's come up in an Exam?

- "What happens if we move from a 5-stage to a 7-stage pipeline"
- "Why is my program half the speed on Apple-M3 vs AMD-Epyc4?"
- "Which branch prediction policy is best for my workload?"
- "If I re-structure this algorithm, is it faster?"
- "Should I put bigger caches into my SoC? (System-On-a-Chip)"
- "How much does new instruction X improve performance?"

# High-level Features
###### Configurable [[CPU]] models
- Simple one-IPC (SimpleAtomic/Timing)
- Detailed in-order execution (InOrder)
- Detailed out-of-order execution (O3)
- Hardware-accelerated fast forwarding (KVM)
###### Pluggable memory system
- Stitch memory system together out of components (caches, DDR)
- Use Wisconsin's Ruby to model multi-core coherency protocols
###### Boot real [[Operating Systems]]
- Linux, Android
###### Many [[ISA]]s
- X86-64, ARM, [[MIPS]], RISC-V
