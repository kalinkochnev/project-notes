![[AVR128DB28 Datasheet.pdf#page=172&rect=36,457,485,668|AVR128DB28 Datasheet, p.172]]
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=172&selection=82,0,84,62&color=yellow|AVR128DB28 Datasheet, p.172]]
> > The device’s I/O pins are controlled by instances of the PORT peripheral registers. Each PORT instance has up to eight I/O pins. The PORTs are named PORTA, PORTB, PORTC,

- What functionality/peripherals are available to each pin are available in this table [[AVR128DB28 Datasheet.pdf#page=18|AVR128DB28 Datasheet, p.18]]

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=172&selection=98,0,102,32&color=yellow|AVR128DB28 Datasheet, p.172]]
> > Each `PORT` pin has a corresponding bit in the Data Direction (`PORTx.DIR`) and Data Output Value (`PORTx.OUT`) registers to enable that pin as an output and to define the output state. For example, pin PA3 is controlled by `DIR[3]` and `OUT[3]` of the `PORTA` instance

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=172&selection=108,4,108,65&color=yellow|AVR128DB28 Datasheet, p.172]]
> > PORT also supports asynchronous input sensing with interrupts


# Initialization
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=174&selection=28,0,32,21&color=yellow|AVR128DB28 Datasheet, p.174]]
> > Enable or disable the output driver for pin Pxn by respectively writing ‘1’ to bit n in the PORTx.DIRSET or PORTx.DIRCLR register
- To use pin `n` as an output, write bit `n` of `PORTx.DIR` to `1`. `0` is input.

# Setting output
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=174&selection=35,1,40,20&color=yellow|AVR128DB28 Datasheet, p.174]]
> > Set the output driver for pin `Pxn` to high or low level respectively by writing ‘1’ to bit n in the `PORTx.OUTSET` or `PORTx.OUTCLR` register

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=174&selection=139,0,139,115&color=yellow|AVR128DB28 Datasheet, p.174]]
> > The Pin n Control (PORTx.PINnCTRL) register is used to configure inverted I/O, pull-up, and input sensing of a pin.
> 
> 

# Virtual Ports
> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=176&selection=18,0,20,23&color=yellow|AVR128DB28 Datasheet, p.176]]
> > The Virtual PORT registers map the most frequently used regular PORT registers into the I/O Register space with single-cycle bit access

> ![[AVR128DB28 Datasheet.pdf#page=176&rect=78,544,548,635&color=yellow|AVR128DB28 Datasheet, p.176]]

> [!PDF|red] [[AVR128DB28 Datasheet.pdf#page=176&selection=52,0,54,47&color=red|AVR128DB28 Datasheet, p.176]]
> > Avoid accessing the mapped VPORT register using the single-cycle I/O instructions immediately after accessing the regular PORT register. This may c

# Bit positions
- AVR library has predefined keywords for bit positions of each register
	- ex: 5th bit `#define PIN5_bp 5`
- The bitmask is also provided (the `i`th bit is set to `1`)

**Equivalence**
```c
PORTB_OUT = (1<<PIN5_bp); 
PORTB_OUT = PIN5_bm;
```
# Header Files
[[Conventions and Notation#Register to Header File conversion]]
```c
#define PORTB_DIR _SFR_MEM8(0x0420) 
#define PORTB_DIRSET _SFR_MEM8(0x0421) 
#define PORTB_DIRCLR _SFR_MEM8(0x0422) 
#define PORTB_DIRTGL _SFR_MEM8(0x0423) 
#define PORTB_OUT _SFR_MEM8(0x0424) 
#define PORTB_OUTSET _SFR_MEM8(0x0425) 
#define PORTB_OUTCLR _SFR_MEM8(0x0426) 
#define PORTB_OUTTGL _SFR_MEM8(0x0427) 
#define PORTB_IN _SFR_MEM8(0x0428) 
#define PORTB_INTFLAGS _SFR_MEM8(0x0429) 
#define PORTB_PORTCTRL _SFR_MEM8(0x042A) 
#define PORTB_PINCONFIG _SFR_MEM8(0x042B) 
#define PORTB_PINCTRLUPD _SFR_MEM8(0x042C) 
#define PORTB_PINCTRLSET _SFR_MEM8(0x042D) 
#define PORTB_PINCTRLCLR _SFR_MEM8(0x042E) 
#define PORTB_PIN0CTRL _SFR_MEM8(0x0430) 
#define PORTB_PIN1CTRL _SFR_MEM8(0x0431) 
#define PORTB_PIN2CTRL _SFR_MEM8(0x0432) 
#define PORTB_PIN3CTRL _SFR_MEM8(0x0433) 
#define PORTB_PIN4CTRL _SFR_MEM8(0x0434) 
#define PORTB_PIN5CTRL _SFR_MEM8(0x0435) 
#define PORTB_PIN6CTRL _SFR_MEM8(0x0436) 
#define PORTB_PIN7CTRL _SFR_MEM8(0x0437)
```

- This is also available in struct format
![[Lecture 2.pdf#page=16&rect=71,4,897,476&color=yellow|Lecture 2, p.16]]

# Examples
```c
// ------- Preamble -------- 
#define F_CPU 4000000UL 
/* Tells the Clock Freq to the Compiler. */ 
#include <avr/io.h> /* Defines pins, ports etc. */ #include <util/delay.h> /* Functions to waste time */ 

int main(void) { 
	/* Data Direction Register D: writing a one to the bit enables output. */ 
	VPORTD.DIR = 0b11111111; 
	VPORTD.OUT = 0b00000100; 
	
	// ------ Event loop ------ // 
	while (1) { 
		VPORTD.OUT = 0b11111111; /* Turn on the LED bits/pins in PORTD */ 
		_delay_ms(1000); /* wait for 1 second */ 
		VPORTD.OUT = 0b00000000; /* Turn off all D pins/LEDs */ 
		_delay_ms(1000); /* wait for 1 second */ 
	} /* End event loop */ 
	return (0); /* This line is never reached */ 
}
```