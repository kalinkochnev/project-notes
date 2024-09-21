
# Switches
- Since the microcontroller is so fast, it might measure the switch as HIGH a thousand times.
- Can have a flag that gets triggered on first true value
![[Lecture 3.pdf#page=9]]


# Debouncing

**Option 1:**
- Add a delay before re-checking if the button is pressed. 
	- Delay should be >= time bouncing occurs

**Option 2**
- Count how many button "presses" occur from the debouncing and count it as one after a threshold is met

**Option 3** [[Lecture 3.pdf#page=13]]
- Use a hardware debouncer (a low pass filter/capacitor)
- Cons: have to wait for capacitor to charge/discharge
