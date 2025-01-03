![[Pasted image 20240614123604.png]]
# Packages
- Install through Help->Manage Embedded Software Packages
- Cube packages stored in `C:\Users\{USERNAME}\STM32Cube\Repository`

# Project structure
## Folders
- `Includes/` - Representation of all include paths and to place references to other include files without compiler specific arguments
- `Core/` - generated project folders + main. Do not change structure.
- `Drivers/` - headers and source files for libraries
- `Binaries/` - final binary file generated by compiler

## Important files
- `Core/Inc/main.h` - contains macro declarations for all labels made using CubeMX
- `Core/Src/main.c` - includes 4 routines
	- `SystemClock_Config(void)` - initializes core and peripheral clocks
	- `MX_GPIO_Init(void)` - configures GPIOs connected to LD2 pin and B1 pin (blue switch on nucleo)
	- `MX_USART2_UART_Init(void)` 
	- `int main(void)` - 1) Initializes
- `Core/Inc/stm32XXxx_hal_conf.h` - HAL configurations are translated into C using macros. Can selectively include HAL modules at compile time
- `Core/Inc/stm32XXxx_it.h` or `.c` file - Depending on CubeMX config, several functions are defined which are callbacks to handle the *Interrupt Service Routines* (ISR)
	- The ISR is invoked by the Nested Vectored Interrupt Controller (NVIC)
	- Callbacks can be found within the startup file under `g_pfnVector`
- `Core/Src/stm32XXxx_hal_msp.c` - MCU Support Package defines initialization functions to configure on-chip peripherals 

### File extensions
`.elf` - Executable and Linkable Format (ELF) binary file
`*.ioc` - device configuration tool generated by CubeMX

# Debugging
### GUI symbols
![[Pasted image 20240617142946.png]]
![[Pasted image 20240617143004.png]]

## Breakpoints

- MCUs have limited number of hardware breakpoints
![[Pasted image 20240617142848.png]]

# Important paths
`C:\Users\Kalin.Kochnev\STM32Cube\Repository\Packs\STMicroelectronics\X-CUBE-TOF1\3.4.1\Projects\NUCLEO-L476RG\Examples` 
- This is the directory that STM stores drivers and examples