# R-type

## R-Format Instruction Layout

<figure><img src="../../.gitbook/assets/r-type.png" alt=""><figcaption></figcaption></figure>

* _opcode_: partially specifies what instruction it is
  * Note: This field is equal to <mark style="color:red;">0110011</mark> for all R-format register-register arithmetic instructions
* _funct7 + funct3_: combined with _opcode_, these two fields describe what operation to perform
* _rs1_(Source Register #1): specifies register containing first operand
* _rs2_: specifies second register operand
* _rd_(Destination Register): specifies register which will receive result of computation

{% hint style="info" %}
Each register field holds a 5-bit unsigned integer (0-31) corresponding to a register number (x0-x31)
{% endhint %}

## R-Format Instructions

<figure><img src="../../.gitbook/assets/r-type-instructions.png" alt=""><figcaption><p>R-type instructions</p></figcaption></figure>

{% hint style="info" %}
Decoding _funct7_ and _funct3_ fields to select appropriate ALU functions.
{% endhint %}

## Datapath

Here is our datapath for R-format instructions.

<figure><img src="../../.gitbook/assets/datapath1.jpg" alt=""><figcaption></figcaption></figure>
