![[Pasted image 20240614095900.png]]

# Code area
- Code starts are `0x0000 0000`
- **System memory** - ROM reserved for bootloaders
- **Option bytes** - bit flags to enable MCU features (flash read, watchdog, etc)

# # Bit banding
- This is inefficient b/c we have fetch, modify, and save 3 times. Also if there is concurrent operation we want to make sure this is completed in a single cycle
```c
uint8_t temp = 0;
temp |= 0x4; // set 3rd bit
temp &= ~0x4; // clear 3rd bit
```
- *Bit banding* allows us to atomically address/access single bits
	- Every bit in memory is assigned to a whole [[Embedded C#Word size|word size]]
	- This is only in the aliased memory region 

 ```c
bit_band_address = alias_region_base + (region_base_offset x 32) + (bit_number x 4)

// Access the 2nd bit (0 indexed)
alias_region_base = 0x22000000
region_base_offset = 0x20000000 - 0x20000000 = 0
bit_band_address = 0x22000000 + 0*32 + (0x2 * 0x4) = 0x22000008
```

![[Pasted image 20240614101252.png]]
- a 32-bit word in "alias" memory refers to a bit in the "bit band" region
	- Cortex-M3 has two 1Mb "bit band" regions (meaning bits are addressable from the alias which are 32Mbit)

**Example**: Accessing GPIOA defined at 0x40020014
![[Pasted image 20240614103041.png]]

- Each bit of word at 0x40020014 in bit band region can modify the output state of a GPIOA pin
- To modify PIN5 of GPIOA port
```c
alias_region_base = 0x42000000 // alias region starts here
region_base_offset = 0x40020014 - 0x40000000 = 0x20014 // how far up we are in the band region

// 1) start in alias region. 
// 2) To refer to the word we want in alias region we have to multiply the region_base_offset by the size of a word
// 3) 4 bits in bit band alias corresponds to the next 1 bit in bit_band space
bit_band_address = 0x42000000 + 0x20014*32 + (0x5 * 0x4)

```
