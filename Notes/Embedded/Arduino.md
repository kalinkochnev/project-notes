# Using [Arduino-Makefile](https://github.com/sudar/Arduino-Makefile/tree/master)
Assuming `arduino-mk` was installed...
- The full makefile is located in `/usr/share/arduino/Makefile.mk`. It actually includes same basic (but useful) instructions for quick configuration with your own makefile
- A markdown file with explanations of variables is also located in the same directory

`ARDMK_DIR` - place where `*.mk` files are present. Installing `arduino-mk` stores it into `/usr/share/arduino` (where arduino ide is located)

- Arduino has header files for the "core" functionality like `digitalWrite()` etc in `/usr/share/arduino/hardware/arduino/avr/cores/arduino`
- Other libraries like `Wire.h` are stored `/usr/share/arduino/hardware/arduino/avr/libraries`

## Install library in project directory and include
1. `USER_LIB_PATH` is the directory where your library files are located. Each folder should contain a `library.properties` folder to be a proper arduino library.
2. Add the name of the library as specified by `library.properties` to the `ARDUINO_LIBS`
ex:
```bash
### ARDUINO_LIBS
### Any arduino libraries you intend to include
### example 
ARDUINO_LIBS = Wire SPI ODriveArduino CAN 

### USER_LIB_PATH
### Path to where the your project's libraries are stored.
USER_LIB_PATH    =  $(realpath $(PROJECT_DIR)/lib)
```