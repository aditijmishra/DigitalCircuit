# Boolean algebra

Now we move from numbers to logic.

Boolean algebra works with only two values:

0,1

A Boolean variable could be:

A=0

or:

A=1


## 1. Boolean operators

The three fundamental operations are:

AND
(A⋅B)

OR
(A+B)

NOT
A

Sometimes NOT is written:

A'

So: A ' =NOT(A)



## 2. Boolean AND

AND is 1 only when both inputs are 1.

A	B	A·B

0	0	0

0	1	0

1	0	0

1	1	1

Think:

"Both conditions must be true."

* Example:

You can enter a system only if:

Correct password AND correct PIN



## 3. Boolean OR

OR is 1 when at least one input is 1.

A	B	A+B

0	0	0

0	1	1

1	0	1

1	1	1




## 4. NOT

NOT reverses the value.

A	A'

0	1

1	0




## 5. Important Boolean laws

These are extremely important for exams.

* Identity laws
A+0=A

A⋅1=A

* Null laws

A+1=1

A⋅0=0

* Idempotent laws

A+A=A

A⋅A=A

* Complement laws

A+A'=1

A⋅A'=0


* Double negation
(A')′=A


* Commutative laws

A+B=B+A

AB=BA

Order doesn't matter.

 
*Associative laws

 (A+B)+C=A+(B+C)
 
(AB)C=A(BC)

* Distributive laws

Very important:

A(B+C)=AB+AC

Also:

A+BC=(A+B)(A+C)


* De Morgan's laws

First law
(AB)'=A'+B′
	​

Second law
(A+B)′=A′B′




* Boolean simplification

Example:

A+AB

Factor A:

A(1+B)

Since:

1+B=1

therefore:

A
	​
This is called the absorption law:

A+AB=A
	​


Another one:

A(A+B)

gives:

A
	​
