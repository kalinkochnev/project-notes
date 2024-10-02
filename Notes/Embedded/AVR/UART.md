[[Notes/Embedded/STM32/UART|UART]]

Universal Sychronous/Asynchronous Receiver Transeiver (USART)
- Asynchronous mode communicates over 3 wire cable (TX, RX, GND)
- Full duplex (can transmit/receive simultaneously)

![[Pasted image 20240911144912.png]]

# Physical layers
## RS-232
![[Pasted image 20240911143627.png]]

- Logic 1 = $[-15, -3]$
- Logic 0 = $[3, 15]$
- Needs level shifter (MAX232 chip)
## USB
- FTDI chip converts UART protocol to USB


# Frame format
- 8 data bits, one parity bit, one stop bit (10 total)
- Wire is at logic high when not in use
- Start bit pulls voltage to low at start of frame
- Odd parity = odd number of 1s, parity bit should be 0
- Clock starts when falling edge is received

# Baud Rate
- Essentially means bits/second
- Each byte of data takes 10 bits. So 9600 baud = 960 bytes/second (1ms per byte)
- Cable limits the baud rate

## Registers
- USARTn.BAUD is a 16 bit register needs to be set
![[Pasted image 20240911145204.png]]

- RXDATA is two registers combined (RXDATAH, RXDATAL) since UART may have up to 9 data bits
![[Lecture 4.pdf#page=11]]

# Bit sampling
- By default the clock takes 16 samples/bit.
	- Majority vote on the middle 3 samples determines value
- The sender and receiver may be using different clocks. The higher sample rate allows to account for difference in clock speeds within 2%

# Printing floats
![[Lecture 8.pdf#page=30|Lecture 8, p.30]]

# Examples
## Initialization
## Transmit
```c
int USART_Transmit(char c) {
 // Bitmask has bit position corresponding to the status bit = 1, 0 otherwise
 // Loop while the DREIF (output pipline) is full
 while ( !(USART3.STATUS & USART_DREIF_bm) );
 USARTT3.TXDATAL = c;

 return 0;
}
```

## Receive
```c
/*
* Perform UART startup initialization.
*/
FILE* uart_init(uint8_t usart_num, uint32_t baud_rate, FILE* stream);
```
- Stream is set to stdout, stdin, stderr steams if `stream=NULL`