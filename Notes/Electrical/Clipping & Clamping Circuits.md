# Clipping circuits
Clipping circuits cutoff the output of a circuit at certain voltage intervals
## Solution process
1. Consider cases when a diode is forward biased and reverse biased.
2. Apply KVL around a loop containing the diode
	1. Assume that the resistor in the loop is experiencing a voltage $>0$
3. Use the inequality to find the condition when the diode is on
4. Create a new loop that relates $V_{out}$ and $V_{in}$

## Positive Series Clipper
![[posseriesclipper.png]]
**Diode on (Loop #1)**:

$$
\begin{align} \\
V_{in}+&V_{R}+V_{f}=0 \\
&V_{R} = - V_{in} - V_{f} > 0 \\
&\boxed{ V_{in} < - V_{f}} \\
\end{align}
$$
Therefore the diode is on when $V_{in} < - V_{f}$
Create a loop that goes all the way around the outside so
$$
\begin{align}
-V_{in}-V_{f}+V_{out} = 0 \\
\boxed{V_{out} = V_{in} + V_{f}}
\end{align}
$$
Therefore the output is $V_{in}+ V_{f}$ when the diode is on (aka $V_{in} < - V_{f}$)


**Diode off**
The negation of the inequality says the diode is off when $V_{in}\geq -V_{f}$
When the diode is off there is no potential difference across $V_{out}$

## Negative series clipper
## Negative biased series clipper
## Unbiased parallel positive clipper
## 2 diode parallel clipper

# Clamping Circuits
Clamping circuits shift the whole signal up or down depending on the type.
## Max clamping
## Min clamping

# Related documents
[[Inkscape#Circuit Symbols for Diagrams]]
