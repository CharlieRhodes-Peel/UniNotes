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
- **[[Flow Control]] and Buffering**: What happens when the network is heavily loaded? What happens if there is simply no space to store a packet somewhere?

# High-Level Requirements
Interconnect design trade-offs:
Think about the good-time-cost triangle thingy or like the switch meme that can only be 2 at a time. It's like that for the following!
- **Performance** How well can your compute cores *communicate
- **Energy** communication is expensive and frequent
- **Scalability** How big can you go? How big do you *need* to go?
- **Reliability** Do you need reliable communication? There are situations where you don't actually need *EVERY* packet to be reliable

# Terminology
- **[[Switch]]/Routing [[Switch]]:** Connects inputs and output channel
	- ![[Pasted image 20260512142943.png]]
	- A diagram showing Channels connecting switches and IPs together
- **Channels** connect [[switch]]es together
- **IP**: A component that is serviced by a [[switch]]:
	- Could be anything that sends traffic i.e: Compute cores, caches, memory units. gpus, i/o, etc...
- **Direct Node**: [[Switch]] with an IP attached to it
	- ![[Pasted image 20260512143323.png]]
	- Diagram showing a channel between two direct nodes
- **Indirect Node** A [[switch]] within a network, that doesn't have a direct attached component
- **Message** A "transfer unit", from the perspective of *IPs*
	- So like a ping to google.com
- **Packet** A "transfer unit", from the perspective of the *network* 
	- A message is made up of 1 or more packets
- **Flit** A "transfer unit", from the perspective of *[[switch]]es* 
	- A packet is comprised of one or more **flits**

# --> [[Topology]] <--

# --> [[Routing]] <--

# Switching Mechanisms
**Circuit switching**: Full path is setup *before* transmission, *blocking* the pathway for other messages
- Better for *streams* of data as has faster arbitration
**Packet switching** Path determined on a **per-packet** basis
- There's no init cost to **streams** of data, so is more *flexible*