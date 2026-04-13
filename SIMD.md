# Summary
**S**ingle **I**nstruction **M**ultiple **D**ata (**SIMD**) is doing the same thing, to many data objects. You need special hardware on the [[CPU]] for it. It's covered very briefly in [[SSE]]. And along with the special hardware needed for it, the **software** needs to be compiled in a way to take advantage of this. (see [[Parallel Systems]] for more related). Another way to achieve a similar result is [[VLIW]]

## Diagram
On the left we see a standard [[MIMD]] layout of things where as the right shows [[SIMD]]
![[Pasted image 20260310133728.png]]

# X86 ([[SSE]])
X86 being a [[CISC]] architecture can do this kinda stuff (with [[SSE]]). You need some extensions in C (for example) for it to work.

# Closer look at ALU architecture
Each [[Data Paths]] (lane) is isolated from the other. So there is **ONE** set of [[Register]]s for each SIMD lane. And there is **ONE** [[ALU]] for calculation in each lane.
![[Pasted image 20260310140335.png]]
(see [[VLIW]] to see how this differs from it)


# SIMD vs [[VLIW]]

|      | Pros                                                                                                                                      | Cons                                                       |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| SIMD | Small instructions, simple architectures. Works well with vector style calculations                                                       | restricted, only works well with vector stuff              |
| VLIW | It's flexible, a somewhat simple architecture. Captures irregular loops well. Compilers can identify parallel operations over long ranges | The instructions are really big. Need more decode overhead |
