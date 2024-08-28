
![Helpful Video](https://www.youtube.com/watch?v=CAvawEcxoPU)
![[Pasted image 20240618134225.png]]
- Two wire communication protocol.
	- Each wire is a birdirectional [[Open Drain vs Open collector|open drain line]]
	- One wire is called Serial Data Line (SDA), the other is Serial Clock Line (SCL)
- All transactions are initiated and completed by the master
- Message contain *address frame* + *data frame* (8 bits)
	- Data frames can be from Master (Controller) -> Slave (Client) or vice versa


# Limitations
- The number of addressable I2C is limited by the number of pins to configure address
- Number of clients on bus is limited by capacitance
	- Pull up time depends on the bus capacitance
- High resistance limits bus speed, low resistance allows faster communication but higher power
# SDA/SCL
- **SDA** (serial data) - data is placed when SCL is *low*, data is sampled/read when SCL is *high*
	- time in-between clock edges defined by devices on the bus
	- SDA only transitions when the clock is LOW. **Otherwise it is read as a START/STOP bit**
- **SCL** (serial clock) - carries the clock signal


# Protocol
1) Every transaction begins and ends with a START and STOP bit
	1) **START** bit -  HIGH to LOW (SDA) while SCL=HIGH
	2) **STOP** bit - LOW to HIGH (SDA) while SCL=HIGH
2) Master sends on the bus the address of the slave device
3) R/W bit is sent (LSB of slave address byte) establishes direction of data
	1) 0 = controller wants to write to client
	2) 1 = controller wants to read from client
4) **Multiple bytes may be sent on one I2C frame**, each one interleaved with ACK bits
	1) ACK bit is sent from the client
	2) 0 = acknowledged (ACK)
	3) 1 = negative acknowledgement = lack of response (NACK)
	4) ACK after data indicates receipt of data
	5) ACK after address indicates address exists and ready to read/write
5) When the bus is free, both lines are *HIGH*

![[Pasted image 20240618141819.png]]

- Every word on SDA must be 8 bits. Address frame must also be 8 bits
- Every byte must be followed by an **Acknowledge (ACK)** bit
- Data is transferred with MSB first
- Client can force the controller to wait by holding the clock line *LOW* in order to complete some kind of function

# Modes
![[Pasted image 20240618142052.png]]

# CubeHAL
```c
typedef struct {
	I2C_TypeDef *Instance; /* I²C registers base address */
	I2C_InitTypeDef Init; /* I²C communication parameters */
	uint8_t *pBuffPtr; /* Pointer to I²C transfer buffer */
	uint16_t XferSize; /* I²C transfer size */
	__IO uint16_t XferCount; /* I²C transfer counter */
	DMA_HandleTypeDef *hdmatx; /* I²C Tx DMA handle parameters */
	DMA_HandleTypeDef *hdmarx; /* I²C Rx DMA handle parameters */
	HAL_LockTypeDef Lock; /* I²C locking object */
	__IO HAL_I2C_StateTypeDef State; /* I²C communication state */
	__IO HAL_I2C_ModeTypeDef Mode; /* I²C communication mode */
	__IO uint32_t ErrorCode; /* I²C Error code */
} I2C_HandleTypeDef;
```

## Methods
#### Polling mode
```c
HAL_StatusTypeDef HAL_I2C_Init(I2C_HandleTypeDef *hi2c)
```
- Configure I2C peripheral

```c 
HAL_StatusTypeDef HAL_I2C_Master_Transmit(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size, uint32_t Timeout)
```
- Perform transaction in write mode
- `hi2c` identifies the I2C peripheral
- `DevAddress` is the address of the slave device
- `*pData` and `Size` are the array we want to transmit
- Timeout can be HAL_MAX_DELAY (0XFFFF FFFF)
- -> Returns HAL_OK if no errors, HAL_TIMEOUT if errors

#### Interrupt mode

```c
HAL_StatusTypeDef HAL_I2C_Master_Transmit_IT(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size);

HAL_StatusTypeDef HAL_I2C_Master_Receive_IT(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size);
```


# Interrupts
- Have to enable interrupts under Pinout & Configuration > Connectivity > I2C > NVIC Settings 

| Interrupt Event                                  | Event Flag | Enable Control Bit |
| ------------------------------------------------ | ---------- | ------------------ |
| Start Bit Sent (Master)                          | SB         | ITEVFEN            |
| Address Sent (Master) or Address Matched (Slave) | ADDR       | ITEVFEN            |
| 10-bit Header Sent (Master)                      | ADD10      | ITEVFEN            |
| Stop Received (Slave)                            | STOPF      | ITEVFEN            |
| Data Byte Transfer Finished                      | BTF        | ITEVFEN            |
| Receive Buffer Not Empty                         | RxNE       | ITEVFEN & ITBUFEN  |
| Transmit Buffer Empty                            | TxE        | ITEVFEN & ITBUFEN  |
# Examples
```c
hi2c3.Instance = I2C3; // Configures the peripheral memory address
hi2c3.Init.Timing = 0x10909CEC; // Configures the I2C_TIMINGR register
hi2c3.Init.OwnAddress1 = 0; // the adddress
hi2c3.Init.AddressingMode = I2C_ADDRESSINGMODE_7BIT;
hi2c3.Init.DualAddressMode = I2C_DUALADDRESS_DISABLE;
hi2c3.Init.OwnAddress2 = 0;
hi2c3.Init.OwnAddress2Masks = I2C_OA2_NOMASK;
hi2c3.Init.GeneralCallMode = I2C_GENERALCALL_DISABLE;
hi2c3.Init.NoStretchMode = I2C_NOSTRETCH_DISABLE;
```

# Direct Memory Access

![[STM32 HAL Documentation.pdf#page=541]]
# Hands on notes
- Sequential communications use a START, RESTART, and END frame. 
	- RESTART reverses the direction of communication
- How do you know which callbacks to use for which interrupts? Look at the [[STM32 HAL Documentation.pdf]]!! This is when I started to finally know what was going on
- I was confused on what the point of the I2C interrupts were if we had to block on them anyways
	- [See the example that confused me]()
	- [See stack overflow for some advice](https://stackoverflow.com/questions/71970334/stm32-i2c-interrupt-method-requires-a-blocking-while-loop)
- This [github repo](https://github.com/STMicroelectronics/STM32CubeL4) has lots of examples!