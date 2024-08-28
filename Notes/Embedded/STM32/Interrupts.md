
## Interrupts
![[Pasted image 20240618110456.png]]

- [[Mastering STM32.pdf#page=146]]

![[Pasted image 20240618105658.png]]

# Enabling Interrupts
- Reset, NMI, Hard Fault are exceptions enabled by default. 
	- Remaining interrupts have to be enabled using `void HAL_NVIC_EnableIRQ(IRQn_Type IRQn)`
	- Disabling interrupts `void HAL_NVIC_DisableIRQ(IRQn_Type IRQn);`
	- Peripherals must also be configured to be interrupted if used
- Available interrupts are found in `Drivers/CMSIS/Device/ST/STM32XXxx/Include/stm32XXxx.h`

## Example:
- Use an interrupt to toggle LD2 LED every time we press user programmable button

1) Configure PC13 GPIO to fire an interrupt
2) Enable the interrupt of EXTI line associated with Px13 which is EXTI15_10_IRqn
3) EXTI15_10_IRQHandler() indicates which pins to trigger interrupt on
4) HAL_GPIO_EXTI_Callback triggers and checks which pin caused interrupt and then does something
```c
int main(void) {
  GPIO_InitTypeDef GPIO_InitStruct = {0};

  /* MCU Configuration----------------------------------------------------------*/
  /* Reset of all peripherals, Initializes the Flash interface and the Systick. */
  HAL_Init();
  /* Configure the system clock */
  SystemClock_Config();

  /* GPIOA and GPIOC Configuration----------------------------------------------*/
  /* GPIO Ports Clock Enable */
  __HAL_RCC_GPIOC_CLK_ENABLE();
  __HAL_RCC_GPIOA_CLK_ENABLE();

  /*Configure GPIO pin : PC13 */
  GPIO_InitStruct.Pin = GPIO_PIN_12 | GPIO_PIN_13;
  GPIO_InitStruct.Mode = GPIO_MODE_IT_RISING;
  GPIO_InitStruct.Pull = GPIO_PULLDOWN;
  HAL_GPIO_Init(GPIOC, &GPIO_InitStruct);

  /*Configure GPIO pin : PA5 */
  GPIO_InitStruct.Pin = GPIO_PIN_5;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);

  /* Configure GPIO pin Output Level */
  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);

  /* EXTI interrupt init*/
  HAL_NVIC_EnableIRQ(EXTI15_10_IRQn);

  while (1);
}

void EXTI15_10_IRQHandler(void) {
	HAL_GPIO_EXTI_IRQHandler(GPIO_PIN_12);
	HAL_GPIO_EXTI_IRQHandler(GPIO_PIN_13);
}

void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin) {
	if(GPIO_Pin == GPIO_PIN_13)
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, SET);
	else if(GPIO_Pin == GPIO_PIN_12)
		HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, RESET);
}
```
![[Pasted image 20240618112807.png]]

# Methods
`uint32_t HAL_NVIC_GetPendingIRQ(IRQn_Type IRQn);`
- See if an interrupt is pending (fired, not running)
- 0 if not pending, 1 if pending

`void HAL_NVIC_SetPendingIRQ(IRQn_Type IRQn)`
- Cause an interrupt to fire
- Can fire an interrupt within an interrupt

`void HAL_NVIC_ClearPendingIRQ(IRQn_Type IRQn);`
- Clear execution of pending interrupt

`uint32_t HAL_NVIC_GetActive(IRQn_Type IRQn);`
- Check if ISR is active 

`void HAL_NVIC_SetPriority(IRQn_Type IRQn, uint32_t PreemptPriority, uint32_t SubPriority);`
- Preempt Priority is between $[0, 4]$

`void HAL_NVIC_SetPriorityGrouping(uint32_t PriorityGroup)`
- Priority group is determined by this table
![[Pasted image 20240618122139.png]]

`void HAL_NVIC_GetPriority(IRQn_Type IRQn, uint32_t PriorityGroup, uint32_t* pPreemptPriority, uint32_t* pSubPriority)`
- Gets the priority of an interrupt
- Have to also specify the group in order to compute the priority

`uint32_t HAL_NVIC_GetPriorityGrouping(void)`
- Can retrieve current priority

# Subpriority
- The priority register (IPR) can be divided into "preempty" and "subpriority"
	- Subpriority breaks ties between IRQ with the same preemption priority
- Whatever grouping of priority bits, it then applies to all interrupts
- Priority groupings can be changed dynamically 
![[Pasted image 20240618121830.png]]

# Masking
- Sometimes you want to make sure that your code is not preempted
- Registers `PRIMASK` and `FAULTMASK` allow disaling 
- Mask only for short periods of time to avoid losing on important interrupts

```c
...
__disable_irq();
/* All exceptions with configurable priority are temporarily disabled.
You can place critical code here */
...
__enable_irq();
```