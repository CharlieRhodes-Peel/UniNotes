## Diagram
![[Pasted image 20260514124154.png]]

# Adding Virtual Channels
This allows *flits* from multiple different *packets* to be stored in separate virtual channels (see [[NoC|Network On Chip]] and [[Flow Control]])

##### Uses of Virtual Channels
- Deadlock escape buffers (let another packet pass through if there is a deadlock)
- Prioritisation (to high prio packets)
- Mitigate wormhole blocking (see [[Flow Control]])


![[Pasted image 20260514134618.png]]
