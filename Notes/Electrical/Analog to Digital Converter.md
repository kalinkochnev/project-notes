https://www.electronics-tutorials.ws/combination/analogue-to-digital-converter.html
![[Pasted image 20240611121907.png]]

- Can have a line of resistors with "steps down" in reference voltage that serves as the point of comparison with an input signal.
	- The comparator compares the reference voltage to the actual input voltage.
	- If `Vin < Vref` the output is `0`
	- If `Vin > Vref` the output is `1`
	- $2^{n}-1$ comparators are needed to convert to an $n$ bit binary output


![[Pasted image 20240611121432.png]]

- The first comparator that triggers to be 1 is the value that we care about. And we translate it to binary using a decoder
![[Pasted image 20240611121849.png]]