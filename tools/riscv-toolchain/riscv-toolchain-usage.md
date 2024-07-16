# RISC-V Toolchain Usage

## Assembler and Disassembler

This is the whole content of `test.asm`

```assembly
addi x1, x0, 0x1 # I-Imm
sw   x1, 2(x0)   # S-Imm
beq  x1, x0, 0x4 # B-Imm
auipc x1, 0x1000 # U-Imm
jal   x1, 0x8    # J-Imm
```

Use `riscv64-unknown-elf-as` to compile it to binary code.

```sh
riscv64-unknown-elf-as -march=rv32i test.asm -o test.out
```

Then use `riscv64-unknown-elf-objdump` to dump the binary code.

```sh
riscv64-unknown-elf-objdump -d test.out
```

{% hint style="info" %}

Question: Can you explain how the instructions are encoded according to the output
of `riscv64-unknown-elf-objdump`? Or does the output match your imagination?

{% endhint %}
