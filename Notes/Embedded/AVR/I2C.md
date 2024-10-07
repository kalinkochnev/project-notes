[[Notes/Embedded/STM32/I2C|STM32 I2C]]
[[Pullup and Pulldown resistors]]

**Overview of communication interfaces and how many devices they can communicate to**
![[Lecture 9.pdf#page=3|Lecture 9, p.3]]

- Can connect up to 128 devices on the bus
- All devices have individual addresses
- Each device can communicate with any other device
- Host/Master Initiates
- TWI stands for Two-Wire Interface
![[Lecture 9.pdf#page=7&rect=194,0,760,472|Lecture 9, p.7]]

# Bus arbitration
- All masters continuously monitor the SDA line after outputting data
1) Device 1 tries to write the data to the line
2) If it sees that the data on the line is not equal to the data it output, then it lost arbitration and a different device has control
3) Device 1 backs off

# Registers
[[AVR128DB28 Datasheet.pdf#page=438|AVR128DB28 Datasheet, p.438]]
`MCTRLA`
- Controls Read/Write Interrupt Enable

`MCTRLB`
- `MCMD` indicates which bit to set (start, stop, received)

`MSTATUS`
- Indicates the status of the bus (does the device own the bus?)

`MADDR`
- Specifies the address of the external client device
- Bit 0 controls whether it is the R/W direction

# Frequency and baud rate
![[Lecture 9.pdf#page=14&rect=337,259,951,444|Lecture 9, p.14]]

# Examples
[[Lecture 9.pdf#page=15|Lecture 9, p.15]]
