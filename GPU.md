# Summary:
- GPUs were originally just graphics co-processors
- Now do much more than graphics
- Different architecture to [[CPU]]s
	- more of a vector-processing role ([[CPU]]s are more scalar)
# Facts:
- Large D[[RAM]] bandwidth
	- DRAM chips arranged around the GPU 
		- yk the squares on a [[RAM]] stick? yeah those are also on the GPU

# Uses: 
- Video compression
- Video transcoding
- Image processing
- Modelling
- Autonomous vehicles
- AI
- Number-crunching
- Crypto currency mining

[[CUDA]]

# Tensor Cores
- Cores targeted at AI acceleration
- Specifically for fused multiply-add (FMA) operations
	- Used alot in:
		- Neural networks
		- Nvidia's DLSS stuff
# Representing Objects:
- Represent 3D objects as a **MESH** of:
	- Vertices
	- Edges
	- Faces
# GPU Pipeline:
![[Pasted image 20231213175256.png]]
- Rasterization = turning shapes into pixels

# Examples:
## Nvidia GPUs (and their architectures)
### GTX 980 (2014):
- Uses "Maxwell architecture"
- 5 TFLOPS !
- 5.2 billion transistors
- 2048 [[CUDA]] Cores
- 1.1 GHz [[core]] clock
- 7GHz effective memory clock
- 256 bit memory [[Bus]]
### GTX 1080ti (2016):
- Uses "Pascal" architecture
- 11.34 TFLOPS
- 11.8 billion transistors
- 3584 [[CUDA]] cores
- 1.5 Ghz [[Core]] clock
- 11 GHz effective memory clock
- 352-bit memory [[Bus]]
- 250 W
### RTX 20 Series (2018)
- Uses Turing architecture
### Ampere (2020) and Ada Lovelace (2022)
- More of the same **BUT** the INT32 cores are now FP32
- Improvements are mostly in the RT and Tensor cores
- And a move from 8nm to 5nm
- More L1 [[Cache]]!

## AMD GPUs
### ATI RV770:
- 10 [[SIMD]] processors with 16 shaders each!!
- Each [[SIMD]] unit has its own thread
### RX 6900 XT:
~25 Tflops
- 26 billion transistors
- 5120 GPU "cores"
- 2.2 GHz [[core]] clock
- 16 Ghz effective memory clock
- 16 GB V[[RAM]] with 256-bit wide [[Bus]] (512 GB/s)
- 80 ray tracing units
- 7nm stuff
### RX 7900 XTX:
~61 Tflops
- 57.7 billion transistors
- 6144 GPU "cores"
- 2.5 GHz [[core]] clock
- 20 GHz effective memory clock
- 24 GB V[[RAM]] with 384-bit wide [[Bus]] (960 GB/s)
- 96 ray tracing units
- 5nm stuff
## Onboard Intel GPU's
~ 1/10th performance of separate GPU
- Current gen ~ 1TFlops
- Good for **LAPTOPS**
- Ideal of encoding tasks

## Playstation 5:
~ 10 TeraFlops
- 8 [[Core]] AMD Zen2 and Radeon GPU
- 36 GPU Compute units with ray tracing support
# Why do we need one?
 - Graphics is maths inensive! 1920x1080 = 2 Mega Pixels (6.2 MB)
 - 3D drawing, rendering and shading needs lots of per-pixel maths, and GPU's are designed to be efficient at this


