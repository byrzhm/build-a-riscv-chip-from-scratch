# S-type

{% hint style="info" %}

S-type instructions are used for store.

{% endhint %}

## S-Format Instruction Layout

<figure><img src="../../.gitbook/assets/s-type.png" alt=""><figcaption></figcaption></figure>

* $\rm Mem[Reg[rs1] + offset] \leftarrow Reg[rs2]$

{% hint style="warning" %}

**Immediate in two parts**

* Can't have both *rs2* and *immediate* in same place as other instructions
* RISC-V design decision is move low 5 bits of immediate to where rd field was in other instructions - keep rs1/rs2 fields in same place
  * register names more critical than immediate bits in hardware design

{% endhint %}

## I+S Immediate Generation

<figure><img src="../../.gitbook/assets/i+s-immgen.jpg" alt=""><figcaption></figcaption></figure>

* Just need a 5-bit mux between two positions where low five bits of immediate can reside in instruction
* Other bits in immediate are wired to fixed positions in instruction

## Store Instructions

<figure><img src="../../.gitbook/assets/s-type-instructions.png" alt=""><figcaption></figcaption></figure>

## Datapath

<figure><img src="../../.gitbook/assets/datapath4.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}

How to control the amount of bytes to write to memory?

{% endhint %}
