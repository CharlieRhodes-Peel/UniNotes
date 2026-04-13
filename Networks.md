# Something that links computers together

# WAN: 
- Wireless Area Network:
	- A network that spans a large *geographical* area
# LAN:
- Local Area Network
	- A network that spans a **small** or **local** *geographical* area

# TCP/[[IP]] Model:
- Application Layer:
	- Hostname (DNS stuff)
	- How the application you are using interacts with the layered model
- Transport Layer:
	- Port number
- Internet Layer:
	- [[IP]] address
- Link Layer:
	- [[MAC address]]

# TCP Flow / Congestion Control:
- Throttling the send rate as to not overwhelm the network

### TCP Flow = *sliding window protocol*
- just remember that, feel like it's important lol

### Congestion control
- Sender starts by sending small packets
- Size of packets sender sends exponentially increases
- Until packet loss is happens, at which it starts again
- Results in a **SAWTOOTH** like pattern
![[Pasted image 20240110100804.png]]
Doesn't always go downhill like this, just an example of what the number of packets could get through is