[[AVR128DB28 Datasheet.pdf#page=232|AVR128DB28 Datasheet, p.232]]
- Timers allow to remove delay functions and trigger precise time events
- Triggers happen when the counter equals a certain value or it overflows

# AVR Timers
- 3 types:
	- Type A: 16 bit, can be split into four 8 bit timers
	- Type B: 16 bit
	- Type D

# Timer TCA0
- `TCA0` - timer counter
- `TCA0.SINGLE.CNT` stores the count
- `TCA0.single.PER` (period) stores the match value at which to trigger
- The direction (counting up or down) can be set
- Count register can be changed by the programmer
![[AVR128DB28 Datasheet.pdf#page=235&rect=77,317,509,468|AVR128DB28 Datasheet, p.235]]



## Timer dividers
The timer clock frequency can be adjusted to get shorter or longer periods
- Available dividers: $N=1,2,4,8,16, 64, 256, 10224$

- Time it takes for the timer to reach the match value
$$
T=\frac{N(1+\text{PERIOD})}{(f_{\text{clock io}})}
$$

## Double buffering


# Registers
[[AVR128DB28 Datasheet.pdf#page=246|AVR128DB28 Datasheet, p.246]] `SINGLE.CTRLA`


`TAC0.SINGLE.INTCTRL` - can enable an interrupt to trigger on counter overflow
`TCA0.`

- `SINGLE` refers to a single timer. Some timers (Timer A) can be split into multiple timers
- The split timers are configured together but operate independently

## CMP0
- Can use `CMP0` to do matches
- Can generate square wave when in `TCA_SINGLE_WGMODE_FREQ_gc` mode
	- `CMP0` output goes to `WO0` (waveform output 0) which writes to `PORTA0`
	- `PORTA0` is equal to an output of 1 every other match trigger
- `TCA0.CMPn` outputs to `PORTAn`
	- Can reroute signals to other ports with the `PORTMUX.TCAROUTEA` register
$$
f_{WO 0} = \frac{f_{\text{clk-period}}}{2N \cdot (1+CMP)}
$$
ex: 

$$
f_{WO 0} = \frac{f_{\text{clk-period}}}{2N \cdot (1+CMP)} = \frac{16 Mhz}{2 (64) (1+249)}
$$

### Code example
```c
 // 500Hz Timer TCA0 assuming F_CPU = 16MHz 
 
void InitTCA0(void) { TCA0.SINGLE.CTRLB = TCA_SINGLE_WGMODE_FRQ_gc;
	// Normal mode 
	TCA0.SINGLE.CMP0 = 249; // Set number of ticks for period /
	TCA0.SINGLE.INTCTRL = TCA_SINGLE_CMP0_bm; // Enable TCA0 CMP0 ISR
	TCA0.SINGLE.CTRLB |= TCA_SINGLE_CMP0EN_bm; // Enable waveform output // Set Prescalar to 64 & enable timer. Each tick is 4us 
	TCA0.SINGLE.CTRLA |= (TCA_SINGLE_CLKSEL_DIV64_gc |TCA_SINGLE_ENABLE_bm); 
	PORTA.DIRSET = PIN0_bm; // enable waveform output 

	// Remap PORT				 
	 PORTMUX.TCAROUTEA |= PORTMUX_TCA0_PORTD_gc; // PORTD.DIRSET = PIN0_bm; // enable waveform output

}
```

# Patterns

# Common issues
## Changing period while the timer is running
- If the period is set to a smaller value than the current count, the counter might 
- Previously you could only fix by triggering period updates when the `count=0`
- Now you can use **double buffering**
	- The period value gets automatically applied at the next update point (when count=0) instead of having to  
	- Aka period update is buffered/held off until next update point

## Continuous interrupts
- Make sure to clear the interrupt after the ISR executes. Depending on the MCU it may or may not clear it on the interrupt.

# Examples

## Timer driven state machines
![[Lecture 6.pdf#page=21]]
```c
////// timer interrupts
#define DEBOUNCE_TIME 10
volatile int debounce_timerCount = DEBOUNCE_TIME;
ISR(TCA0_OVF_vect)
{
	if (debounce_timerCount >0) {
		debounce_timerCount--;
	} else {
		buttonSM();
		debounce_timerCount = DEBOUNCE_TIME;
	}
	TCA0.SINGLE.INTFLAGS |= TCA_SINGLE_OVF_bm; // must clear the interrupt
}
// 1ms ISR for Timer TCA0 assuming F_CPU = 16MHz
void InitTimerTCA0(void)
{
	TCA0.SINGLE.CTRLB = TCA_SINGLE_WGMODE_NORMAL_gc; // Normal mode
	TCA0.SINGLE.PER = 249; // Set number of ticks for period
	TCA0.SINGLE.INTCTRL = TCA_SINGLE_OVF_bm; // Enable TCA0 Overflow ISR
	// Set Prescalar to 64 & enable timer. Each tick is 4us
	TCA0.SINGLE.CTRLA |= (TCA_SINGLE_CLKSEL_DIV64_gc | TCA_SINGLE_ENABLE_bm);
}

///// Debounce state machine

volatile bool btnPushed = false;
#define BTN (!(VPORTB.IN & PIN2_bm))
typedef enum {RELEASED, MAYBE_PUSHED,
PUSHED, MAYBE_RELEASED
} btn_state_t;

void buttonSM(void)
{
	static btn_state_t state = RELEASED;
	switch (state)
	{
		case RELEASED:
			if (BTN)
				state = MAYBE_PUSHED;
			break;
			
		case MAYBE_PUSHED:
			if (BTN) {
				state = PUSHED;
				btnPushed = true;
			} else {
				state = RELEASED;
			}
			break;
		case PUSHED:
			if (!BTN)
				state = MAYBE_RELEASED;
			break;
		case MAYBE_RELEASED:
			if (BTN)
				state = PUSHED;
			else
				state = RELEASED;
			break;
	}
}

```

## Task based programming

- We want to minimize wait times
```c
int main(void)
{
	while(1) {
		if (CondABC) {
			CodeA;
			delay_ms(WaitTimeB);
			CodeB;
			delay_ms(WaitTimeC);
			CodeC;
			ResetCondABC();
		}
	}
	…
}
```

- Separate the code into tasks
```c
void SubTaskA(InpABC)
{
	CodeA;
	InpB = CaptureCurrentStateCodeA;
}
void SubTaskB(InpB)
{
	RecoverStateEndOfCodeA(InpB);
	CodeB;
	InpC = CaptureCurrentStateCodeB;
}
void SubTaskC(InpC)
{
	RecoverStateEndOfCodeBB(InpC);
	CodeC;
}
```

```c
ISR(TCA0_OVF_vect)
{
	if (TimerWaiting>0)
	TimerWaiting--;
}

int main(void)
{
	state = A;
	while(1) {
	switch(state) {
		case A:
			if (CondABC) {
				SubTaskA(InpABC);
				state = B;
				TimerWaiting = WaitTimeB;
			}
			break;
		case B:
			if (TimerWaiting==0) {
				SubTaskB(InpB);
				state = C;
				TimerWaiting = WaitTimeC;
			}
			break;
		case C:
			if (TimerWaiting==0) {
				SubTaskC(InpC);
				state = A;
				ResetCondAB();
			}
			break;
	}
}
}

```