# What is KV?
[KV Explained](https://www.youtube.com/watch?v=uvyi6hPIt8w)

- How fast you spin for what voltage you input
	- Test: spin the motor w/ known voltage and no load. Measure the rpm
	- The lower the KV, the greater the back emf
	- Low KV means thinner wire (not sure why)
$$
KV=\frac{RPM_{\text{no load}}}{V_{\text{ back emf}}}
$$
- As motor turns the direction of the magnetic field across the coil reverses (changes very abruptly) so there is a large back emf
![[Pasted image 20240923203302.png]]

- Back EMF increases w/ strength of magnet, speed of motor, and number of coil turns
- Increasing the number of turns adds a little more back-emf
$$
V=-N \frac{\Delta \Phi_{B}}{dt}
$$
- Back EMF of a motor eventually cancels out the applied voltage so it cannot spin any faster, which is why it eventually stops accelerating.

- When the motor is under load, $V_{\text{back emf}} \neq V_{s}$ (presumably because it is not spinning as fast as no load?) 
- Because $V_{\text{back emf}} \neq V_{s}$ ,  the motor is able to push current into the motor and converts it in to mechanical power
$$
P=I_{m}V_{\text{back emf}}
$$
![[Pasted image 20240923203627.png]]

- Suppose both systems have the same power input. System A has higher KV but lower voltage but system B has lower KV but higher voltage
- In order for the power dissipated by the 4s motor to equal that of the 8s motor, the resistance of the 4s motor must be 1/4 that of the 8s
	- Since higher current in system A, much more power is dissipated

- In theory it is possible to get 1/4 the resistance since system A has half the length and presumably same amount of copper (so 2x cross-section)
	- so $\text{Resistance}=\rho(\frac{length}{\text{area}})$
	- There is a limit to how thick the stranding can be made.

![[Pasted image 20240923205832.png]]
- Multi-strand wires are used to increase cross-sectional area but this significantly reduces heat dissipation

## Pros/Cons of higher voltage
- Lower currently and less energy loss from all components
- Low KV means more turns and worse coolin
# Motor controllers
[[E-bikes#Motor controller]]

- **1)** It converts the DC voltage of the battery pack into 3 phase alternating current for the motor windings without which the motor could not spin, and
- **2)** It can continuously adjust the voltage going to the motor, from 0V up to the full battery pack voltage, in response to the user's throttle signal, pedal sensors, and various current limits.

the controller acts as an efficient DC-DC buck converter. While it steps down the voltage going to the motor, it simultaneously steps up the current by the same ratio. You can have 48V and 10 amps flowing from the battery into the motor controller, and have 24V and 20 amps flowing from the controller to the motor

A small low current motor controller might be rated for 14 amps, which means it will only draw a maximum of 14 Amps from the battery pack. When the motor attempts to draw more current than this, the controller then automatically reduces the voltage provided to the motor in order to keep the battery current draw right at the limit
