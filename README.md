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
	> $$A_i=\dfrac{E_t}{4.44\times f_s \times B_m}$$
 2. Calculate the effective diameter of the transformer core:
	> $$d_i=\sqrt{\dfrac{A_i}{K_i}}$$
 3. Calculate the area of the transformer window:
	> $$A_w=\dfrac{S}{3.33\times f_s\times B_m\times A_i\times K_w\times\delta_{avg}}$$
 4. Calculate the width of the transformer core window:
	> $$b_w=\sqrt(\dfrac{A_w}{\alpha})$$
 5. Calculate the height of the transformer core window:
	> $$h_w = b_w \times \alpha$$
 6. Calculation of the effective length between two columns of the transformer core:
	> $$D = d_i + b_w$$
 7. Calculation of the cross-section of the transformer core and yokes:
	- *We assume them to be equal for simplicity of calculations.*
	> $$A_i = A_y$$
 8. Calculate the length of the transformer yoke:
	> $$W = 2\times D + 0.9\times d_i$$
 9. Calculate the width of the transformer yoke:
	> $$b_y = 0.9\times d_i$$
 10. Calculate the height of the transformer yoke:
	 > $$h_y = \dfrac{A_y}{b_y}$$
 
 **The calculated parameters are all in meters, meters, square meters, cubic meters.**

## Core loss (stage two)
In the second step, we have to calculate the core losses. For this, we follow the following steps:
1. Calculate the volume of the transformer core:
	- The transformer is three-phase, so there are three columns in the core.
	> $$vol_{core}=3\times A_i\times h_w$$
2. Calculate the volume of the transformer yokes:
	- The transformer has two yokes, one at the bottom and one at the top.
	> $$vol_{yokes}=2\times A_y\times W$$
3. Calculate total volume of core and yokes:
	> $$vol_{total}=vol_{core} + vol_{yokes}$$
4. Calculate the weight of the transformer core:
	> $$mass_{core}=vol_{core}\times (density&ensp;of&ensp;iron)$$
5. Calculate the weight of the transformer yokes:
	> $$mass_{yokes}=vol_{yokes}\times (density&ensp;of&ensp;iron)$$
6. Calculate total mass of core and yokes:
	> $$mass_{total} = mass_{core} + mass_{yokes}$$
7. Calculation of iron loss per kg, including eddy current:
	-This relationship is modeled on a graph.
	> $$P_{loss}=0.85+1.5792\times (B_m-0.8)+2.8437\times (B_m-0.8)^2-0.104167\times (B_m-0.8)^3+0.78125\times(B_m-0.8)^4 $$
8. Calculation of total iron losses:
	- Usually, due to neglecting some parameters and variables, the total iron losses are considered to be around 5 to 7 percent more.
	> $$P_{loss-total} = P_{loss}\times mass_{total}$$

	> $$P_{loss-total-suggeste} = P_{loss-total}\times (1.05&ensp;or&ensp;1.07)$$

## No-load current (stage three)
In this step, we have to calculate the no-load current of the core, which we do according to the following steps:
1. Calculation of magnetization loss per kg, including Hysteresis:
	>$$S_{loss} = -657.4+2084.458\times B_m-2159.68\times(B_m)^2+736.43\times(B_m)^3$$
2. Calculation of total magnetic losses:
	>$$S_{loss-total} = S_{loss}\times mass_{total}$$
3. Calculation of magnetizing current:
	>$$I_{mag}=\dfrac{S_{loss-total}}{3\times V_{high_{ph}}}$$
4. Calculation of iron loss current:
	>$$I_{iron}=\dfrac{P_{loss-total}}{3\times V_{high_{ph}}}$$
5. Calculation of no-load current:
	>$$I_{no-load}=\sqrt{I_{mag}^2+I_{iron}^2}$$
6. Calculation of no-load current in terms of P.u:
	>$$I_{no-load-p.u}=\dfrac{I_{no-load}}{I_{rated}}$$
	-It can also be expressed as a percentage $$(that&ensp;number) \times 100$$

