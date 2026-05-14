# Mechanism for Routing
- **Baked into router logic** simple arithmetic using positional co-ordinates, or more complicated adaptive routing
	- i.e you calculate based on the way the packet is formatted
- **Source IP drives it** The source IP includes routing information for each [[switch]] in the packet. Simple (small) [[Switch]]es, but packet *header* size increases
- **Look-up table** Each [[Switch]] has a (programmable) cheatsheat. Opposite trade-offs to the above
Modern day routing mechanism use a hybrid of all of these ideas
# Routing Algorithms
## Fixed oblivious - always routed the same
### Dimension-Ordered Routing
- Traverse each dimension in sequence 
	- where a dimension is a set of links that connect nodes along a particular direction. Nodes in the same "row" along a dimension are directly connected in that direction only
	- $\therefore$ A simple **ring** or **bus** chain (see [[Topology]]) would be 1D while a **mesh** would be 2D (again see [[Topology]])

| Pros                                 | Cons                              |
| ------------------------------------ | --------------------------------- |
| Simple switches, it's all arithmetic | Can fall into congestion hotspots |
|                                      | Doesn't adapt to failure well     |

#### Diagram
Imagine a 3x3 mesh with the following nodes
![[Pasted image 20260514130644.png]]
Lets say the source is at node 1 and the destination is at source 9.

If we do **XY** routing. That is, going in the X *then* the Y dimension. The order of nodes the packet would travel in would be 1 -> 2 -> 3 -> 6 -> 9



## Stochastic oblivious - has some injected randomness into routing
### Valiant Routing
Using a random waypoint node to route to. Is generally used as a network **load balancing** tool
- Can be combined with deterministic routing to level out network load
	- Works best with a network is (unevenly) loaded
- Restrict waypoint selection to trade off balancing with latency e.g only a few hops away from dst

| Pros                            | Cons                          |
| ------------------------------- | ----------------------------- |
| Balances an uneven network load | Increases latency (more hops) |

#### Diagram
![[Pasted image 20260514131050.png]]
## Adaptive Routing - may change based on network state
Adapts to traffic and routes around it. However, you have to dictate 1. How re-routes are done, i.e which direction to go in and 2. Need to keep track of network congestion at each switch

| Pros                            | Cons                                                                                            |
| ------------------------------- | ----------------------------------------------------------------------------------------------- |
| Routes well around failed nodes | Requires routers to communicate congestion with each other: greater router complexity therefore |
| Better network load balancing   | Have to be keenly away of *livelock*                                                            |

### Diagram
In the below diagram, The **third** edge in the path is congested, so it finds another way around
![[Pasted image 20260514131445.png]]
# Deadlock
###### meme
![[Pasted image 20260514131815.png]]

## What is it?
Circular dependencies... where each packet is waiting for a buffer
## Dealing with deadlock (generally)
- **Detect and break at runtime** Heavy handed, always works, but increases router complexity
- **Escape paths** More buffers requires more space... what happens when the escape paths get blocked?
- **In the routing algorithm** Usually the best idea. e.g: in 2D, forbid three of eight turns guarantee avoiding deadlock