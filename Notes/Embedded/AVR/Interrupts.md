# Programmed I/O
- W/o interrupts the CPU is directly controlling the I/O
	- checking for updates
	- Sending commands
	- Getting data
- This wastes CPU time

# Interrupts
- Useful when the I/O is slow
- CPU doesn't have to wait

## Polling vs Interrupts
- The compiler can optimize 

| Polling vs                                                                                                            | Interrupts                                                                            |
| --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| - Regular events can be controlled at user level<br>- Compiler can optimize, doesn't have to store as many registers. | - Good for infrequent events<br>- Useful when can't predict when events will come<br> |
|                                                                                                                       |                                                                                       |
## Control flow
1) Processor executes main code
2) Interrupt happens and processor stops main code
3) Processor saves main code state (program counter/registers)
4) Processor jumps to interrupt service routine (ISR)
5) After ISR completes, processor restores program state

**Note:** It takes 11 cycles to enter and exit an ISR, 20-30 cycles to save state of the MCU (2.5$\mu s$)


Interrupt vector table - indicates where the ISR is located in in memory
- RETI instruction tells CPU to return to main
- If an interrupt mask bit is set but an ISR in the vector table is not set, default action is to reset board on interrupt.

# General flow
![[Lecture 5.pdf#page=9]]


# Common issues
[[Notes/Embedded/STM32/Interrupts|Interrupts]]
## Flags and `volatile`
- A common pattern is that an interrupt sets a flag so the main function will do some work.
	- The compiler may see the flag variable in main and see it isn't used anywhere else, so it saves the value in a register.
	- In the ISR, the flag is in memory
	- The effect is that variable locations are in two different spots
	- This is what `volatile` prevents [[Embedded C#`volatile`]]
## Setting a flag common to main and ISR
- While checking a status flag common to main and ISR, it's possible the interrupt might trigger right after the flag was checked
=> Before checking a flag, disable the interrupts first and then re-enable after done checking

## ISRs that take a long time
Ex: Using printf inside an interrupt. It takes a long time and other interrupts can't be processed
1. You can try buffering the characters that need to be printed
	1. Con: buffer may overflow if ISR is triggered frequently

## Nested interrupts
- Need to temporarily disable the interrupt when entering the ISR since the interrupt might re-trigger the same interrupt and cause weird behavior.
# Lab notes
CTRLA Register - [[AVR128DB2848 Datasheet.pdf#page=399]]
