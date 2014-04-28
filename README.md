ECE281_Lab5
===========

PRISM Programming


__*BOTH PRISM PROGRAMS 1 AND 2 CHECKED BY DR. NEEBEL*__


__*1st PRISM Program*__


The first PRISM program was just to understand how the instructions are given to make something happen like in a computer. This program would count from 9 to F outputting each hex number to OUTPUT 3. The instructions as organized by the PRISM program are shown below:

![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/PRISM_PROGRAM_1.gif?raw=true)

The way this program work is by starting with loading 8 into the accumulator. Then 1 is added to the accumulator. Next the accumulator is ouputted to OUTPUT 3, and if the accumulator is negative, the program will jump back through loop to adding 1 until the program ends in an infinite loop, keeping zero in the output.
To delve into the program, look at the four snippets below this paragraph. The snippets are outlining what state the program is in at 10 ns intervals. From 5-15 ns, the program will FETCH the instruction "7" from the Data, then DECODE what instruction 7 refers to. Because it is LDAI instruction, the program will IMMEDIATELY EXECUTE using the operand from 25-35 ns. The program knows that an EXECUTE is the last of the state diagram before looping back to FETCH. The next FETCH sees in the Data is "6" which is DECODED from 45-55 ns as the ADDI instruction. It also is an IMMEDIATE EXECUTION from 55-65 ns. Next "4" is FETCHed (65-75 ns), which DECODEs(75-85 ns) to an OUT instruction. An OUT instruction requires the next state, DECODE LoADDR (85-95 ns). This takes in the operand "3" and sends it through MARLo, and that sets the right address for the DIRECT IO EXCECUTE (95-105 ns) to send the accumulator ("9" at this point) to. From 105-115 ns, "B" is FETCHed, which DECODEs (115-125 ns) to a JN instruction. A JN recieves the status signal A<0, and if it is true, the instruction will execute a jump to the operand adress which is retrieved in DECODE LoADDR(125-135 ns) and DECODE HiADDR (135-145 ns). Then the JUMP EXECUTE occurs based on the status signal from the accumulator as discussed before. That is how this COUNTER program works. Shown below is the first 165 ns of the program, before the program jumps back to "loop".

![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/Lab5PRISM_1st.gif?raw=true)

![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/Lab5PRISM_2nd.GIF?raw=true)

![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/Lab5PRISM_3rd.GIF?raw=true)

![](https://github.com/dustyweisner/ECE281_Lab5/blob/master/Lab5PRISM_4th.GIF?raw=true)


__*2nd PRISM Program*__


The 2nd PRISM PROGRAM Counted from 0-99 or backwards depending on if the input was positive or negative.

I created the COOL_PROGRAM, which counts in a loop from 1-9 in a single OUPUT. It starts at output zero, but if only the first input is 1, the output shifts left one output(or back to OUTPUT 3). Also it shifts the other way if only the 2nd input is 1. If they are both 1, or both anything other than 1, the program keeps the output in the current output. The PRISM program of the loop is in my ECE281_Lab5 repository, and it has FULL FUNCTIONALITY.


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
