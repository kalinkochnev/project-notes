![[Pasted image 20240618124129.png]]

![[Pasted image 20240618124353.png]]

# Basic timers
```c
typedef struct {
	TIM_TypeDef *Instance; /* Pointer to timer descriptor */
	TIM_Base_InitTypeDef Init; /* TIM Time Base required parameters */
	HAL_TIM_ActiveChannel Channel; /* Active channel */
	DMA_HandleTypeDef *hdma[7]; /* DMA Handlers array */
	HAL_LockTypeDef Lock; /* Locking object */
	__IO HAL_TIM_StateTypeDef State; /* TIM operation state */
} TIM_HandleTypeDef;
```
- `Instance` - pointer to TIM descriptor (ex TIM6 refers to one of basic timers available)
- `Init` - instance of `struct TIM_Base_InitTypeDef` which configures base timer functionalities
- `Channel` - number of active input/output channels (not available for basic timers)
- `*hmda` - pointer to array of descriptors to DMA requests associated w/ timer
- `State` - used by HAL to keep track of state

## Configuration
```c
typedef struct {
	uint32_t Prescaler; /* Specifies the prescaler value used to divide the TIM clock. */
	uint32_t CounterMode; /* Specifies the counter mode. */
	uint32_t Period; /* Specifies the period value to be loaded into the active
	Auto-Reload Register at the next update event. */
	uint32_t ClockDivision; /* Specifies the clock division. */
	uint32_t RepetitionCounter; /* Specifies the repetition counter value. */
} TIM_Base_InitTypeDef;
```
- `Prescaler` divides timer clock by factor from 1 up to 65535 (prescaler register has 16 bit resolution)
- `CounterMode` defines counting direction. Basic timers only `TIM_COUNTERMODE_UP`. 
- `Period` - max value for timer before it restarts `[0x1, 0xFFFF]` for 16 bit or `0x1, 0xFFFF FFFF` for TIM2/TIM5 timers that implement 32 bit
	- `0x0` stops timer from starting
- `ClockDivision` a more advanced feature
- `Repetition counter` - every timer has an "update" register that keeps track of timer overflow conditions. Counts number of times timer overflows before the overflow timer event is raised. *Only used for advanced timers*