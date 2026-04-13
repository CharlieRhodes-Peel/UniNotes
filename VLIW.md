# Summary
**V**ery **L**ong **I**nstruction **W**ord (**VLIW**) where each instruction  (is very big and) specify's multiple operations, multiple individual registers are read and written. (See [[SIMD]] for a comparison between it and VLIW). Its only really used for special purpose processors, not general-purpose machines, so is good as a completely custom [[ISA]] and architecture.

The advantage with VLIW is that many combinations are possible, as each ALU (see diagram below) can be controlled independently. You need a lot of bits per instruction and lots of multiplexers (examples in [[Control Signals]] and [[Data Paths]]), so you do need a significant amount of area for routing.
## Diagram:
Here we see many independent [[ALU]]s, there is still one register file (containing all the registers) the instructions just is very big
![[Pasted image 20260310135734.png]]

# Examples of systems
VLIW systems need to be VLIW from the start. You can't easily "extend" an existing [[ISA]] (unlike [[SIMD]] with [[SSE]] and other extensions). Though we don't see these anymore as a general-purpose, desktop like PC, it was tried with Itanium but it ultimately failed and we don't see it.

There were many attempts at general-purpose VLIW [[ISA]]s
- Heavy academic research into [[ISA]]s, architectures, and compilers
- HP was a big proponent through the PA-RISC [[ISA]] and [[CPU]]s
There are ~2 general-purpose VLIW [[ISA]]s + architectures
1. IA-64 + Itanium : Intel's attempt to move beyond (32-bit) x86
2. Elbrus 2000 : A Russian processor family I know nothing about
There are many special-purpose VLIW ISAs + archs
- Your phone probably has one in it
- Your [[GPU]] may be VLIW

## AMDs XDNA AI Engines
**DISCLAIMER** you aren't really expected to remember how this works or anything just generally it's use case
- It's architecture is optimised for AI and DSP
- It's now being used (VLIW) for Ryzen AI
- They are *efficent* special purpose CPU
### So what is an AI engine?
- Multi-core with 2d-mesh topology
The CPUs are:
- VLIW
- [[SIMD]] (but weird)
- In-order and [[Pipelining]]ed (but weird)
- Hazards, scheduling, and forwarding all handled by the **compiler** instead !
The Memory Hierarchy is **explicitly** managed
- Explicit movement of data between [[Cache]] and [[RAM]]
- Explicit movement of data between [[Cache]]s for communication (between CPU, sorta like multi-core communication)

They know that alot of their operations are going to be working with vectors, because AI is all just linear algebra anyways. So they 128-bit, 256-bit, 512-bit and even in some cases 1024-bit registers!!! That's huge!!

| Pros                                    | Cons                                                              |
| --------------------------------------- | ----------------------------------------------------------------- |
| Area efficiency is good                 | Complex and specialised, not a general purpose solution           |
| Power efficiency is good                | Difficult to program: kernel design + data movement + parallelism |
| High achieved / theoretical performance | No code protability: even XDNA -> XDNA2 requires a redesign       |










