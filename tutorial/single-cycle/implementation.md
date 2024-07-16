# Implementation

## Implementation Overview

First, we will implement the basic elements, i.e., PC, memory, register file, ALU and so on.
Then we will connect these basic elements together with our control unit. The control unit
will be super easy to implement, because RV32I is basically a nine-bit ISA!

<figure><img src="../../.gitbook/assets/nine-bits.png" alt=""><figcaption></figcaption></figure>

## Basic Elements

### PC

PC is just a 32-bit register.

{% hint style="info" %}

* Only the low bits of PC are useful, because the instruction memory is limited.
* The low two bits of PC are always zero, how to utilize it?

{% endhint %}

### Memory

{% hint style="warning" %}

To implement a single-cycle processor, we need asynchronous
read instruction and data memory.

{% endhint %}

#### Instruction Memory

For simplicity, IMEM is not writable, i.e, it's a ROM.

Check my [implementation](https://github.com/byrzhm/SimpleRV/blob/main/single-cycle/src/imem.sv) here.

#### Data Memory

Data memory should be synchronous write and asynchronous read RAM.

{% hint style="info" %}

How to support `sb`, `sh` and `sw`?

{% endhint %}

Check my [implementation](https://github.com/byrzhm/SimpleRV/blob/main/single-cycle/src/dmem.sv).

### Register File

Our register file should be synchronous write and asynchronous read.

{% hint style="warning" %}

Remember x0 is wired to 0.

{% endhint %}

Check my [implemention](https://github.com/byrzhm/SimpleRV/blob/main/single-cycle/src/register_file.sv).

### ALU

ALU should support following operations:

* ADD:  y = a + b
* SUB:  y = a - b
* AND:  y = a & b
* OR:   y = a | b
* XOR:  y = a ^ b
* SLL:  y = a << b
* SRL:  y = a >> b
* SRA:  y = $signed(a) >>> b
* SLT:  y = ($signed(a) < $signed(b)) ? 1 : 0
* SLTU: y = (a < b) ? 1 : 0

{% hint style="warning" %}

When doing shift, only the low 5 bits of b are useful.

{% endhint %}

Here is my [implementation](https://github.com/byrzhm/SimpleRV/blob/main/single-cycle/src/alu.sv).

### Immediate Generator

<figure><img src="../../.gitbook/assets/all-immediate.png" alt=""><figcaption></figcaption></figure>

My implementation goes [here](https://github.com/byrzhm/SimpleRV/blob/main/single-cycle/src/immgen.sv).

### Comparator

Pretty easy and here is my [implementation](https://github.com/byrzhm/SimpleRV/blob/main/single-cycle/src/comparator.sv).

## Control Unit

RV32I is basically a nine bit ISA. If you get stuck, check my [implementation](https://github.com/byrzhm/SimpleRV/blob/main/single-cycle/src/controller.sv).

## Connect all the components

It's not very hard to connect all the components. If you don't know what to do,
check the complete datapath we have built.

## Test our implementations

I write some very simple testbenches to test my implementations, you can see these testbench at [single-cycle/sim](https://github.com/byrzhm/SimpleRV/tree/main/single-cycle/sim)
