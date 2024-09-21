[[AVR128DB28 Datasheet.pdf#page=29|p.29]]
1 word = 16 bits
`X` = don't care value
`Z` = High impedance floating state for a signal or bus

> [!PDF|yellow] [[AVR128DB28 Datasheet.pdf#page=19&selection=599,0,614,1&color=yellow|AVR128DB28 Datasheet, p.19]]
> > Pin names are of type Pxn, with x being the PORT instance (A, B, C, ...) and n the pin number. Notation for signals is PORTx_PINn
# Registers & Bits [[AVR128DB28 Datasheet.pdf#page=30|pg.30]]

| Symbol                     | Description                                                                                                                                                                                                                                                                                                                                          |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`R/W`**                  | Read and write access                                                                                                                                                                                                                                                                                                                                |
| **`BITFIELD[n:m]`**        | Set of bits from bit n down to m, inclusive.<br><br>ex: `PINA[3:0] = {PINA3, PINA2, PINA1, PINA0}.`                                                                                                                                                                                                                                                  |
| **`Reserved`**             | Reserved bits/bit fields are unused and reserved for future use. Always write reserved bits to ‘0’ when the register is written. Reserved bits will always return zero when read.                                                                                                                                                                    |
| **`PERIPHERAL(n/x)`**      | If several instances of peripheral exist `n/x` is selected to refer to a single on<br><br>ex: `USARTn - USART1`, `PORTx - PORTA`                                                                                                                                                                                                                     |
| **`Reset`**                | Value of register after Power-on Reset.                                                                                                                                                                                                                                                                                                              |
| **`SET/CLR/TGL`** (suffix) | A single register (ex: `PORT`) have  additional registers available for direct SET/CLR/TGL. This avoids read-modify-write operations.<br><br>In the PORT peripheral<br>- Writing `1` to `CLR` will clear bit in PORT register<br>- Writing `1` to `SET` with set the bit in PORT register<br>- Writing `1` in `TGL` will toggle bit in PORT register |

^cf7c80
# Register to Header File conversion
[[AVR128DB28 Datasheet.pdf#page=30&selection=110,0,138,54&color=yellow|AVR128DB28 Datasheet, p.30]]
 - A register is identified by `<peripheral_instance_name>.<register_name>`, 
	 - ex: CPU.SREG, USART2.CTRLA, or PORTB.DIR
- The peripheral name is given in the [[Peripheral Address Map]]
- `<peripheral_instance_name>` is obtained by substituting any `n` or `x` in the peripheral name with the correct instance identifier.
- When assigning a predefined value to a peripheral register, the value is constructed following the rule: `<peripheral_name>_<bit_field_name>_<bit_field_value>_gc`
	- Bit field names are found in [[Register Descriptions]]
```c
// peripheral name w/o instance identifier: USART
// bit field name: RXMODE
// bit field value: CLK2X
USART_RXMODE_CLK2X_gc
```

- For peripherals with different register sets in different modes, `<peripheral_instance_name>` and `<peripheral_name>` must be followed by a mode name, for example
```c
// TCAO in Normal Mode (SINGLE) uses waveform generator in frequency mode
TCA0.SINGLE.CTRL=TCA_SINGLE_WGMODE_FRQ_gc;
```