## Low-voltage winding (stage four)
In this step, one of the main steps is to calculate or choose the number of laps, width, length, insulation thickness, etc., and my other parameters should be within the standard range. The steps of this section are as follows:
1. Calculation of the number of turns of the low voltage winding:
	- The number of rounds must be a multiple of 2. If not, we will round it to the nearest multiple of 2.
	> $$T_2=\dfrac{V_{low_{ph}}}{E_t}$$

- Usually, to place the insulation and the number of turns of the low voltage winding, it is wound in two or more layers so that each one has a distance of a few millimeters from the other.
2. Calculation of low voltage winding current:
	>$$I_2=\dfrac{S}{3\times V_{low_{ph}}}$$
3. Calculation of cross-section of low voltage winding:
	>$$a_2=\dfrac{I_2}{\delta_{LV}}$$
4. Calculation of permissible height for low voltage winding:
	- Usually, 80% of the window height is used for low voltage and 20% is for insulation considerations.
	>$$h_{LV}=h_w\times 0.8$$
5. Calculate the height of each conductor in each layer:
	> $$h_{each-con}=\dfrac{h_{LV}}{\dfrac{T_2}{L}}$$
	- $L$ is the number of layers of the low voltage winding.
- Usually on the low voltage side, because the calculated cross-sectional area is more than the range and cross-sectional area of standard cables, so we have to divide it into 2n strands and arrange them in a special arrangement, for example, $h$ strands in the axial length and $w$ strands in the radial length of the transformer $(h\times w = 2n)$.
6. Calculate the thickness of each strand of wire in each conductor:
	>$$h_{each-strand}=\dfrac{h_{each-con}}{h}$$
- Now, in order to calculate the width of the wire string, we must refer to Table A-5, which are the standard wires that are available to us, and find the cross-section of that string (if such an axial length is not available in the table, you can change the range, but you must be careful changes in other parameters should be within their stability limits).
	>$$table_{A-5} \to w_{each-strand}$$
- After determining the thickness and width of the current wire, 5 mm should be added to both, which is because of the insulation on it.
	>$$ then \to h_{each-strand}+0.5^{mm}\quad w_{each-strand}+0.5^{mm}$$
7. Calculation of modified cross-section with $h_{each-strand-ins}$ and $w_{each-strand-ins}$ listed in table A-5:
	>$$a_{2-strand_{new}}=h_{each-strand-ins}\times w_{each-strand-ins}$$
	- The total cross-section of the conductor:
		>$$a_{2-con_{new}}=a_{2-strand_{new}}\times (h\times w)$$
8. Calculation of the radial length of the low voltage winding:
	- First, add the number of coiled strands radially (for one layer), then multiply by the radial length of each strand to calculate the radial length of each conductor, but we must be aware that we have a low voltage $L$ layer winding, so these dimensions must be as L is multiplied and added with a distance between the existing layers $(L-1)\times (space\:between\:layer)$ to calculate the thickness of the low voltage winding.
	>$$w_{total-winding-LV}=(w\times w_{each-strand-ins})\times L + (L-1)\times (space&ensp;between&ensp;layer)$$
- Now we have to calculate the outer and inner diameter of the low voltage winding. So we do the following:
- We know that the effective radius of the transformer core is equal to $d_i$.
- First, we calculate the insulation between the core and the low voltage winding. The first insulation is the oil channel, which you should refer to Table 5-7 to determine, and since we are calculating the diameter, we should multiply it by 2 and add it to $d_i$.
- The second insulation is called cylindrical insulation, which we must choose from table 5-7 and then double it (Inner radius of low voltage winding).
	>$$d_{inner-radius} = d_i + 2\times (oil&ensp;duct) + 2\times (cylinder)$$
- You need to double the calculated radial length of the low voltage coil to get its diameter (Outer radius of low voltage winding).
	>$$d_{outer-radius}=d_{inner-radius} + 2\times w_{total-winding-LV}$$
