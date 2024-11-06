# EEPROM
[[Lecture 13 - EEPROM & Watchdog Timer.pdf]]
- Electrically Erasable and Programmable memory (EEPROM)
	- Way to store user data that is distinct from the program
	- Is bytewise erasable
- Flash
	- Is blockwise erasable
	- Write in 80 $\mu s$, erase in 11ms
- SRam
	- 1 cycle (62.5 ns)


# Watchdog timers
[[Lecture 13 - EEPROM & Watchdog Timer.pdf#page=15|Lecture 13 - EEPROM & Watchdog Timer, p.15]]
- Lets say a piece of code runs but it gets stuck. You want to reset the board
	- When you enter an ISR your interrupts get disabled so you won't be able to get out of this case
- Automatically resets the board if something doesn't happen within a certain amount of time

- Watchdog has a counter
- Need to periodically reset watchdog timer `wdt_reset()` from `#include <avr/wdt.h>`
- **Watchdog timer is still on after a reset**. So need to stop watchdog upon startup

- You can check the reason for a reset by using `RSTCTRL_WDRF` flag is set in the `RSTCTRL.RSTFR` register
# Combining the two
- Can save state in the EEPROM in the event of a board reset from watchdog
