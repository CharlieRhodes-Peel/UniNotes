Generally have a power use between ~2 - 280 W

**13th Gen Intel Improvements**:
- Instructions Per Clock (key aim)
- Wider Decoding (32 instr/cycle !!)
- Bigger Micro-Op [[Cache]]
- More Exec ports (12)
- out of order window increase
- big load/store queues (>100)
- lots of others for other gens

# Hybrid Architecture:
- A mix of **Performance** and **Efficiency** cores:
	- Efficiency [[core]] are used more in more portable (mobile) devices
	- And vice versa
- Processes needing less performance can run on E cores and save power/heat 

# Newer Generation Intel [[CPU]]'s:
- They are [[CISC]] but "under the hood" do many [[RISC]] like [[Instruction]]s
- [[PCIe]] v5 (16 lanes plus 4 [[PCIe]] v4)
- DDR5 [[ram]] support
- 2-way Simultaneous multithreading (SMT) / [[Hyperthreading]] common with intel

# AMD:
- Can beat Intel on IPC
- 12 memory channels on some chips
- 128 [[PCIe]] 5.0 lanes
- [[Hyperthreading]] also common
## Zen4:
- Multi-[[core]] chiplets that use 5nm process

# Apple's ARM-based [[CPU]]s
(For apple laptops)
- Uses ARM's "Big-Little" architecture - used in phones/tablets previously
- Fast P cores plus power efficient E cores
- Rely on a smarter scheduler