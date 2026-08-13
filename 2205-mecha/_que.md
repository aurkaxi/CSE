>[!note] 
>1. most questions were combined, like definition + unrelated explanation or math = 1 question for 5 marks; diagram of one thing + characteristics of something else = 4 marks. this is why i couldn't group them via topic.
>   so skipping questions might not be a good idea.
>2. most questions are not repeated, except definitions. good luck with that.
# what
what is... define... explain with example...
1. loading error in a potentiometer [mec]
2. define sensor [mec, 2021, 2021(yes twice), ]
3. Transductions (not transducer) [2021]
4. define transducer [mec, 2021]
5. active transducer [mec]
6. passive transducer [mec]
7. primary transducer [2023, 2021]
8. secondary transducer [2023, 2021]
9. mechatronics [niter, fec, 2023, 2021]
10. each constituent of mechatronics [fec]
11. electrical strain gauge [fec]
12. dielectric constant [fec]
13. industry 4.0 [stec]
14. moment of inertia [stec]
15. dead band [stec]
16. resolution [stec. 2021]
17. sensitivity [stec, 2021]
18. transportation lag [stec]
19. second order instrument: [stec]
	1. time constant
	2. rise time
	3. peak time
	4. settling time
20. the following dynamic characteristics of a sensor [2023] (jehetu pori nai so jani na eigular definition context er jonno vary kore ki na, naki same. for safety, kept separated)
	1. rise time
	2. fall time
	3. settling time
	4. transient response
	5. steady state response
21. system in mechatronics [2022]
22. temperature sensor [2022]
23. laminar flow [2022]
24. Proximity sensors [2022]
25. LDR [2022]
26. Interfacing Electronic circuits [2021]
27. Tactile Sensor [2021]
28. Write short notes on [2021]
	1. Effective gear ratio
	2. Efficiency of gear ratio
	3. Backlash
	4. Stiffness
	5. Break away friction
	6. Back drive ability
29. Accuracy [2021]
30. Precision [2021]
31. plc [2021]
32. signal conditioner [2021]
# why
1. why moment of inertia is important for modeling rotating systems [stec]
2. two real-life applications of mechatronics [niter]
3. write two real life applications of stepper motor [niter]
4. why compensation circuit is required for thermocouples [stec]
5. application of RTD in mechatronic system [2022]
6. application and benefit of mechatronics. [2021]
7. Why motion Transmission is necessary in mechanical system? [2021]
8. advantage of hydraulic system [2021]
9. disadvantage of hydraulic system [2021]
10. advantages of PLC system for industry [2021]
# diff
1. absolute, gauge, and vacuum pressures. [stec]
2. hydraulic and pneumatic systems [2023, 2022, ]
3. compare the functions of series wound dc motor and shunt wound dc motor [2023]
4. condense microphone and dynamic microphone [2023]
# diagram and/or circuit
draw a diagram for everything. The questions listed below are simply the ones where a diagram was explicitly required. this list may contain duplicate question from other categories.
1. circuit diagram loading error in a potentiometer [mec]
2. any one type of proximity sensor based on sensing [mec]
3. draw the block diagram of a temperature measurement system with its three basic components, show their interconnection and briefly explain it [niter]
4. draw the equivalent electrical circuit of this system using the force-voltage analogy (force->voltage, velocity->current) [niter] ![[Pasted image 20260602183110.png]]
5. suppose an automatic door opens when a person stands near it and remains closed otherwise. the system uses a proximity sensor, a controller, and a motor actuator.
	1. if the door position (open or closed) is provided as feedback, draw a block diagram showing how this forms a closed-loop control system for accurate door operation. briefly explain the diagram and identify the following elements in the system: input, output, feedback element and controller [niter]
6. sketch and show the non-linearity and hysteresis properties of sensor [fec]
7. sketch how a capacitive proximity sensor detects the presence of non-metallic objects in its specific close range [stec]
8. working principle of a linear variable differential transformer [stec]
9. draw the step response characteristics curve of a second order instrument [stec]
10. open loop control system [2023]
11. closed loop control system [2023]
12. working principle of a potentiometer with a labeled diagram. [2023]
13. draw the curves of the following dynamic characteristics of a sensor [2023]
	1. rise time
	2. fall time
	3. settling time
	4. transient response
	5. steady state response
