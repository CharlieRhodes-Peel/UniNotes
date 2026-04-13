# CUDA Cores
- Uses a [[SIMD]] model
- Contains a floating point unit (and sometimes an integer unit)
- Special Function Units are for trigonometric operations
- RTX 4090 has 128 Streaming Multiprocessors
	- A "streaming multiprocessor" is made up of 128 CUDA cores
- Uses thread warps
	- Each warp executing the same instruction ([[SIMD]])