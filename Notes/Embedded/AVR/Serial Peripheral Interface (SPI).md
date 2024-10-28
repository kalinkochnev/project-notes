[[Lecture 12 - SPI.pdf]]
- Has four signals
- 8 bit communication protocol
- It is bidirectional communication
- Host/master decides which client to talk to based on the "chip select"
	- Each client/slave has only one 

| SCKL | Serial clock (outputs from host)                |
| ---- | ----------------------------------------------- |
| MOSI | Master output, Slave Input (output from host)   |
| MISO | Master Input, Slave Output (output from client) |
| SS   | Slave Select (active low, output from host)     |
|      |                                                 |
# Data modes
- Defines when data is sent to client or host

| **SPI mode** |                                                        |
| ------------ | ------------------------------------------------------ |
| 0            | Samples the data line on the rising edge of the clock  |
| 1            | Samples the data line on the falling edge of the clock |
| 2            |                                                        |
| 3            |                                                        |
# MicroWire $\mu$Wire
- Subset of SPI
- 3 wire mode
- Uses a single data line instead of two
- Unidirectional communication

# Registers
`CTRLA`
- Data order indicates if LSB or MSB first
- Indicate if client or slave
- Can indicate clock prescaler
- Enable or disable peripheral

`CTRLB`
- Enable buffer mode - 
	- 2 receive buffers, 1 transmit buffer
- Client disable mode - 