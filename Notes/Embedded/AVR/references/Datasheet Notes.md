
# CPU
![[AVR128DB28 Datasheet.pdf#page=34&rect=32,459,530,673&color=yellow|AVR128DB28 Datasheet, p.34]]
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=34&selection=98,18,102,36&color=yellow|AVR128DB28 Datasheet, p.34]]
> > The instructions in the program memory are executed with a single-level pipeline. While one instruction is being executed, the next instruction is prefetched from the program memory. This enables instructions to be executed on every clock cycle.

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=36&selection=29,81,31,95&color=yellow|AVR128DB28 Datasheet, p.36]]
> > After an arithmetic or logic operation, the Status Register (CPU.SREG) is updated to reflect information about the result of the operation.

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=36&selection=43,0,45,74&color=yellow|AVR128DB28 Datasheet, p.36]]
> > The multiplier is capable of multiplying two 8-bit numbers into a 16-bit result. The hardware multiplier supports different variations of signed and unsigned integer and fractional numbers

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=36&selection=73,0,73,112&color=yellow|AVR128DB28 Datasheet, p.36]]
> > After being reset, the CPU will execute instructions from the lowest address in the Flash program memory, 0x0000
> 
> 

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=36&selection=83,0,85,102&color=yellow|AVR128DB28 Datasheet, p.36]]
> > During interrupts and subroutine calls, the return address PC is stored on the stack as a word pointer. The stack is allocated in the general data SRAM, and consequently, the stack size is only limited by the total SRAM
> 
> 

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=37&selection=64,0,68,46&color=yellow|AVR128DB28 Datasheet, p.37]]
> > The stack is used for storing return addresses after interrupts and subroutine calls. Also, it can be used for storing temporary data. The Stack Pointer (SP) always points to the top of the stack. The address pointed to by the SP is stored in the Stack Pointer (CPU.SP) register.

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=38&selection=25,0,27,45&color=yellow|AVR128DB28 Datasheet, p.38]]
> > The register file consists of 32 8-bit general purpose working registers used by the CPU. The register file is located in a separate address space from the data memory
> 
> 

## Memory map
![[Lecture 2.pdf#page=6&rect=135,18,820,470|Lecture 2, p.6]]
# Pinout
![[AVR128DB28 Datasheet.pdf#page=13&rect=31,170,543,712|AVR128DB28 Datasheet, p.13]]
![[Lecture 2.pdf#page=4&rect=253,2,770,469|Lecture 2, p.4]]



# Interrupts
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=19&selection=619,0,625,10&color=yellow|AVR128DB28 Datasheet, p.19]]
> > All pins can be used for external interrupt, where pins Px2 and Px6 of each port have full asynchronous detection.


# Reset
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=20&selection=60,0,60,52&color=yellow|AVR128DB28 Datasheet, p.20]]
> > The PORT pins are in their default state after Reset

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=22&selection=118,0,122,78&color=yellow|AVR128DB28 Datasheet, p.22]]
> > The RESET pin on the device is active-low with an internal pull-up resistor, and externally pulling the pin low will result in a device Reset. An external pull-up resistor is usually not required

# External voltage reference
If the design includes using an external voltage reference, the general recommendation is to use a suitable capacitor connected in parallel to the reference

# Power and Regulation
![[AVR128DB28 Datasheet.pdf#page=27&rect=75,233,555,327&color=yellow|AVR128DB28 Datasheet, p.27]]
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=27&selection=154,0,161,10&color=yellow|AVR128DB28 Datasheet, p.27]]
> > The device has an internal voltage regulator that powers the VDDCORE domain. This domain has most of the digital logic and the internal oscillators. The voltage regulator balances power consumption when the CPU is active or in a sleep mode

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=28&selection=41,0,46,56&color=yellow|AVR128DB28 Datasheet, p.28]]
> > The Power-on Reset (POR) and the Brown-out Detector (BOD) monitors VDD and will keep the system in reset if the voltage level is below the respective voltage thresholds
> 
> 
# External Oscillators
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=25&selection=50,4,54,111&color=yellow|AVR128DB28 Datasheet, p.25]]
> > use of external oscillators and the design of oscillator circuits are not trivial because of many variables: VDD, operating temperature range, crystal type and manufacture, loading capacitors, circuit layout, and PCB material

