- **Bit weight** - how much voltage corresponds to a single step up
- **Full scale** - what is the maximum voltage you can replicate
- **Quantization error** - the difference between the analog signal and the closest available digital value at each sampling instant from the A/D converter
![[Pasted image 20241002143929.png]]

![[Lecture 8.pdf#page=8|Lecture 8, p.8]]

- A multiplexer selects which pin to use for the ADC
- A sample and hold circuit (a capacitor that gets charged and then disconnected)

- It takes $\frac{13.5 + 2}{\text{ADC CLK}} + \frac{4}{\text{CPU CLOCK PERIOD}}$ clock cycles
	- The 13.5+2 is in 12 bit mode (responsible for sampling and conversion)
	- 11.5 in 10 bit mod

# Accuracy
- MCU produces 150mV of line noise
- Capacitances close to CPU can eliminate
# Registers
`CTRLA`
- Run standby - should ADC run in lower power mode
- Conv mode
	- Single ended - compare to ground
	- Differential - compare differential
- Left adju - whether result is "left adjusted"
- RESSEL - 10 bit or 12 bit mode
- FREERUN - run forever

`CTRLB` Can control the accumulation of a number of ADC readings. Can use to get an average over time.
- SAMPNUM - how many samples to accumulate

`CTRLC`
CLK_ADC must be between 125kHz and 2Mhz
- Prescaler decreases the CPU clock speed so that the ADC can handle it
	- Prescaler of 16 gives $\frac{16\text{MHz}}{16}=1MHz$
	- ex: $\frac{13.5+2}{1 MHz}+\frac{4}{16MHz}=15.75 [\mu s]$

`CTRLD`
- It takes time to setup the ADC so 

`MUXPOS`
- Selects which pin to use on the microcontroller for conversion

`RES`
- Contains result of ADC conversion
- if `LEFTADJ` bit is set to one, it brings the 
	- This is so we don't have to manually shift in case we only want to read the upper 8 bits

`VREF.ADC0REF`
- Specifies what voltage reference to use

- You need to actually start the ADC to run a conversion
	- When the conversion is complete, the bit is reset to 1
	- Need to wait
	- Interrupts might be pointless because too much overhead.
```c
ADC0.COMMAND = ADC_STCONV_BM;
while ((ADC0.COMMAND & (1<<ADC_STCONV_bp)))
```


# Conversion
![[Lecture 8.pdf#page=23&rect=147,4,792,493|Lecture 8, p.23]]

