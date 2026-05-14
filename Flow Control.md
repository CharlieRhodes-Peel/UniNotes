What happens when the network is heavily loaded? What happens if there is simply no space to store a packet somewhere?
# Methods
Generally the last two, (*bufferless dlfection* and, *store and forward*) aren't used that much now, but they are included here to make **Wormholes** make sense

## Wormholes
*Flits* (see [[NoC|Network On Chip]]) move independently, **BUT** buffers can't mix flix from different packets. i.e the **path is reserved** to the first packet who's flits are ahead

| Pros                                                 | Cons                                                                                                                                                                    |
| ---------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Lower latency, and buffers are used more effectively | The *wormhole blocking* affect that is described in diagram (slows blue packets down). Can be mitigated with virtual channels in a [[Switch]] (see <-- for information) |

### Diagram
So here you see in the diagram, the *Green* flits have made it through the [[Switch]] with two inputs, and the green flit is ahead. So the blue flits will have to wait (and collect up like in store and forward) until the path is clear
![[Pasted image 20260514134050.png]]

## Bufferless deflection
The is when [[Switch]]es don't contain any buffers. Traffic is injected by the IP when there is a free output connection.
- In response to contention, one packed is *deflected* to it's neighbour

| Pros                         | Cons                                          |
| ---------------------------- | --------------------------------------------- |
| No space taken up by buffers | Livelock is possible                          |
|                              | Performance issues under high congestion      |
|                              | Extra routing complexity to manage deflection |

## Store and Forward
Each packet is moved in it's *entirety* between each [[Switch]]. Has high latency, and high buffer requirements. So each *flit* is sent one at a time in the packet until the full packet is send to the next [[Switch]]
