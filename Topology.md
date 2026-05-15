# Summary
How things are connected to other things

For the following topologies below. Realistically most systems **combine** aspects of all of these
# Types of Topology
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
- Almost no contention on the channels, Any contention is at the [[switch]] level
- Latency is quickest O($1$), it's hard to layout complex maps of switches, so any latency is a *distance* problem
- **Layout** like I said above is **hard**
- Scaling is **TERRIBLE** O($n^2$), every time you want to add a new [[switch]] have to connect every other [[switch]] to it
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

### Case study: Sun Niagara II
Here is the chip layout for the Sun Niagara II
- The *crossbar* is located at the part labelled *ccx*
![[Pasted image 20260515114642.png]]
- There is 1 bar **per** L2 [[Cache]] and non-cachable unit(the **NCU**)
- The crossbar has two **buffers** per **core** per **L2** **cache** to handle data transfer (which is not shown here)

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

### Case study: IBM Cell (2007), in PS3
This chip uses uses 8 synergistic Processor Elements (**SPEs**), just think of them as cores though they are more specialised to multimedia than general purpose ones. These are **ringed** together using the element [[NoC|Interconnect]] [[Bus]]
![[Pasted image 20260515115534.png]]

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


# Topology Metrics
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