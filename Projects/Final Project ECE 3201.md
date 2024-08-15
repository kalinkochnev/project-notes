# Honors project
![[Pasted image 20240424231028.png]]

# Differnetial mode gain



# Final Project
## Common mode gain
At midband, it is -15.167 dB

![[Pasted image 20240423215159.png]]

## Differential gain
`20*LOG10(V(Cout:2)/V(Cin:1))`
Lower cutoff occurs at 36.535dB - 3dB = 33.535 dB
- Occurs at frequency 482.3 Hz
- Gain equivalent to 67.104

![[differentialModePspice.png]]

`V(Cin:1)/I(Cin:1)`
Input impedance: 601.3K (for low frequencies)
Drops below 500K at 106 kHz
![[Pasted image 20240423213943.png]]

Output impedance: 2.4k at low frequencies, at midband frequencies Ro=22.946
![[Pasted image 20240423214649.png]]

## CMRR
$$
\text{CMRR}=\frac{10^{36.535/20}}{10^{-15.167/20}} = 384.68
$$