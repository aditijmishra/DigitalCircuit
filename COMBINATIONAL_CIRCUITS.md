# COMBINATIONAL CIRCUITS

Now we combine gates to create useful circuits.

A combinational circuit has:

Output determined only by the current inputs.

There is no memory.

* Examples:

Half adder

Full adder

Multiplexer

Demultiplexer

Encoder

Decoder

Comparator



 ## 1. Half Adder

A half adder adds two one-bit numbers.

Inputs:

A,B

Outputs:

Sum S

Carry C

Truth table:

A	B	S	C

0	0	0	0

0	1	1	0

1	0	1	0

1	1	0	1


Therefore:

S=A⊕B
	​

C=AB
	​
So a half adder requires:

XOR + AND


## 2. Full Adder

A full adder adds:

A+B+Cin
	​


Inputs:

A

B
Carry-in

Outputs:

Sum

Carry-out

The important equations are:

S=A⊕B⊕Cin
	​

and:

Cout
	​

=AB+Cin
	​

(A⊕B)
	​
A full adder is important because multiple full adders can be connected to create larger binary adders.




## 3. Multiplexer

A MUX is basically a digital selector.

Suppose we have:

I0

I1

I2

I3

and want to select one input.

A 4-to-1 MUX has:

4 inputs

2 selection lines

1 output

Because:

2^2=4


Selection:

S1	S0	Output
0	0	I0

0	1	I1

1	0	I2

1	1	I3



Exam question

How many selection lines are required for 16 inputs?

Use:

2^n
=16

Therefore:

n=4

Answer:

4
	​





## 4. Decoder

A decoder converts:

n inputs→2n

 outputs

Example:

2-to-4 decoder:

2 inputs

   ↓
   
Decoder

   ↓
   
4 outputs

Because:

2

2

=4

A decoder is commonly used for selecting memory locations or devices
