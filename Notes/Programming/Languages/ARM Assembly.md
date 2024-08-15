- Each operation always involves CPU registers (except for `load` and `store` which transfers from CPU register to memory)

```assembly
; "a" is known as register r7 with offset #7
; "b" is known as register r7 with offset #6
; "c" is known as register r7 with offset #5
movs r3, #3 ;move "3" in register r3
strb r3, [r7, #7] ;store the content of r3 in "a"
movs r3, #2 ;move "2" in register r3
strb r3, [r7, #6] ;store the content of r3 in "b"
ldrb r2, [r7, #7] ;load the content of "a" in r2
ldrb r3, [r7, #6] ;load the content of "b" in r3
smulbb r3, r2, r3 ;multiply "a" with "b" and store result in r3
strb r3, [r7, #5] ;store the result in "c"
```