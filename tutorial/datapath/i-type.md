# I-type

## I-Format Instruction Layout

<figure><img src="../../.gitbook/assets/i-type.png" alt=""><figcaption></figcaption></figure>

* The `funct7` and `rs2` fields from R-Format are replaced by 12-bit signed immediate, `imm[11:0]` (in range \[-2048, 2047]).
* Remaining fields (`rs1`, `funct3`, `rd`, `opcode`) same as R-Format.
* Immediate is always sign-extended to 32-bits before use in an arithmetic operation.

### I-immediate

<figure><img src="../../.gitbook/assets/i-immediate.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/immgen-i.jpg" alt=""><figcaption><p>Immediate generator generates I-type immediate</p></figcaption></figure>

## I-Format Arithmetic Instructions

<figure><img src="../../.gitbook/assets/i-type-instructions.png" alt=""><figcaption><p>I-Format Arithmetic Instructions</p></figcaption></figure>

### Adding I-Format arithmetic instructions to datapath

<figure><img src="../../.gitbook/assets/datapath2.jpg" alt=""><figcaption></figcaption></figure>

## I-Format Load Instructions

Load instructions are also I-type.

<figure><img src="../../.gitbook/assets/load-instruction-layout.png" alt=""><figcaption><p>Load Instruction Layout</p></figcaption></figure>

* Reg\[rd] <- Mem\[Reg\[rs1] + offset]
  * The 12-bit immediate is added to the base address in `rs1` to form the memory address
  * The value loaded from memory is stored in register `rd`

<figure><img src="../../.gitbook/assets/i-type-load-instructions.png" alt=""><figcaption><p>I-Format Load Instructions</p></figcaption></figure>

{% hint style="info" %}
Note that the `funct3` field is to specify the width (i.e., the amount of bytes) and signedness of load data.
{% endhint %}

### Adding load instructions to datapath

<figure><img src="../../.gitbook/assets/datapath3.jpg" alt=""><figcaption></figcaption></figure>