14. draw the working principle of an inductive proximity sensor. [2023]
15. explain the automatic car parking system. [2023]
16. the Electromechanical system [2022]
17. inductive proximity sensor [2022]
18. characteristics of LDR [2022]
19. plc [2022]
20. temperature resistance curve [2022]
21. Convert the spring-mass-damper system into an equivalent electrical system. Write down the system equation. [2022] ![[Pasted image 20260626113600.png]]
22. Draw the block diagram for open loop and close loop control system for heating a room. [2021]
23. Draw the solenoid control diagram of double acting cylinder when Activated and Not activated. [2021]
24. Draw the flow diagram of hydraulic system [2021]
# derive equation
1. loading error in a potentiometer [mec]
2. resistance of the liquid level system [mec, 2023, 2022]
3. capacitance of the liquid level system [mec, 2023, 2022]
4. a mechanical system consists of two masses and connected by springs and dampers. an external force F(t) is applied to mass, and the output displacement is (t). assuming linear spring and damper elements, derive the differential equations relating the input force f(t) and out displacement (t). [mec]
5. consider the mechanical system shown below, consisting of to masses, two springs, and a damper. a force f(t) is applied on mass $m_1$. ignore friction. write the equations of motion for both masses in terms of displacement x1 and x2 [niter] ![[Pasted image 20260602183110.png]]
6. show that the transfer function of the rc low-pass filter given below is [niter]
   $$
   G(s) = (Y(s))/(X(s)) =1/(tau s +1), text(where ) tau=RC
   $$
   ![[Pasted image 20260626010000.png]]
7. and integral controller $K_i/s$ is used with the given plant $G(s)$ in a unity feedback system as shown below. derive the closed-loop function $(Y(s))/(X(s))$ of the system [niter]
   ![[Pasted image 20260626010202.png]]
8. construct a mathematical model of the series RLC circuit shown below. consider applied voltage v as input and voltage dorp across capacitor $V_c$ as output. assume that resistance R, inductance L, and capacitance C are know. [stec]
   ![[Pasted image 20260626011012.png]]
9. derive an equation for acceleration of a mass m attached to a pulley of mass M and radius R as shown in the figure below [stec]
   ![[Pasted image 20260626011137.png]]
10. a liquid entering and leaving a container develop an equation describing how the height of liquid in the container depends on the rate of input of liquid into the container [2023]
    ![[Pasted image 20260626012151.png]]
