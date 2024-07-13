# R-type

## R-Format Instruction Layout

<figure><img src="../../.gitbook/assets/r-type.png" alt=""><figcaption></figcaption></figure>

* *opcode*: partially specifies what instruction it is
  * Note: This field is equal to $\textcolor{red}{0110011_{two}}$ for all R-Format register-register arithmetic instructions
* *funct7 + funct3*: combined with *opcode*, these two fields describe what operation to perform

<br>

* *rs1*(Source Register #1): specifies register containing first operand
* *rs2*: specifies second register operand
* *rd*(Destination Register): specifies register which will receive result of computation

{% hint style="info" %}

Each register field holds a 5-bit unsigned integer (0-31) corresponding to a register number (x0-x31)

{% endhint %}

## R-Format Instructions

<figure><img src="../../.gitbook/assets/r-type-instructions.png" alt=""><figcaption>R-type instructions</figcaption></figure>

{% hint style="info" %}

Decoding *funct7* and *funct3* fields to select appropriate ALU functions.

{% endhint %}

## Datapath

Here is our datapath for R-Format instructions.

<figure><img src="../../.gitbook/assets/datapath1.jpg" alt=""><figcaption></figcaption></figure>
