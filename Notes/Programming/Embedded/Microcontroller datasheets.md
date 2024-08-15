https://www.elektormagazine.com/articles/microcontroller-documentation-part-3-block-diagrams
- Look for **pin allocation table** that indicates what features can be used on what pin

# Registers
- Registers hold data temporarily during execution of program. Have a fixed number of bits. 
- In the data sheet the **register descriptors** contain the name of the register and the names of the groups of bits within the register

## Common registers
- **General purpose** registers store intermediate data between arithmetic/logical operations (have access)
- **Stack pointer** is a register that keeps track of position in the stack.
	- Stack stores temporary values, return addresses, during subroutine calls and interrupts
- **Link register** 
- **Control registers** contain configuration for peripherals, control bits for enable/disabling interrupts
- **Status register** contains current status of microcontroller using status/flag bits
	- The microcontroller can check the outcome of arithmetic operations (overflow, carry, zero, etc)
- **Special function registers** provide control/access to peripherals. Used to configure/control I/O, timers, UART, ADC, SPI, etc
- **Program counter** contains memory address of next instruction

## Register descriptions
https://chipcodelab.com/what-are-the-registers-in-the-microcontroller/
1) **`U`** Some bits can be implemented or unimplemented
2) **`R/W`** Implemented bit. Is read and/or write
3) **`-`** hyphen
4) **`0/1`** Value after the device is reset
5) `/`
6) **`q`** a reset dependent pin (changes depending on what caused reset)

|   |   |   |
|---|---|---|
|**Abbreviation**|**Expansion**|**Description**|
|r|read|The software can only read these bits.|
|w|write|The software can only write to this bit. Reading the bit returns the reset  <br>value.|
|rw|read/write|The software can read and write to these bits.|
|rc_w1|read/clear  <br>Clear bit writing ‘1’|The software can read as well as clear this bit by writing 1. Writing ‘0’ has  <br>no effect on the bit value.|
|rc_w0|read/clear  <br>Clear bit writing ‘0’|The software can read as well as clear this bit by writing 0. Writing ‘1’ has  <br>no effect on the bit value.|
|rc_r|read/clear by read  <br>Read bit, automatically clears it to ‘0’|The software can read this bit. Reading this bit automatically clears it to ‘0’.  <br>Writing ‘0’ does not affect the bit value.|
|rs|read/set|The software can read this bit. Writing ‘0’ or ‘1’ triggers an event but does not affect the bit value.|
|rt_w|read-only write trigger|The software can read this bit. Writing ‘0’ or ‘1’ triggers an event but has no  <br>effect on the bit value.|
|t|toggle|The software can only toggle this bit by writing ‘1’. Writing ‘0’ has no effect.|
|Res.|Reserved|The reserved bit must be kept at reset value.|

ex: ![[Pasted image 20240611104137.png]] *Generally, if writing make sure the unimplemented bits are set to 0*
```c
myValue &= 0b00011111;
STATUS = myValue;
```

### Bit groups
- A group of bits may need to be sit, so it may be notated as `BIT_GROUP<X:Y>` where X is MSB and Y is LSB
	- sometimes bits in the same group may be split over same register or go across more than one register



#### Inverted bits
- Have a bar over the top $\overline{X}$
- 0 output means X=1, 1 output means X=0
# Clock
- Different clock sources can be used depending on needs for accuracy (internal clock may not be good enough for UART)
	- A bit group is used to select which clock is used in this processor
	- Bit group is also used to select which bits
- The post scalar divider is a counter that triggers every N cycles and outputs 1 if that particular division is triggered
	-  A bit group is used to select which cycle size to select on

![[Pasted image 20240611105750.png]]