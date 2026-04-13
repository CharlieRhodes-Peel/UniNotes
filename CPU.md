# Areas that can be improved:
- Faster Virtualisation
- Better Branch Prediction
	- For [[Pipelining]]
- New [[SSE]] Instructions
- Improved Lock Support
- Additional Caching Hierarchy
- Improved Loop Streaming
- Deeper Buffers
- Simultaneous Multi-Threading 
- Larger [[Cache]]
# Power Management
- Built into the chip
- Separate [[Microcontroller]] looks after power
	- Can turn off a whole [[core]] completely
	- Can boost clock when needed ([[Turbo Boost]])

# How do we make things "better":
*Better*, as a user, is a subjective metric. Could it be measured by instructions per second? instructions per cycle? instructions per joule? programs per second? All of these have quantitative results but represent different user's needed
- Both [[ISA]] and architecture have an impact
	- We can open up the [[ISA]] to give architectural freedom
	- Or close down the [[ISA]] to make compilation easier
	- We could add more silicon to speed things up
	- Or reduce silicon to reduce area
	- ...