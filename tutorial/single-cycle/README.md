# Single Cycle

We have built the complete RV32I datapath. Now we gonna design the control unit.

<figure><img src="../../.gitbook/assets/complete-datapath.jpg" alt=""><figcaption></figcaption></figure>

## Control Unit

<figure><img src="../../.gitbook/assets/control-truth-table.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}

* Some instructions are omitted, for example, `bge` and `bgeu`.
* LdSel signal is omitted.

{% endhint %}

## Timing

{% hint style="info" %}

Think of the following questions carefully. You need to find the answer on your own through your own effort.

**1. Why an instruction can be executed in single cycle in a single-cycle processor?**

**2. What properties are needed for instruction memory, data memory and register file?**

**3. What if the instruction memory or data memory or register file can only be read synchronously?**

**4. What's the possible critical path of single-cycle processor?**

{% endhint %}

<figure><img src="../../.gitbook/assets/single-cycle-timing.jpg" alt=""><figcaption></figcaption></figure>

Basically, each instruction comes in at its first rising clock edge and finish at
its second rising clock edge (often write its result back).
