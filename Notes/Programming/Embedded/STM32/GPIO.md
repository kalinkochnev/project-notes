# I/O Port Structure
![[Pasted image 20240618101943.png]]

# Method signatures
`HAL_GPIO_Init(GPIO_TypeDef *GPIOx, GPIO_InitTypeDef *GPIO_Init)`
- Initializes the configuration of the pin

`GPIO_PinState HAL_GPIO_ReadPin(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin)`
- GPIO_PIN is the pin number $[0, n]$
- Read the pin state. `GPIO_PIN_RESET` when low, `GPIO_PIN_SET` when high

`void HAL_GPIO_WritePin(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin, GPIO_PinState PinState)`
- GPIO_PIN is the pin number $[0, n]$
- `GPIO_PIN_RESET` when low, `GPIO_PIN_SET` when high

`void HAL_GPIO_TogglePin(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin)`

`HAL_StatusTypeDef HAL_GPIO_LockPin(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin).`
- Lock the configuration of the IO. Attempts to modify will fail until a reset occurs

`void HAL_GPIO_DeInit(GPIO_TypeDef *GPIOx, uint32_t GPIO_Pin)`
- Sets the pin to default reset status (input floating mode)
- Avoids wasting power when in sleep mode
# Struct declarations
## GPIO_TypeDef
- Is a struct representation of a register for GPIO configuration
- Often points to an address to the address of a peripheral (ex GPIOA) to enable access in a struct form
- See page [[Mastering STM32.pdf#page=136]]
```c
typedef struct {
	volatile uint32_t MODER;
	volatile uint32_t OTYPER;
	volatile uint32_t OSPEEDR;
	volatile uint32_t PUPDR;
	volatile uint32_t IDR;
	volatile uint32_t ODR;
	volatile uint32_t BSRR;
	volatile uint32_t LCKR;
	volatile uint32_t AFR[2];
	volatile uint32_t BRR;
} GPIO_TypeDef;
```


## GPIO_InitTypeDef
- A struct to actually configure the usage of the pin
- See page [[Mastering STM32.pdf#page=136]]
```c
typedef struct {
	uint32_t Pin;
	uint32_t Mode;
	uint32_t Pull;
	uint32_t Speed;
	uint32_t Alternate;
} GPIO_InitTypeDef;
```

- `Pin` is a bit mask that configures a pin. Ex `001 | 010` says that we will configure pin 1 and 2 using this configuration
- `Mode` changes the operating mode of the pin and can assume any of the values in this table:
![[Pasted image 20240618101241.png]]
- `Pull` - has options of `GPIO_NOPULL`, `GPIO_PULLUP`, `GPIO_PULLDOWN`
- `Speed` - a range of switching speeds for the pin as constants
- `Alternate` - internal peripherals can be exposed to pins on the MCU


# Using direct register write (example)
**Example**: Write to GPIOA peripheral, enable PA5 as an output and pull the pin to High
![[Pasted image 20240617161231.png]]
1) Set the mode of the pin to be using the `MODER`  register (MODE-register).
	1) For pin 5, it is register MODER4 and to enable general purpose output write `01`
![[Pasted image 20240617161500.png]]
2) Set the value of the pin to be HIGH using the `ODR` (output data register)
	1) The offset from the start of the peripheral (0x48000000) is 0x14
	2) Set the bit to 1
```c
int main(void) {
	volatile uint32_t *GPIOA_MODER = 0x0, *GPIOA_ODR = 0x0;
	
	GPIOA_MODER = (uint32_t*)0x48000000; // Address of the GPIOA->MODER register
	GPIOA_ODR = (uint32_t*)(0x48000000 + 0x14); // Address of the GPIOA->ODR register
	
	//This ensures that the peripheral is enabled and connected to the AHB1 bus
	__HAL_RCC_GPIOA_CLK_ENABLE();
	
	*GPIOA_MODER = *GPIOA_MODER | 0x400; // Sets MODER[11:10] = 0x1
	*GPIOA_ODR = *GPIOA_ODR | 0x20; // Sets ODR[5] = 0x1, that is pulls PA5 high
	while(1);
	}
}

// OR using the HAL
/*Configure GPIO pin : PA5 */
GPIO_InitStruct.Pin = GPIO_PIN_5;
GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);
```

Usage
```c
GPIO_TypeDef *GPIOA = 0x48000000;
GPIOA->MODER |= 0x400;
GPIOA->ODR |= 0x20;
```


