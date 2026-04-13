**The compiler needs to know it's available!**
# Uses:
- Image processing - multiple pixels at a time
- Video processing - processing blocks
- array/vector processing
- text processing
	- x1.25 - x1.7 speed ups reported
- General speed-up (depends on app)
	- Compilers can detect code which can use SSE
	- Read the auto-vectorization link

# **SSE**: **S**treaming [[SIMD]] **E**xtensions for [[x86]]:
- 128 bit registers that can be packed with various data types
- 64-bit [[x86]] [[CPU]]'s have 16 of these registers
- Extra ~50 instructions
- Additional:
	- AVX extends SSE
		- 256-bit registers
		- Three-operand instructions
	- AVX-512: 512-bit registers
		- Performance increases in certain situations
##### Example with 256 bits:
- 8 32bit floating point numbers packed into a special register
- Processed together
- Then unpacked

# SSE(1) Streaming [[SIMD]] extensions:
- 8 x 16bit words or 4 x 32bit words
- Intel [[CPU]]'s have 8 of these special registers
- Can do float maths (SSE)

# SSE2 - Streaming [[SIMD]] extensions:
- 16 x 16bit words or 8 x 32bit words
- Intel [[CPU]]'s have 16 of these special registers
- Can do float maths
- AMD [[CPU]]'s after 2011 are similar