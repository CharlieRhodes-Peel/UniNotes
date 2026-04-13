# Summary:
- Everything on a **single chip**
- Fixed amount of **on-chip** [[RAM]], storage and I/O
- Low cost for application that are **space restrained**
- Low performance and Low power
- 8, 16, 32 bit are common
- Not very large [[Pipelining]] stuff

# What is?
- Self-contained computer on a **SINGLE** chip
- 8-bit and 16-bit used to be common, 32-bit now king
- Slow clock: 32kHz to ~100MHz
- Small [[RAM]], small storage and can be very low power
- Very Cheap ! > 55% of all [[CPU]]s sold

# Where are they used?
- Embedded controllers
- Cameras
- Medical devices
- Vehicle control systems
- Home appliances (i always think of a washing machine or a fridge)
- Vending machines
- etc. (it's a really long list) think of something that is electronic but is not a **general purpose** computer and that's a microcontroller
# Memory:
- Has [[Register]]s
- S[[RAM]]: as low as 1k
- Flash/EEPROM:
	- 16-64k for programs to run
- Typically no cache (don't link for this reason)
- Microcontrollers generally don't have Memory Management Units (MMU)

# Input / Output (I/O):
- General purpose I/O:
	- Interrupts
	- Pulse Width Modulation ([[PWM]])
- Timers, clocks, counters
- Serial interfaces
	- USART, UART, SPI, CAN (idk what these mean)
- **Can also have**:
	- [[ADC]]s and [[DAC]]s for analogue I/O
	- Capacitive touch interfaces
	- [[Networks]] interfaces, screen interfaces, [[USB]] interfaces, etc.

# Low Power:
- They are designed for battery use
	- Hundreds of $\micro A$ to $<10mA$ active
		- with a few $\micro A$ when in sleep mode
- Uses $\micro W$ or $mW$ (modern CPU's ~2-280W) (don't link)
# Embedded OS:
#### Can't run a "real" [[Operating Systems]]
- Embedded operating systems do exist however !
	- $\micro$Clinux
	- Real-time [[operating systems]]: 
		- FreeRTOS, $\micro$C/OS, Mbed OS
	- IoT operating systems:
		- RIOT-OS, Contiki-NG, TinyOS
#### The Issue with Embedded OS and Libraries:
**LICENSING...**
- 
# Programming Microcontrollers:
- They **NEED** to be programmed
- Remember LED flash lab ?? (that !)
- Usually code written in C
- Unlike desktop application
	- Memory usage and efficiency are **MUCH** more of a concern
# Examples:
### Atmel AVR:
- 8 bit [[RISC]]-based microcontroller
- modified Harvard architecture
- available in a range of flash/[[RAM]] sizes
![[Pasted image 20231214140453.png]]
### Microchip PIC Family
- 8-bit or 16bit wide data memory, 12/14/24 bit instructions
	- latest are 32-bit MIPS
- From 6-pin SMD all they way up to 144-pin SMD chips
- **Harvard architecture**
- Over 12 **billion** sold by 2013
![[Pasted image 20231214140648.png]]

### TI MSP430:
- 16-bit [[RISC]]
- Von Neumann architecture
- Known for it's **LOW POWER**
- Some include radio peripherals
### ESP32 and Xtensa:
- Integrated Wi-Fi and Bluetooth
	- So is used for IoT applications
- [[CPU]] uses Xtensa or [[RISC]]-V [[core]]
	- Not ARM but very [[RISC]]!
- Dual [[core]]
- 240 MHz
- 4 MiB Flash
- 320 KiB [[RAM]]
- C/C++, LUA and [[MicroPython]] support (programmable !)
	- So i guess this is more like a [[Microprocessor]] ??
### ARM Cortex-M:
- Microcontroller part of the ARM family
- 32-bit [[RISC]] [[core]]
- Uses a mix of Von neumann and Harvard architecture
- Uses Thumb-1 and Thumb-2 versions of the ARM [[instruction set]]
###### M4, fast, powerful:
- 50-180 MHz
- 16-256 kB [[RAM]]
- 32 kB to 2 MB flash
- Can do Floating Point, Advanced bit field manipulations and General data processing