9. Calculation of the effective diameter between the inner and outer radius:
	 >$$d_{mean-avg}=\dfrac{d_{inner-radius}+d_{inner-radius}}{2}$$
10. Calculate the length of the low voltage winding:
	>$$L_{mean-winding-LV}=\pi \times d_{mean-avg}$$
11. Calculation of low voltage winding resistance:
	>$$R_{winding-LV}=\dfrac{(Specific&ensp;resistance&ensp;of&ensp;copper)\times L_{LV}\times T_2}{a_{2-con_{new}}}$$
12. Calculation of copper volume of low voltage winding:
	>$$vol_{winding-LV}=T_2\times L_{mean-winding-LV}\times a_{2-con_{new}}$$

## High Voltage Winding (stage five)
At this stage, we have to design the winding of the high voltage section in such a way that it is placed inside the window, and it must be acceptable in terms of height, so we do the following steps to design the high voltage winding:
1. Calculation of the number of high voltage winding turns:
	- The number of turns of the high voltage winding must be a multiple of 2.	
	>$$T_1=\dfrac{V_{high_{ph}}}{V_{low_{ph}}}\times T_2$$
- In transformers, the number of conductor turns in the last round, both from the bottom and from the top, is usually less than the middle part of the transformer, which is for insulation considerations, etc. It should also be noted that each conductor can have a maximum of 100 strands, so we have a capacity limit.
2. Calculate the high voltage winding of the transformer:
	>$$T_{middle}=(number\:of\:turn)_{middle}\times (number\:of\:strand)_{each-con}$$
	- $if\quad T_2-T_{middle} < 200\quad then\quad T_{top}=T_{bottom}=\dfrac{T_2-T_{middle}}{2}$
3. Calculation of high voltage winding current of the transformer:
	>$$I_1=\dfrac{S}{3\times V_{high_{ph}}}$$
4. Calculation of the cross-section of the high voltage winding of the transformer:
	> $$a_1=\dfrac{I_1}{\delta_{HV}}$$
- Now we need to get its diameter from Table A-1 based on the cross-section of the winding.
	>$$ table_{A-1} \to d_{winding-strand}$$
- After determining the diameter of each coil in the high voltage of the transformer, we must add 3 mm to the diameter of the wire, because we must also consider the insulation on it.
	>$$d_{winding-strand-ins} = d_{winding-strand} + 3^{mm}$$
- Note that there may not be a wire with such a cross-section, so consider a wire with a closer cross-section and consider the new cross-section in the problem.
5. Calculation of permissible height for high voltage winding:
	- Usually, 70% of the height of the window is considered as the allowed height, and the remaining 30% is considered for insulation considerations.
	>$$h_{HV}=h_w\times 0.7$$
6. Calculation of the height of each conductor in the high voltage winding:
	>$$h_{each-con}=\dfrac{h_{HV}}{(number\:of\:turns)_{middle}+2}$$
	- Now we need to know how many strands of wire are placed in each conductor along its axial length. For this reason, we divide the height of each conductor by the diameter of each strand of wire with its insulation to determine the number (the desired number must be a trend number or the same number without any decimals).
	>$$h_{number\:of\:strand_{each-con}}=\dfrac{h_{each-con}}{d_{winding-strand-ins}}$$
	- Now we have to multiply the number of turns of the wire strand that is placed axially in each conductor by the diameter of the wire strand with insulation.
	>$$h_{each-con_{new}}=h_{number\:of\:strand_{each-con}}\times d_{winding-strand-ins}$$
7. Calculation of the number of wire strands in the radial axis in the high voltage winding:
	- Now we have to calculate the number of wires in the radial axis. For this, we must divide the total number of wire strands in each conductor by the number of wire strands in the longitudinal axis to calculate the number of wire strands in the radial axis (of course, the desired number must be rounded and not include a decimal number).
	>$$ w_{number\:of\:strand_{each-con}}=\dfrac{(number\:of\:strand)_{each-con}}{h_{number\:of\:strand_{each-con}}}$$
