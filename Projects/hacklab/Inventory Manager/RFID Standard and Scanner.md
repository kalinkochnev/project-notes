https://learn.sparkfun.com/tutorials/rfid-basics

Tutorial: https://learn.sparkfun.com/tutorials/simultaneous-rfid-tag-reader-hookup-guide/introduction

# Gen2 UHF RFID Memory Standard
Memory is split into 

#### Tag Identifier Memory (TID)
Unique tag identifier that is encoded with every RFID ($1.46 \cdot 10^{48}$ possible)
#### Electronic product code memory (EPC)
User editable. Sort of like a barcode meant to identify things specific to the user (like milk for ex)
#### User memory
Between 0 to 64 bytes. Extra data to be associated with EPC (like expiration date for milk ex)



# M6E-NANO
https://learn.sparkfun.com/tutorials/simultaneous-rfid-tag-reader-hookup-guide/hardware-overview
- Controlled via serial through either hardware (HW-UART) or software (SW-UART)
	- no idea what the difference is
![[Pasted image 20240412171341.png]]

## Pins

| 9, 10 | PWM controlled buzzer |
| ----- | --------------------- |
|       |                       |
