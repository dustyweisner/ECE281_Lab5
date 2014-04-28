ECE281_Lab5
===========

PRISM Programming

__*1st PRISM Program*__


![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/Lab5PRISM_1st.gif?raw=true)

![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/Lab5PRISM_2nd.GIF?raw=true)

![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/Lab5PRISM_3rd.GIF?raw=true)

![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/Lab5PRISM_4th.GIF?raw=true)


__*QUESTIONS AND ANSWERS*__


1.	When the controller’s current state is “FETCH,” what is the status of the following control lines:

  a.	PCLd - ON

  b.	IRLd - ON

  c.	ACCLd - OFF

2.	The current state is Decode LoAddr and the IR contains “OUT.”  What are the control signals that are asserted, and what will the next state be?

  The control signals are MARLoLd and PCld, and the next state is Direct IO Execute.


3.	What are the three status signals sent from the PRISM datapath to the PRISM controller?


  A = 0, A < 0, and 1


4.	Why is it important that ACCLd signal be active during the execute state for the ADDI instruction?


  The ACCLd needs to be active during the execute state during an ADDI instruction because ADDI adds what is in the operand to the accumulator, and to add to what is in the accumulator, you need to load what is in it to be used during the ADD function in the ALU.


5.	What changes are necessary to the PRISM datapath to add another instruction (SUBI, which would subtract an immediate value from the accumulator) to the instruction set?


  First off, there would need to be another bit to all of the control signals with 4 bits, and therefore another wire for each. This would include making addr(9 downto 5) and addr(4 downto 0). That would make PC 10 bits.