8. Calculation of radial length for high voltage winding:	
	- Now we have to multiply the number of strands of wires calculated in the radial axis by the diameter of the insulated wire to calculate the length of the radial axis.
	>$$w_{radial-axis-winding}=w_{number\:of\:strand_{each-con}}\times d_{winding-strand-ins}$$
9. Calculation of high voltage winding height:
	>$$h_{total-winding_{HV}}=h_{each-con_{new}}\times [(number\:of\:turn)_{middle}+2]$$
	- $if\quad h_{total-winding_{HV}}<h_{HV} \quad then\quad True$
10. Calculation of total height at high voltage:
	- It should also be noted that a spacer should be placed for each conductor, which is at least 4 mm.
	> $$h_{ins-spacer}=4^{mm}\times [[(number\:of\:turn)_{middle}+2]-1]$$
	- We have two end insulators, each equal to 35 mm.
	> $$h_{ins-end}=2\times 35^{mm}$$
	- We have a metal ring insulation which is equal to 20 mm.
	>$$h_{ins-ring}=20^{mm}$$
	- We also put a space filling insulation which is equal to 4 mm.
	>$$h_{ins-slackness}=4^{mm}$$
	- Now we collect all the above items together
	>$$h_{total-winding-ins_{HV}}=h_{total-winding_{HV}}+h_{ins-spacer}+h_{ins-end}+h_{ins-ring}+h_{ins-slackness}$$
	- $if \quad h_{total-winding-ins_{HV}}<h_w \quad then \quad True$
11. Calculation of radial length of high voltage winding:
	- Since the high voltage winding is wound on the low voltage winding, then to calculate the radial length, we must continue it from the outer layer of the low voltage. First, an oil channel must be placed between the high and low voltage windings, which according to Table 5-8 should be (Its values are diagonal, the values should be entered radially and then multiplied by 2) Then it will be added with the value of the external radial length of the low voltage axis and the inner diameter of the insulating cylinder at high pressure will be calculated.
	>$$table_{5-8} \to w_{oil-duct_{between-LV-and-HV}}$$
	- Now we have to calculate the thickness of the insulating cylinder. In high voltage, you should get its value from table 5-8 (if the values are not in the table, use interpolation) and add it with the value of the inner diameter of the insulating cylinder in high voltage to calculate the inner diameter of the high voltage winding.
	>$$table_{5-8} \to w_{culinder_{between-LV-and-HV}}$$
	>$$d_{inner-radius}=d_{outer-radius}+2\times w_{oil-duct_{between-LV-and-HV}}+ 2\times w_{culinder_{between-LV-and-HV}}$$
	- Now add the above value with twice the thickness of the high voltage winding and call it the outer diameter of the high voltage winding.
	>$$d_{outer-radius}=d_{inner-radius}+2\times w_{radial-axis-winding}$$
- Finally, we must place the oil channel between the high voltage windings for non-identical phases, which is also obtained in Table 5-8.
	>$$table_{5-8}\to w_{oil-duct-between-HV-to-HV}$$
12. Calculation of the closeness of non-phase windings:
	>$$d_{distance-between-HV-to-HV}=D-(d_{outer-radius}+w_{oil-duct-between-HV-to-HV})$$
13. Calculation of the effective diameter of the high voltage winding:
	>$$d_{mean-winding-LV}=\dfrac{d_{outer-radius}+d_{inner-radius}}{2}$$
14. Calculation of average length of high voltage winding:
	>$$L_{mean-winding-LV}=\pi \times d_{mean-winding-LV}$$
15. Calculation of high voltage winding resistance:
	>$$R_{winding-HV}=\dfrac{(Specific\:resistance\:of\:copper)\times L_{mean-winding-LV}\times T_1}{a_{1-con}}$$
16. Calculation of high voltage winding volume:
	>$$vol_{HV}=T_1\times L_{mean-winding-LV}\times a_{1-con}$$
