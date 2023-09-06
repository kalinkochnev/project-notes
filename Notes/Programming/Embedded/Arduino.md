# Using [Arduino-Makefile](https://github.com/sudar/Arduino-Makefile/tree/master)
Assuming `arduino-mk` was installed...
- The full makefile is located in `/usr/share/arduino/Makefile.mk`. It actually includes same basic (but useful) instructions for quick configuration with your own makefile
- A markdown file with explanations of variables is also located in the same directory

`ARDMK_DIR` - place where `*.mk` files are present. Installing `arduino-mk` stores it into `/usr/share/arduino` (where arduino ide is located)

- Arduino has header files for the "core" functionality like `digitalWrite()` etc in `/usr/share/arduino/hardware/arduino/avr/cores/arduino`
- Other libraries like `Wire.h` are stored `/usr/share/arduino/hardware/arduino/avr/libraries`

