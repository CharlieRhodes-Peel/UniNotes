---
aliases:
  - Network On Chip
  - Network on Chip
  - Interconnect
---
# Summary
NoC or interconnects is something that connect "internal" components together. The complexity is usually found in the communication!

##### There are 3 core concepts to NoC
- **Topology** How are IPs and switches connected?
- **Routing** What path does one IPs message take to its destination? Who makes that decision?
- **Flow Control and Buffering**: What happens when the network is heavily loaded? What happens if there is simply no space to store a packet somewhere?

# High-Level Requirements
Interconnect design trade-offs:

Think about the good-time-cost triangle thingy or like the switch meme that can only be 2 at a time. It's like that for the following!

- **Performance** How well can your compute cores *communicate
- **Energy** communication is expensive and frequent
- **Scalability** How big can you go? How big do you *need* to go?
- **Reliability** Do you need reliable communication? There are situations where you don't actually need *EVERY* packet to be reliable

# Terminology
- **Switch/Routing Switch:** Connects inputs and output channel
	- ![[Pasted image 20260512142943.png]]
	- A diagram showing Channels connecting switches and IPs together
- **Channels** connect switches together
- **IP**: A component that is serviced by a switch:
	- Could be anything that sends traffic i.e: Compute cores, caches, memory units. gpus, i/o, etc...
- **Direct Node**: Switch with an IP attached to it
	- ![[Pasted image 20260512143323.png]]
	- Diagram showing a channel between two direct nodes
- **Indirect Node** A switch within a network, that doesn't have an attached component
- **Message** A "transfer unit", from the perspective of *IPs*
	- So like a ping to google.com
- **Packet** A "transfer unit", from the perspective of the *network* 
	- A message is made up of 1 or more packets
- **Flit** A "transfer unit", from the perspective of *switches* 
	- A packet is comprised of one or more **flits**

# Topology
How things are connected to other things

For the following topologies below. Realistically most systems **combine** aspects of all of these
## [[Bus]] 
Requires an arbiter sitting on the bus, controlling the communication pattern. IPs must request to send, reserving the bus.

Separate busses (hierarchical) for memory traffic (see [[Bus]] for more information on these things)

| Pros                                     | Cons                      |
| ---------------------------------------- | ------------------------- |
| Simple implementation and layout         | Arbitration scales poorly |
| Coherence implementations are well known | Easy to saturate          |
### Diagram
![[Pasted image 20260512144604.png]]

## Point-to-Point
When every node is connected directly to every other node.
- Almost no contention on the channels, Any contention is at the switch level
- Latency is quickest O($1$), it's hard to layout complex maps of switches, so any latency is a *distance* problem
- **Layout** like I said above is **hard**
- Scaling is **TERRIBLE** O($n^2$), every time you want to add a new switch have to connect every other switch to it
### Diagram
![[Pasted image 20260512145441.png]]

## Crossbar
One [[Bus]] per node

| Pros                                                                   | Cons                                                                                    |
| ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| Every node directly connected but uses less wiring than point-to-point | Still has O($n^2$) link scaling when compared to point-to-point                         |
| Concurrent transfers, depending on destination                         | Still has O(1) link but arbitration adds an additional scaling cost over point-to-point |
### Diagram
![[Pasted image 20260512145841.png]]

## Multistage Networks (Indirect)
Kind looks like a Neural Network to me
N = Number of IPs
R = Layers of switches

- Uses *R*-degree switches, depth of $\log_R(N)$ and a width of $N/R$
- Sizes scales with O($N \log_R(N)$), but latency scales with O($\log_R(N)$)

### Diagram
![[Pasted image 20260512150902.png]]

## Ring
Comparable to a [[Bus]] - higher bandwidth

| Pros                                                  | Cons                             |
| ----------------------------------------------------- | -------------------------------- |
| Size scales with O(N) just add one link for each node | Latency also scales with O(N) :( |
| Easy to build and lay out, Leads to simple switches!  |                                  |
### Diagram
![[Pasted image 20260512151226.png]]
### Addtionally; Hierarchical Rings
Lower latency but greater complexity.
Vary the number of "bridging switches" and hierarchy levels for an elastic trade off.
#### Diagram
![[Pasted image 20260512151303.png]]

## Trees
- Trees are useful for combinatorical tasks that split and split into task (or like recursion)
- Higher branches "thickened" to support dense traffic
- Latency scaling: O($log_R(N)$)  |  Node Scaling O(N)
### Diagrams
![[Pasted image 20260512151956.png]]

## Hypercubes (X-Dimensional Cubes)

| Pros                                  | Cons                  |
| ------------------------------------- | --------------------- |
| Low Latency                           | Layout is a nightmare |
| Good redundancy with adaptive routing |                       |
### Diagram
![[Pasted image 20260512152023.png]]


## Meshes - The most common
- Every node is connected to four neighbours except sides and corners
- Node scaling O(N)
- Latency scaling O($\sqrt{N}$)

| Pros                                      | Cons                                            |
| ----------------------------------------- | ----------------------------------------------- |
| Scales well                               | Anisotropic (performance on edges is different) |
| Easy to layout, with many routing options |                                                 |
### Diagram
![[Pasted image 20260512152315.png]]

### Additionally: Torus

| Pros                                                 | Cons                                        |
| ---------------------------------------------------- | ------------------------------------------- |
| No anisotropy (when laid out properly)               | Harder to layout due to unequal link length |
| Greater bisection bandwidth than the equivalent mesh |                                             |
#### Diagram
![[Pasted image 20260512152251.png]]

## Topology Metrics
- **Routing Distance** (of a route) number of channels along a route
- **Minimal Routing Distance** (of a pair of switches) minimum routing distance between two switches
- **Diameter** (of a network) the greatest minimal routing distance in a network
- **Average Routing Distance** (of a network) the *mean* minimal routing distance between all pairs of nodes in a network
- **Bisection Bandwidth**: Cut the network in half, and sum the bandwidth of each link you've cut. Bisection bandwidth is the minimum possible value

### Example:
![[Pasted image 20260512153929.png]]
For this mesh;

It's diameter is 4
Average routing distance (they way I have calculated it)

	Avg Routing distance for an corner node: 2.25
	Avg Routing Distance for an edge node: 1.875
	Avg Routing Distance for a center node: 1.5
	
	There's 4 corners, 4 edges and one center so the total average routing 
	distance = 2

Bisection Bandwidth, for an NxN mesh is $b \sqrt{N}$ where b is the bandwidth (assume that each link has a bandwidth of b)
	





