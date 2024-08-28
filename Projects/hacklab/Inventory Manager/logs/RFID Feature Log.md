# 8/15/24
- [x] Implement transmit/receives implementations for serial in `serial_reader_dummy.c`
- [ ] Test UART communication from esp32

- Be warned of auto-imports. They can break things unintentionally.

- Important files: `serial_transport.h`
	- `TMR_SR_SerialTransport` struct is the abstraction for the communication with the specific platform
## API Notes
> [!PDF|yellow] [[M6E-NANO Datasheet.pdf#page=14&selection=20,14,20,99&color=yellow|M6E-NANO Datasheet, p.5]]
> > host processor’s receiver must have the capability to receive up to 256 bytes of data



> [!PDF|yellow] [[M6E-NANO Datasheet.pdf#page=14&selection=45,5,45,74&color=yellow|p.5]]
> >  Upon initial power up, the default baud rate of 115200 will be used.


[[API]]
[[M6E-NANO Datasheet.pdf]]

# 8/13/24
Here is an example on how to integrate esp32 components 
https://github.com/martinberlin/cale-idf/tree/master/components



# 8/9/24
The thingmagic api is so good and well thought out... Thank god. At least on the surface it appears that way. Thankfully they abstracted all of the hardware specific details and I only need to implement a few functions hopefully! It seems super doable though. And the [[Projects/hacklab/Inventory Manager/Baremetal_Interfacing_Guide.pdf|Baremetal_Interfacing_Guide]] seems to have wiring instructions as well. 

Follow `README.PORTING` for specific instructions. 
- [x] Enable bare metal mode in `tm_config.h`  with 
- [x] Implement `osdep_dummy.c` which includes timer and sleep functions
- [ ] Implement transmit/receives implementations for serial in `serial_reader_dummy.c`

[Initializing uart esp32](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/uart.html)

I made an outline of the MVP [[Site MVP]]

# 7/31/24
- [ ] Create `Serial` interface that makes use of ESP32 methods
	- [ ] `write()`
	- [ ] `read()`
	- [ ] `destructor`
	- [ ] `available()`
	- [ ] `flush()`

# 7/17/24
## Recap
- Someone already implemented an esp32 repository that makes use of the Sparkfun Simultaneous RFID reader. Sparkfun provides a driver, but this guy made improvements to it. 
- Drawbacks: it uses the Arduino API. I'm trying to learn FreeRTOS so this is a non-starter
- I am planning on reworking the library to use FreeRTOS types.
	- [ ] Replace Arduino `Serial` , `Stream`, `millis()`, `F()`, `boolean`, `HEX`
	- [ ] Enable variable length arrays for C++ compilation
	- [ ] Unknown typename "class" in `UHF_RFID_Reader.h`. Doesn't seem to recognize the header file is C++ not C

## Resources
[ESP32 UART/Serial Communication](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/uart.html)
[Establishing serial communication ESP32](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/establish-serial-connection.html)
[[M6E-NANO Datasheet.pdf]]
[Other documentation on dev board](https://www.sparkfun.com/products/14066#documents-tab)
[[ThingMagic-MercuryAPI-Programmer-Guide-1_37_3.pdf|Mercury API Programmers Guide]]
[[Baremetal_Interfacing_Guide.pdf|Mercury API Bare Metal Guide]]