11. derive second order differential equation governing the motion of a mass attached to a spring and damper [2023]
12. Write the transfer function equations governing the mechanical systems shown in figure [2022] ![[Pasted image 20260626113600.png]]
13. Convert the spring-mass-damper system into an equivalent electrical system. Write down the system equation. [2022] ![[Pasted image 20260626113600.png]]
# classify
# describe
most of them require [[#what]] and [[#diagram and/or circuit]]
1. proximity sensors based on sensing principle [mec]
2. good sensor [mec]
3. basic element of mechatronics system [mec, 2021]
4. list the four engineering disciplines involved in mechatrnonics and state one role of each [niter]
5. suppose an automatic door opens when a person stands near it and remains closed otherwise. the system uses a proximity sensor, a controller, and a motor actuator.
	1. explain any one sensor-transducer mechanism that can be used to detect the distance of a person approaching the door [niter]
	2. in 1-2 sentences, explain how the closed loop control system maintains higher accuracy and reliability in door operation compared to an open loop system. [niter]
6. working principle of a stepper motor [niter]
7. A plant $G(s) = \frac{1}{\tau s + 1}$ is controlled by an integral controller $\frac{K_i}{s}$ in a unity feedback system as shown below. what will happen if the integral controller $K_i/s$ is removed from the system [niter] ![[Pasted image 20260626010202.png]]
8. describe how a capacitive proximity sensor detects the presence of non-metallic objects in its specific close range? [fec]
9. how mechatronics is related to biomedical engineering with example [stec]
10. the building blocks of a mechanical system [stec]
11. describe the working principle of a linear variable differential transformer [stec]
12. construction and working principle of a vortex flow meter [stec]
13. list the key features of smart sensors [2023]
14. working principle of a potentiometer [2023]
15. the phases of mechatronics design process [2023]
16. open loop control system [2023]
17. closed loop control system [2023]
18. how mechatronics integrates mechanical, electrical, and computing elements to create intelligent system [2023]
19. how does adjusting the wiper position affect the output voltage in a voltage divider circuit [2023]
20. explain the working principle of an inductive proximity sensor. describe how proximity sensor detects the presence of metallic objects without physical contact by utilizing changes in inductance when a metal object enters its electromagnetic field [2023]
21. explain the role of a gearbox in a mechanical actuation system [2023]
22. how gearbox in a mechanical actuation system impacts the torque and speed of the output [2023]
23. develop a mechatronics solution for pick and place robot and explain the various mechatronics elements [2023, 2022]
24. basic principle of thermocouples [2023]
25. explain the automatic car parking system. [2023]
26. Explain the Mechatronics system design with example. [2022]
27. the Electromechanical system [2022]
28. specialty of the working of thermistors. [2022]
29. "A piezoelectric element may be treated as a Capacitor"-justify the statement. [2022]
30. Describe the inductive proximity sensor [2022]
31. characteristics of LDR [2022]
32. working procedure of plc [2022]
33. Describe the non-linearity and hysteresis characteristics of sensor with proper figure [2022]
34. Briefly explain the basic components of automatic control systems? [2022]
35. Explain the basic elements of a closed loop control system with the help of an automatic water level controller. [2022]
36. Briefly explain the relationship between resistance and temperature for the RTD [2022]
37. Suggest a sensor that could be used for a furnace to monitor the rate at which the heating oil flows along a pipe. The output from the measurement system is to be an electrical signal which can be used to adjust the speed of the oil pump. [2022]
38. Write down the module of mechatronics system. [2021]
39. How Transformer used as an Impedance matching Device? [2021]
40. Explain the effect of Temperature and effect of Strain on resistance that is used to measuring Instrument? [2021]
41. how Interfacing Electronic circuits works [2021]
42. How is Strain Gauge used for mechanical (Force/Torque) sensor? [2021]
43. Write on Construction and Operation of Tactile Sensors [2021]
44. What are the basic elements of measurement system? [2021]
45. Follow the figure in right side and write the name of [2021]
    1. control unit,
    2. correction unit,
    3. Process,        
    4. Controlled variable
    5. Measuring device
       ![[Pasted image 20260626114443.png]]
46. What is the working principle of Autofocus system of digital camera? [2021]
47. When a Sensor is in operation mode, what phenomenon occurs [2021]
48. RADAR is a microwave-based motion detector system, Analysis [2021]
49. Which types of detectors are used for occupancy and motion sensing of objectives? [2021]
50. Selection criteria for a Transducer? [2021]
# math
1. a linear potentiometer has total resistance $2k Omega$ and is connected across 20V supply. the slider is at 25% of its total length. a load resistance of $4k Omega$ is connected across the output. find the error [mec]
2. determine the force needed to a piston of 2 cm radius in order to result a force of 6000n at the working piston of radius 6cm. calculate the hydraulic pressure in bar [mec, 2023]
3. a pressure transducer has a full range of 0 to 150 psi and is specified to have a repeatability of +-0.02% of the full range. calculate the allowable output variation for repeated measurements at a specific input pressure of 75 psi [mec]
4. a second order system step response is shown in the figure below. [niter] 
   ![[Pasted image 20260626005741.png]]
	1. from the graph, estimate the approximate percentage overshoot ($M_p$) and the peak time ($T_p$)
	2. using the values obtained in 2(a). determine the damping ratio, natural frequency, damped natural frequency, and phase angle
5. an integral controller $K_i/s$ is used with the given plant $G(s)$ in a unity feedback system as shown below. resulting in the closed-loop transfer function: $\frac{Y(s)}{X(s)} = \frac{K_i}{\tau s^2 + s + K_i}$. determine the time constant $tau$ of the plant and the integral gain $K_i$ given $T_p=0.1s$ and $M_p=10\%$. [niter]
   ![[Pasted image 20260626010202.png]]
6. a potentiometer displacement sensor is to be used to position measurement that has a diameter of 8.8 cm. if the slider around the complete track for a distance of 100 cm. the resistance changes linearly over this range from 0 to 0.8$kOmega$. the above sensor is incorporated in last-two-digit_ur_reg_n(exp:0.22A) current. for an output motion of 220v the sensitivity of the potentiometer is ? [fec]
7. the output of the industrial lvdt is connected to a voltmeter of range of 0v to 22V through amplifier having a gain of 220. for a displacement of 14mm. find the output of lvdt and the sensitivity of the instrument(v/m) [fec]
8. an rtd resistance increases from 100 to 115.4 ohm. find the temperature rise & the sensitivity of rtd? [fec]
9. a pressure sensor has an accuracy of $+-2\%$. if the true pressure is 500 psi, what is the range of possible measured values for the sensor [2023]
10. a temperature sensor is calibrated to read 25C at a constant temperature. over the course of six months, the output gradually shifts, and after this period, it reads 27C. calculate the drift in the sensor output [2023]
11. A potentiometer displacement sensor is to be used to position measurement from 0 to 100 cm linearly. The resistance changes linearly over this range from 0 to $1\text{ k}\Omega$. The above sensor is incorporated in 0.67A current. For an output motion of 210V the sensitivity of the potentiometer is ? [2022]
12. If a pipe goes from a 15-cm diameter to 8-cm diameter and the velocity of the 15-cm section is 4.21 m/s, what is the average velocity in the 8-cm section? [2022]
13. Calculate the strain gauge factor, if the resistance is 154 Ohms, which change by 8 ohms for 6000 microstrain. [2022]
14. A portable x-ray unit has a step-up transformer, the 220 V input of which is transformed to the 180 kV output needed by the x-ray tube. The primary has 80 loops and draws a current of 20 A when in use. [2022]
	1. What is the number of loops in the secondary?
	2. Find the current output of the secondary.
15. A 5 KVA single phase Transformer has a turns ratio of 10: 1and is fed from a 2.5 KV supply. Neglecting losses, determine [2021]
	1. the full load secondary current
	2. The minimum load resistance which can be connected across the secondary winding to give full load KVA
	3. The primary current at full load KVA.
16. Consider a hydraulic motion system where an accumulator is to be selected. Let the maximum and minimum line pressures be 3000 psi and 90% of that (2700 psi), respectively. Let n = 1.4 nominally for the nitrogen gas. Let the discharge volume to be 1 gallon. Calculate the necessary accumulator volume. [2021]
# sequential function chart
1. an automated packaging system is used in a small factory. the process starts when an empty box is placed on a conveyor belt. a sensor detects the box and stops the conveyor. then filing unit dispenses products into the box for a fixed time after filling is complete, the filing unit stops, and a sealing unit seals the box. finally the conveyor restarts and moves the packed box to the output area and the system waits for the next box. draw a sequential function chart (sfc) for this system showing the steps, transitions, and actions clearly. [mec]
2. consider the situation of the washing cycle of a domestic washing machine where the drum is to be filled with water and then whel full a heater has to be switched on and remain on until the temperature reaches the required level. then the drum is to be rotated for a specified time. draw the sequential functional chart (sfc) [2023]
# plc logic design
1. in an industrial cooling system, a fan is programmed to turn on 20 seconds after the system is activated and remain on until the system is turned off. design the plc logic for this operation. [mec]
# ladder diagram
try writing instruction list with it (even not asked explicitly)
1. a signal lamp is required to be switched on if a pump is running and pressure is satisfactory, or if the lamp test switch is closed. write the ladder diagram and instruction list as well [2023]
2. draw the ladder diagram for the following logic gates: and, or, not, nand, nor , ex-or [2023]
