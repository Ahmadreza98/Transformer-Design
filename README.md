# Transformer-Design
In this repository, I intend to design the transformer in the electrical machine design course, which is part of the electrical engineering courses in the master's degree.
## Introduction
To design the transformer based on the information provided by the employer, the transformer must be designed, which includes:
1. The primary voltage of the transformer.
2. The secondary of the transformer.
3. Number of transformer phases.
4. Transformer working frequency.

In the design of a transformer, there are variables that, in order to optimize the important parameters and place them in the desired range, we must constantly change the variables to reach our desired results, these variables are:
1. Flow density.
2. "K" coefficient to calculate volts per turns of the transformer.
3. Calculation of volts per turn "Et" of the transformer.
4. "Kw" window space factor of the transformer.
5. The coefficient of the window space factor Cf of the transformer.
6. The current density of the low voltage winding in terms of amperes per square millimeter. 
7. The current density of the high voltage winding in terms of amperes per square millimeter.
8. Average current density of high and low voltage windings to calculate the dimensions of the transformer core.
9. Transformer iron density.
10. Density of transformer winding copper.
11. Insulation thickness of high voltage transformer winding.
12. Insulation thickness of low voltage transformer winding.
13. The ratio of the length of the window to the width of the window of the transformer core.
14. "Ki" the area coefficient of the transformer core column.

**Some of the above parameters are implicit and do not need to be changed, so we only discuss variable values.**

## Magnetic frame design (stage one)
In the first step, we must design the dimensions of the core so that we can check other steps such as calculating the short circuit current, high and low voltage winding, etc. So we have:

 1. First, we have to calculate the cross-sectional area of the transformer core:
	> $$ A_i = \dfrac{E_t}{4.44\times f_s \times B_m} $$
 2. Calculate the effective diameter of the transformer core:
	 > $$ d_i = \sqrt(\dfrac{A_i}{K_i}) $$
 3. Calculate the area of the transformer window:
	 > $$ A_w = \dfrac{S}{3.33\times f_s\times B_m\times A_i\times K_w\times\delta_{avg}} $$
 4. Calculate the width of the transformer core window:
	 > $$ b_w = \sqrt(\dfrac{A_w}{\alpha}) $$
 5. Calculate the height of the transformer core window:
	 > $$ h_w = b_w \times \alpha $$
 6. Calculation of the effective length between two columns of the transformer core:
	 > $$ D = d_i + b_w $$
 7. Calculation of the cross-section of the transformer core and yokes:
	- *We assume them to be equal for simplicity of calculations.*
	> $$ A_i = A_y $$
 8. Calculate the length of the transformer yoke:
	  > $$ W = 2\times D + 0.9\times d_i $$
 9. Calculate the width of the transformer yoke:
	  > $$ b_y = 0.9\times d_i $$
 10. Calculate the height of the transformer yoke:
	  > $$ h_y = \dfrac{A_y}{b_y} $$
 
 ** The calculated parameters are all in meters, meters, square meters, cubic meters.**
